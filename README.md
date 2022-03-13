# Documentation ProjetBD Groupe 5



### __Propriétés élémentaires :__

idProd, intituléProd, prixCProd, descProd, urlProd

caracProd, valeurProd

idUtil, mailUtil, mdpUtil, nomUtil, prenomUtil, adrUtil

idCategorie, nomCategorie

idOffre, dateOffre, heureOffre, prixOffre

<br>

### __Dépendances fonctionnelles :__ 

> Les  produits  ont  un  identifiant  unique  et  sont  décrits  par  un  intitulé,  un  prix  courant,  un  petit  texte  de description, l’URL d’une photo du produit,  et  un  ensemble  de  couples  caractéristique/valeur  qui  lui  sont spécifiques

idProd -> intituléProd, PrixCProd, DescProd, UrlProd

> Les clients sont identifiés par leur adresse email, un mot de
passe, leur nom, leur prénom et leur adresse postale 

idUtil -> mailUtil, mdpUtil, nomUtil, prenomUtil, adrUtil


> Une catégorie a un nom

idCategorie -> nomCategorie

> Les offres sont identifiées par l’identifiant de produit et la date et l’heure de l’offer, et on précisera le prix proposé et le compte utilisateur concerné
Une offer est faite par un utilisateur pour un produit

idOffre -> dateOffre, heureOffre, prixOffre, idProd, idUtil

<br>

### __Contraintes de valeurs :__

PrixCProdut > 0

prixOffre > 0

<br>

### __Contraintes de multiplicité :__

> un produit peut avoir des caractéristiques

idProd -|->> caracProd, valeurProd 

> une catégorie possède une ou plusieurs sous-catégorie.s


idCategorie -|->> idCategorie 

> Si un produit est acheté, alors il est associé a son offer gagnante

idProd -|-> idOffre

<br>

### __Contraintes contextuelles :__

__Pour une offer donné :__
> “Une nouvelle offer doit avoir un prix (prixOffre) strictement supérieur au prix courant du produit (prixCProd)”

> “Si une offer est ajoutée, le prix courant (prixCProd) du produit devient celui de l’offer (prixOffre)”

<br>

# 


### __Types d'entité__

Produit(idProd, nomProd, prixCProd, descProd, urlProd)

Utilisateur(idUtil, mailUtil, mdpUtil, nomUtil, prenomUtil, adrUtil)

Categorie(idCategorie, nomCategorie)

Offer(idOffre, dateOffre, heureOffre, prixOffre)

CaracProduit(caracProd)

<br>

### __Types d'association__

> un produit peut avoir des caractéristiques

__Possede:__ idProd (1..*) -|->> (0..*) caracProd, valeurProd [propriété propre] 

> une catégorie possède une ou plusieurs sous-catégorie.s

__EstMereDe:__ idCategorie (0..1) -|->> (0..*) idCategorie 

> une offer est associée à un produit

__EnchereDe:__ idOffre (0..*) -> (1..1) idProduit 

> une offer est associée à un utilisateur

__EncherePar:__ idOffre (0..*) -> (1..1) idUtil 

> une catégorie concerne plusieurs produits

__CategorieDe:__ idCategorie (1..1) ->> (1..*) idProduit 


<br>

### __Sous-type d'entité__

OffreGagnante associée à l’entité “Offer”
- duplication pour accès en temps rapide

<br>

### __Propriétés propres__

idProd, caracProd -> valeurProd
