# Diagramme de Cas d'Utilisation

```plantuml
@startuml
left to right direction

together {
	actor "Visiteur" as VS
	actor "Standard" as ST
	actor "Premium" as PR
	actor "Bibliothécaire" as BL
}

rectangle "Portail OmniLib" {
	usecase "Naviguer sur le portail" as UC_Portail
	usecase "Consulter catalogue" as UC_Catalogue
	usecase "Mettre à jour catalogue" as UC_MiseAJour
	usecase "Valider les retours" as UC_Retours
	usecase "Télécharger eBooks" as UC_Telecharger
	usecase "Louer une VOD" as UC_Louer
	usecase "Réserver un livre en ligne" as UC_Reserver
	usecase "Emprunter au guichet" as UC_Emprunt
	usecase "Vérifier retard" as UC_Verifier
	usecase "Valider l'emprunt" as UC_Valider
	usecase "Commander en ligne" as UC_Ligne
	usecase "Acheter titre de transport" as UC_Transport 
}

VS -- UC_Portail
VS -- UC_Catalogue

VS <|-- ST
ST <|-- PR

ST -- UC_Emprunt
ST -- UC_Reserver
ST -- UC_Ligne

PR -- UC_Telecharger
PR -- UC_Louer

BL -- UC_Valider
BL -- UC_Verifier
BL -- UC_Retours
BL -- UC_MiseAJour

together {
	actor "Transporteur" as TR
}

TR -- UC_Transport

@enduml
```





