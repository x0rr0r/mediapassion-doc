==============================
Documentation API MediaPassion
==============================

Cette api permet l'accès aux informations de la base de données Media-Passion via des systèmes de requêtes simples et des retours dans un format facilement utilisable par vos applications. (XML uniquement pour le moment, JSON prochainement)

Pré-requis
----------
Vous devez disposer d'une clé API pour pouvoir utiliser la base de Media-Passion. Cette clé ne doit en aucun cas être diffusée en clair dans votre application. 

Utilisation
-----------
En plus de la clef API qui identifie votre application, vos utilisateurs devront être inscrits sur le site www.media-passion.org pour pouvoir accéder aux informations de la base. Afin de ne pas faire transiter en clair ces identifiants, ceux-ci seront transmis sous la forme d'un "hashcode". Aussi, pour utiliser la version sécurisée de l'api, vous remplacerez les champs Username et APIPassword respectivement par : 
- le login encodé en base64 (cela permet signaler à l'API que le mot de passe ne sera pas en clair, et de basculer en mode sécurisé) 
- un sha1 (algorithme de hachage sécurisé) de la concaténation du login en minuscule et du mot de passe. 

Exemple en PHP
``` php
$Username = base64_encode($login);
$Password = sha1(strtolower($login).$apipassword);
```

Exemple en Python
``` python
import base64
Username = base64.b64encode( "login" )
 
import sha
Password = sha.new( "login".lower() + "apipassword" ).hexdigest()
```
