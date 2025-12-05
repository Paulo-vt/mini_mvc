Script SQL :

CREATE TABLE Categorie(
   id_Categorie INT,
   Nom VARCHAR(30) NOT NULL,
   Image VARCHAR(100),
   Description TEXT NOT NULL,
   PRIMARY KEY(id_Categorie)
);

CREATE TABLE Produit(
   id_Produit INT,
   Nom VARCHAR(50) NOT NULL,
   Prix DECIMAL(4,2) NOT NULL,
   Description TEXT NOT NULL,
   Stock INT NOT NULL,
   Image VARCHAR(100),
   Statut BOOLEAN NOT NULL,
   id_Categorie INT NOT NULL,
   PRIMARY KEY(id_Produit),
   FOREIGN KEY(id_Categorie) REFERENCES Categorie(id_Categorie)
);

CREATE TABLE Client(
   id_Client INT,
   Nom VARCHAR(30) NOT NULL,
   Prénom VARCHAR(30) NOT NULL,
   Adresse VARCHAR(50) NOT NULL,
   Ville VARCHAR(30) NOT NULL,
   Code_Postal VARCHAR(10) NOT NULL,
   Email VARCHAR(100) NOT NULL,
   Mot_de_passe VARCHAR(100) NOT NULL,
   PRIMARY KEY(id_Client)
);

CREATE TABLE Administrateur(
   id_Administrateur INT,
   Nom_d_utilisateur VARCHAR(30) NOT NULL,
   Email VARCHAR(100) NOT NULL,
   Mot_de_passe VARCHAR(100) NOT NULL,
   Rôle BOOLEAN NOT NULL,
   PRIMARY KEY(id_Administrateur)
);

CREATE TABLE Commande(
   id_Commande INT,
   Produit VARCHAR(100) NOT NULL,
   Quantité INT NOT NULL,
   Statut VARCHAR(30) NOT NULL,
   Montant_total DECIMAL(4,2) NOT NULL,
   Adresse_de_livraison VARCHAR(100) NOT NULL,
   id_Client INT NOT NULL,
   PRIMARY KEY(id_Commande),
   FOREIGN KEY(id_Client) REFERENCES Client(id_Client)
);

CREATE TABLE Commander(
   id_Produit INT,
   id_Client INT,
   Quantité INT NOT NULL,
   Sous_total DECIMAL(4,2) NOT NULL,
   PRIMARY KEY(id_Produit, id_Client),
   FOREIGN KEY(id_Produit) REFERENCES Produit(id_Produit),
   FOREIGN KEY(id_Client) REFERENCES Client(id_Client)
);



1. Le prix unitaire est stocké dans la table "Commander" pour figer le prix au moment de la commande, même si le prix du produit est modifié plus tard dans la table "Produit".

2.

3. Le stock de chaque produit est conservé dans le champ "Stock" de la table Produit. À chaque commande validée, la quantité commandée est soustraite de ce stock. Le champ "Statut" du produit peut indiquer si le produit est encore disponible.

4. Oui tels que id_Produit, id_Categorie etc... 

5. Grace à : "PRIMARY KEY(id_Commande)" ce qui auto-incremente l'id de ma commande à chaque commande réalisée.

6.