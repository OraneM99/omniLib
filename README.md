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
    UC_Ligne <.. UC_Transport : <<extend>>
}

actor "Transporteur" as TR

VS -- UC_Portail
VS -- UC_Catalogue

ST -- UC_Ligne
ST -- UC_Emprunt

PR -- UC_Telecharger
PR -- UC_Louer

BL -- UC_MiseAJour
BL -- UC_Retours



UC_Transport -- TR 


@enduml
```




```mermaid
classDiagram

Personne <|-- Visiteur
Personne <|-- Bibliothecaire
Visiteur <|-- Standard
Standard <|-- Premium

Media <|-- MediaPhysique
Media <|-- MediaNumerique

MediaPhysique <|-- Livre
MediaNumerique <|-- Ebooks
MediaNumerique <|-- VOD

class Personne  {
<<abstract>>
}

class Visiteur {
+consulterCatalogue()
+naviguerPortail()
}

class Standard {
-String nom
-String prenom
-int numeroAdherent
+commanderEnLigne()
+emprunterAuGuichet()
}

class Premium {
-int numeroDeForfait
+louerVod()
+telechargerEbooks()
}

class Bibliothecaire {
-String nom
-String prenom
+validerRetour()
+mettreAJourCatalogue()
+validerEmprunt()
}

class Media {
<<abstract>>
-String titre
-String auteur
-int anneeEdition
}

class MediaPhysique {
<<abstract>>
}

class MediaNumerique {
<<abstract>>
}

class Catalogue {
-int numeroRayon
+rechercher()
}

class Livre {
-int codeBarre
}

class EtatUsure {
	<<enumeration>>
	NEUF
	BON ETAT
	MOYEN
	MAUVAIS
}

class Ebooks {
-int taille
-String format 
}

class VOD {
-int duree
-String resolution
}

class Transporteur {
-int numeroSuivi
+livrerDomicile()
}

Visiteur --> Catalogue : connait
Livre *-- EtatUsure : composition
Catalogue --* Media : contient


```


```plantuml
@startuml
start
:Utilisateur standard;
:S'identifier;
repeat
repeat
:choisis un livre;

:reserver un livre;

repeat while (livre dispo) is (no) not (yes)


repeat while (penalite de retard) is (yes) not (no)
:confirmer reservation;

:options de livraison;
stop
@enduml

```