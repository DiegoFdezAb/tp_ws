# TP curl - comprendre les requêtes et les réponses HTTP

Pour les questions suivantes, vous devez utiliser l'url suivante : https://webhook.site/6f594809-a4b4-483e-841b-0c3b0a00edfe

Pour tous les appels vous devez ajouter un header pour identifier votre appel parmis ceux des autres étudiants : x-student : VOTRE_NOM

## Faire un appel curl : copier la commande exécutée et indiquer la requête et la réponse

curl -I https://webhook.site/6f594809-a4b4-483e-841b-0c3b0a00edfe -H "x-student : Diego"

## Quel est la version du protocole utilisé par le serveur ?
HTTP/1.1

## Quels sont les headers que l'on envoie dans la requête ? Quels sont leur sens ?
Les headers sont des donées additionneles entre le client et le serveur, ça peut-être une liste de langues supportés par exemple. Leur sens est bi-directionnel, le client envoie des données et le serveur aussi.

## Quelles informations pouvez-vous trouver à propos du certificat SSL ?
SSL connection using TLSv1.3 / TLS_AES_256_GCM_SHA384 

Server certificate:                                                                                                *  subject: CN=webhook.site                                                                                          *  start date: Jul 31 23:09:19 2022 GMT                                                                              *  expire date: Oct 29 23:09:18 2022 GMT                                                                             *  subjectAltName: host "webhook.site" matched cert's "webhook.site"                                                 *  issuer: C=US; O=Let's Encrypt; CN=R3                                                                              *  SSL certificate verify ok.

## Quel est le code de la réponse ? Que signifie-t-il ?
200 OK, ceci indique la réussite d'une requête

## Quels headers recevez vous dans la response ? Quels sont leur sens ?

Server: nginx                                                                                                        Content-Type: text/plain; charset=UTF-8                                                                              Vary: Accept-Encoding                                                                                                X-Request-Id: cbacc752-d439-4f82-9b71-55e9e9b85463                                                                   X-Token-Id: 6f594809-a4b4-483e-841b-0c3b0a00edfe                                                                     Cache-Control: no-cache, private                                                                                     Date: Tue, 04 Oct 2022 14:44:54 GMT  

## Faire un appel curl en envoyant du texte brut : copier la commande exécutée et indiquer la requête et la réponse
curl -X POST -i -H "Content-Type: text/plain" --data "test" https://webhook.site/6f594809-a4b4-483e-841b-0c3b0a00edfe 

HTTP/1.1 200 OK                                                                                                      Server: nginx                                                                                                        Content-Type: text/plain; charset=UTF-8                                                                              Transfer-Encoding: chunked                                                                                           Vary: Accept-Encoding                                                                                                X-Request-Id: 01e9bb9d-ff75-4499-9c39-09832a550597                                                                   X-Token-Id: 6f594809-a4b4-483e-841b-0c3b0a00edfe                                                                     Cache-Control: no-cache, private                                                                                     Date: Tue, 04 Oct 2022 15:07:31 GMT 

## Faire un appel curl en envoyant du JSON (avec les bons headers) : copier la commande exécutée et indiquer la requête et la réponse

curl -i -X POST -H "Content-Type: application/json" --data "{"test":"lol"}" https://webhook.site/6f594809-a4b4-483e-841b-0c3b0a00edfe

HTTP/1.1 200 OK                                                                                                      Server: nginx                                                                                                        Content-Type: text/plain; charset=UTF-8                                                                              Transfer-Encoding: chunked                                                                                           Vary: Accept-Encoding                                                                                                X-Request-Id: 84744681-ffb8-4dd0-8f05-d292e33c9423                                                                   X-Token-Id: 6f594809-a4b4-483e-841b-0c3b0a00edfe                                                                     Cache-Control: no-cache, private                                                                                     Date: Tue, 04 Oct 2022 15:06:39 GMT   

## Faire une appel curl en envoyant une basic authentication en utilisant 2 méthodes différentes : copier les commandes exécutées et indiquer la requête et la réponse à chaque fois 

curl https://webhook.site/6f594809-a4b4-483e-841b-0c3b0a00edfe -u "diego:diego"

curl https://webhook.site/6f594809-a4b4-483e-841b-0c3b0a00edfe -H "Authorization: Basic token"


## Exécuter la commande suivante avec la méthode GET puis indiquer la réponse : curl https://demo.api-platform.com/books/07dd4786-aaa7-4d08-a467-076b76f1d1b6 

{"@context":"\/contexts\/Error","@type":"hydra:Error","hydra:title":"An error occurred","hydra:description":"Not Found"}

## Exécuter la commande suivante avec la méthode PATCH  puis indiquer la réponse : curl https://demo.api-platform.com/top_books/1

<!DOCTYPE html>
<html>
<head>
    <meta charset="UTF-8" />
    <meta name="robots" content="noindex,nofollow,noarchive" />
    <title>An Error Occurred: Method Not Allowed</title>
    <style>body { background-color: #fff; color: #222; font: 16px/1.5 -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif; margin: 0; }
.container { margin: 30px; max-width: 600px; }
h1 { color: #dc3545; font-size: 24px; }
h2 { font-size: 18px; }</style>
</head>
<body>
<div class="container">
    <h1>Oops! An Error Occurred</h1>
    <h2>The server returned a "405 Method Not Allowed".</h2>

    <p>
        Something is broken. Please let us know what you were doing when this error occurred.
        We will fix it as soon as possible. Sorry for any inconvenience caused.
    </p>
</div>
</body>


## Quel est le code HTTP reçu ? Quel est sa signification ?


Avec le GET on a une erreur, on n'obtient pas le titre du livre ni la description.

Avec le PATCH on obtient une erreur 405, ce qui veut dire que notre requête PATCH n'est pas autorisé.

## Exécuter la commande suivante puis indiquer la réponse : curl https://demo.api-platform.com/top_books/1

{"@context":"\/contexts\/TopBook","@id":"\/top_books\/1","@type":"TopBook","id":1,"title":"Depuis l\u0027au-delà","author":"Werber Bernard","part":"","place":"F WER","borrowCount":9}
  
## Exécuter la commande suivante puis indiquer la réponse : curl https://demo.api-platform.com/top_books/9999

  {"@context":"\/contexts\/Error","@type":"hydra:Error","hydra:title":"An error occurred","hydra:description":"Not Found"}

## Quel est le code HTTP ? Que signifie-t-il ?

On obitent le livre numéro 1. Cependant le livre numéro 9999 n'existe pas et donc on obtient une erreur.

## Exécuter la requête suivante et copier la réponse : curl https://google.fr

  <HTML><HEAD><meta http-equiv="content-type" content="text/html;charset=utf-8">
<TITLE>301 Moved</TITLE></HEAD><BODY>
<H1>301 Moved</H1>
The document has moved
<A HREF="https://www.google.fr/">here</A>.
</BODY></HTML>


## Quel est le code HTTP reçu ? Pouvez-vous expliquer cette réponse ?

  On reçoit un code 301 Moved, ce qui signifie que l'URL a été déplacé vers un nouvel URL.

## Comment éviter cette réponse ? Trouvez 2 solutions différentes et détaillez les.
  
  curl https://google.fr -L 
  
  Ceci nous rajoute la commande --location, ceci marche car l'on a l'erreur 301 qui indique que l'URL demandé a un nouvel URL et le nouvel URL est marqué dans le header location.
  
  curl https://www.google.fr
  
  Ceci marche puisque c'est la nouvelle adresse avec les "www".
