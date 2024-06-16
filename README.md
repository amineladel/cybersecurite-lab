# Lab 3 

### Question 1

```bash
openssl genrsa -out mySmall.pem 1024
```
### Question 2

```bash
openssl rsa -in mySmall.pem -text -noout
```

- openssl rsa : C'est la commande de base pour les opérations liées aux clés RSA dans OpenSSL.
- in mySmall.pem : Spécifie le fichier contenant la clé privée RSA à afficher. Remplacez "mySmall.pem" par le nom de fichier correct si vous avez utilisé un nom différent.
- text : Demande à OpenSSL de décoder les informations de la clé RSA en texte lisible.
- noout : Prévient OpenSSL de ne pas écrire la clé RSA elle-même en sortie.

### Question 3

Stocker une clé privée en texte clair n'est pas recommandé dans un contexte réel, car cela la rend vulnérable à l'accès non autorisé. La sécurité des clés privées est cruciale dans le cryptage asymétrique, car elles permettent de déchiffrer des messages ou de signer des documents numériquement, donnant ainsi accès à des informations sensibles.

### Question 4

```bash
openssl genrsa -out private1.pem 1024
```

### Question 5

```bash
openssl genrsa -out private2.pem 1024
```

### Question 6



Pour le fichier "private1.pem" :

```bash
openssl rsa -in private1.pem -text -noout
```

Pour le fichier "private2.pem" :

```bash
openssl rsa -in private2.pem -text -noout
```

### Question 7

Pour "private1.pem"

```bash
openssl rsa -in private1.pem -pubout -out public1.pem
```

Pour "private2.pem"
```bash
openssl rsa -in private2.pem -pubout -out public2.pem
```

### Question 8 

Oui, il est courant et sécuritaire de stocker la clé publique en texte clair. Voici pourquoi :

1. Fonctionnement des clés publiques :
2. Interopérabilité :
3. Pratique :
4. Aucune information sensible :

### Question 9

Pour "public1.pem"
openssl rsa -pubin -in public1.pem -text -noout

Pour "public2.pem"
openssl rsa -pubin -in public2.pem -text -noout


### Question 10

openssl genrsa -out private4096.pem 4096

### Question 11

openssl rsa -in private4096.pem -pubout -out newPublic4096.pem

### Question 12

openssl rsa -in private4096.pem -text -noout

### Question 13

openssl rsa -in private4096.pem -out private4096_encrypted.pem -aes256

-> pass phrase : azerty

### Question 14

Commençons par la courbe P-224, également connue sous le nom de "secp224k1". Voici les étapes à suivre pour générer une clé privée EC avec OpenSSL :


```
openssl ecparam -genkey -name secp224k1 -out private_secp224k1.pem
```



Pour "prime256v1" :

```
openssl ecparam -genkey -name prime256v1 -out private_prime256v1.pem
```

Pour "secp384r1" :

```
openssl ecparam -genkey -name secp384r1 -out private_secp384r1.pem
```

Ces commandes vous permettront de générer des clés privées pour trois types différents de courbes elliptiques, stockées chacune dans leur propre fichier.

### Question 16

Étape 1 : Chiffrer la Clé Privée avec 3DES

- openssl pkcs8 -topk8 -v2 des-ede3-cbc -in private_secp224k1.pem -out private_secp224k1_encrypted.pem

Étape 2 : Générer la Clé Publique à partir de la Clé Privée Chiffrée

openssl ec -in private_secp224k1.pem -pubout -out public_secp224k1.pem

### Question 18

Enc :

openssl rsautl -encrypt -in message.txt -inkey public1.pem -pubin -out message.enc

Dec : 

openssl rsautl -decrypt -in message.enc -inkey private1.pem -out message_decrypted.txt

