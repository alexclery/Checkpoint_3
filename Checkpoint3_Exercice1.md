### Exercice 1 : Manipulations pratiques sur VM Windows (temps estimé : 1h30)

VM SRVWIN01.

#### Partie 1 : Gestion des utilisateurs

L'utilisateur Kelly Rhameur a quitté l'entreprise.
Elle est remplacée par Lionel Lemarchand

- **Q.1.1.1 Créer l'utilisateur Lionel Lemarchand avec les même attribut de société que Kelly Rhameur.**
  
  ![Q1 1 1 1](https://github.com/user-attachments/assets/56dc2828-e7d9-41f9-bb63-67c98275fb54)
![Q1 1 1 2](https://github.com/user-attachments/assets/f45da919-3c94-4da8-95e3-efc5da565b5e)
![Q1 1 1 3](https://github.com/user-attachments/assets/42cd5fb2-f356-4c95-af6a-7365bf095bbe)


- **Q.1.1.2 Créer une OU DeactivatedUsers et déplace le compte désactivé de Kelly Rhameur dedans.**
  
  ![Q1 1 2 1](https://github.com/user-attachments/assets/93d67360-be69-43ba-9631-6a1206b605b2)
![Q1 1 2 2](https://github.com/user-attachments/assets/79ec04ec-2a82-4a7e-87d4-8cefc6bbd3c8)


- **Q.1.1.3 Modifier le groupe de l'OU dans laquelle était Kelly Rhameur en conséquence.**
  
  ![Q1 1 3 1](https://github.com/user-attachments/assets/0d8a88c8-9a54-4bfe-983e-1edf451756de)
![Q1 1 3 2](https://github.com/user-attachments/assets/03aedb91-f844-48a7-8ef9-b0aabd676de1)


- **Q.1.1.4 Créer le dossier Individuel du nouvel utilisateur et archive celui de Kelly Rhameur en le suffixant par -ARCHIVE.**

#### Partie 2 : Restriction utilisateurs

- Q.1.2.1 Faire en sorte que l'utilisateur Gabriel Ghul ne puisse se connecter que du lundi au vendredi, de 7h à 17h.

- Q.1.2.2 De même, bloquer sa connexion au seul ordinateur CLIENT01.

- Q.1.2.3 Mettre en place une stratégie de mot de passe pour durcir les comptes des utilisateurs de l'OU LabUsers.

#### Partie 3 : Lecteurs réseaux

- Q.1.3.1 Créer une GPO Drive-Mount qui monte les lecteurs E: et F: sur les clients.
