# Diagramme de Cas d'Utilisation

```plantuml
@startuml
left to right direction

actor "Visiteur" as VS
actor "Standard" as ST
actor "Premium" as PR

actor "Bibliothécaire" as BL

ST -left-|>  VS
PR -left-|> ST

' --- SYSTÈME ---
rectangle "Portail OmniLib" {

    (Naviguer sur le portail) as UC_Portail
    (Consulter catalogue) as UC_Catalogue
    (Télécharger eBooks) as UC_Telecharger
    (Louer une VOD) as UC_Louer
    (Réserver un livre en ligne) as UC_Reserver
    (Emprunter au guichet) as UC_Emprunt
    (Commander en ligne) as UC_Ligne
    (Livrer à domicile) as UC_Transport 

    (Mettre à jour catalogue) as UC_MiseAJour
    (Valider les retours) as UC_Retours
    (Vérifier retard) as UC_Verifier
    (Valider l'emprunt) as UC_Valider


    UC_Emprunt ..> UC_Valider : <<include>>
    UC_Verifier ..> UC_Valider : <<include>>
    UC_Retours ..> UC_Valider : <<include>>
    UC_Ligne ..> UC_Transport : <<extend>>
}

actor "Transporteur" as TR

VS -- UC_Portail
VS -- UC_Catalogue

ST -- UC_Reserver
ST -- UC_Ligne
ST -- UC_Emprunt

PR -- UC_Telecharger
PR -- UC_Louer

BL -- UC_MiseAJour
BL -- UC_Retours



UC_Transport -- TR 


@enduml
```




