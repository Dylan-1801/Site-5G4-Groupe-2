---
title: "Solution de l'atelier"
icon: rocket
weight: 1
chapter: true
---


# Création d’un jeu avec Unreal Engine

- On va utiliser Unreal Engine mais en choisissant l’option C++ au lieu de BleuPrint pour faire un jeu de Piece et de Target comme on le remarque dans la photo suivante :

<img src="/images/ajouter-projet.png" width="400">

. Une fois que c’est créé, on va commencer avec le premier jeu: 

. On clique sur Tools et création de classe avec C++. 

. Clique sur Actor pour donner un objet (Parent class) et on le nomme Pièce 

. On aura deux classes : Piece.cpp et Piece.h 

- Piece.cpp :


        #include "CoinActor.h" 

        #include "GameFramework/Character.h" 

        #include "Engine/Engine.h" 

          

        ACoinActor::ACoinActor() 

        { 

        PrimaryActorTick.bCanEverTick = true; 

      

        CollisionSphere = CreateDefaultSubobject<USphereComponent>(TEXT("CollisionSphere")); 

        RootComponent = CollisionSphere; 

      

        CollisionSphere->InitSphereRadius(50.f); 

        CollisionSphere->SetCollisionEnabled(ECollisionEnabled::QueryOnly); 

        CollisionSphere->SetCollisionObjectType(ECC_WorldDynamic); 

        CollisionSphere->SetCollisionResponseToAllChannels(ECR_Overlap); 

        CollisionSphere->SetGenerateOverlapEvents(true); 

      

        CollisionSphere->OnComponentBeginOverlap.AddDynamic(this, &ACoinActor::OnOverlapBegin); 

      

        CoinMesh = CreateDefaultSubobject<UStaticMeshComponent>(TEXT("CoinMesh")); 

        CoinMesh->SetupAttachment(RootComponent); 

        CoinMesh->SetCollisionEnabled(ECollisionEnabled::NoCollision); 

        } 

          

        void ACoinActor::BeginPlay() 

        { 

            Super::BeginPlay(); 

        } 

      

        void ACoinActor::Tick(float DeltaTime) 

        { 

        Super::Tick(DeltaTime); 

        AddActorLocalRotation(FRotator(0.f, 180.f * DeltaTime, 0.f)); 

        } 

          

        void ACoinActor::OnOverlapBegin( 

        UPrimitiveComponent* OverlappedComp, 

        AActor* OtherActor, 

        UPrimitiveComponent* OtherComp, 

        int32 OtherBodyIndex, 

        bool bFromSweep, 

        const FHitResult& SweepResult 

        ) 

        { 

        if (!OtherActor || OtherActor == this) 

            return; 

      

        ACharacter* Player = Cast<ACharacter>(OtherActor); 

        if (Player && GEngine) 

        { 

            GEngine->AddOnScreenDebugMessage( 

                -1, 

                1.2f, 

                FColor::Yellow, 

                TEXT("Pièce ramassée !") 

            ); 

        } 

      

        Destroy(); 

         }

- Piece.h : 
 
 

        #pragma once 

          

        #include "CoreMinimal.h" 

        #include "GameFramework/Actor.h" 

        #include "Components/SphereComponent.h" 

        #include "Components/StaticMeshComponent.h" 

        #include "CoinActor.generated.h" 

          

        UCLASS() 

        class RAMASSER_API ACoinActor : public AActor 

        { 

            GENERATED_BODY() 

          

        public: 

            ACoinActor(); 

          

        protected: 

            virtual void BeginPlay() override; 

          

            UFUNCTION() 

            void OnOverlapBegin( 

                UPrimitiveComponent* OverlappedComp, 

                AActor* OtherActor, 

                UPrimitiveComponent* OtherComp, 

                int32 OtherBodyIndex, 

                bool bFromSweep, 

                const FHitResult& SweepResult 

            ); 

          

        public: 

            virtual void Tick(float DeltaTime) override; 

          

        protected: 

            UPROPERTY(VisibleAnywhere, BlueprintReadOnly, Category = "Coin") 

            USphereComponent* CollisionSphere; 

          

            UPROPERTY(VisibleAnywhere, BlueprintReadOnly, Category = "Coin") 

            UStaticMeshComponent* CoinMesh; 

        }; 

- On retourne dans Unreal Engine et on cherche BP_Piece qui se trouve dans le Content Drawer : 

. On la dépose dans la scene. Ensuite, on cherche dans la section outliner pour BP_Piece 

. Une fois que c’est trouvé, on clique dessus et dans Details, on choisit un mesh simple (forme) 

. On démarre le jeu pour tester. 

- Résultat attendu :

<img src="/images/res-ramasser.png" width="400">

----

- Pour le deuxieme jeu : 

. On clique sur Tools et création de classe avec C++. 

. Cliquez sur Actor pour donner un objet (Parent class) et on le nomme TargetActor 

. On aura deux classes : TargetActor.cpp et TargetActor.h

- TargetActor.cpp : 

        #include "TargetActor.h" 

        #include "Engine/Engine.h" 

          

        ATargetActor::ATargetActor() 

        { 

	        PrimaryActorTick.bCanEverTick = true; 

          

	        // Mesh de la cible 

	        TargetMesh = CreateDefaultSubobject<UStaticMeshComponent>(TEXT("TargetMesh")); 

	        RootComponent = TargetMesh; 

          

	        // On veut pouvoir tirer dessus avec un LineTrace 

	        TargetMesh->SetCollisionEnabled(ECollisionEnabled::QueryAndPhysics); 

	        TargetMesh->SetCollisionObjectType(ECC_WorldDynamic); 

	        TargetMesh->SetCollisionResponseToAllChannels(ECR_Block); 

        } 

          

        void ATargetActor::BeginPlay() 

        { 

	        Super::BeginPlay(); 

        } 

          

        void ATargetActor::Tick(float DeltaTime) 

        { 

	        Super::Tick(DeltaTime); 

        }


- TargetActor.h: 

        #pragma once 

          

        #include "CoreMinimal.h" 

        #include "GameFramework/Actor.h" 

        #include "Components/StaticMeshComponent.h" 

        #include "TargetActor.generated.h" 

          
        UCLASS() 

        class RAMASSER_API ATargetActor : public AActor 

        { 

	        GENERATED_BODY() 

        public: 

	        ATargetActor(); 

        protected: 

	        virtual void BeginPlay() override; 

        public: 

	        virtual void Tick(float DeltaTime) override; 

        protected: 

	        // Mesh de la cible 

	        UPROPERTY(VisibleAnywhere, BlueprintReadOnly, Category = "Target") 

	        UStaticMeshComponent* TargetMesh; 

        };

- Ajouter la fonction de tir au personnage: 
 

. Dans les fichier .cpp et .h de ton caractere, on doit ajouter la fonction de tir pour qu’on puisse éliminer l’objet : 

 

- YourCharacter.h: 

 
        void Fire(); 

          

        // Distance du tir 

        UPROPERTY(EditAnywhere, BlueprintReadWrite, Category = "Combat") 

        float FireDistance = 10000.f;


- YourCharacter.cpp: 


        // Fonction pour tirer 

        void AramasserCharacter::Fire() 

        { 

	        APlayerController* PC = Cast<APlayerController>(GetController()); 

	        if (!PC) 

		        return; 

          

	        FVector CameraLocation; 

	        FRotator CameraRotation; 

	        PC->GetPlayerViewPoint(CameraLocation, CameraRotation); 

          

	        FVector Start = CameraLocation; 

	        FVector End = Start + (CameraRotation.Vector() * FireDistance); 

          

	        FHitResult Hit; 

	        FCollisionQueryParams Params; 

	        Params.AddIgnoredActor(this); 

          

	        if (GetWorld()->LineTraceSingleByChannel(Hit, Start, End, ECC_Visibility, Params)) 

	        { 

		        AActor* HitActor = Hit.GetActor(); 

		        if (ATargetActor* Target = Cast<ATargetActor>(HitActor)) 

		        { 

			        if (GEngine) 

			        { 

				        GEngine->AddOnScreenDebugMessage( 

					        -1, 

					        1.5f, 

					        FColor::Green, 

					        TEXT("Cible touchée !") 

				        ); 

			        } 

          

			        Target->Destroy(); 

		        } 

	        } 

          

	        // DrawDebugLine(GetWorld(), Start, End, FColor::Red, false, 1.f, 0, 1.f); 

        }

- Dans la section d’Input du fichier .cpp du caractere créé: 

        PlayerInputComponent->BindAction("Fire", IE_Pressed, this, &AramasserCharacter::Fire);

- On retourne dans Unreal Engine et on cherche TargetActor qui se trouve dans le Content Drawer : 

. On la dépose dans la scene, ensuite on cherche dans la section outliner pour TargetActor 

. Une fois que c’est trouvé, on clique dessus et dans Details, on choisit un mesh simple (forme) 

. On démarre le jeu pour tester. 

- Résultat attendu: 
<img src="/images/res-tirer.png" width="400">