# TP-Docker

# Premièrement récupérer lapplication à dockeriser sur le GitHub lauryao :  
$git clone [lien du répertoire/dossier à dockeriser] 

# Pour une dockerisation organisé créer deux répertoires : 
- /tomcat/
- /postgres/

# Dans les répertoires tomcat & postgres copier :  
- Dans tomcat    -->    le fichier code du lien GitHub
- Dans postgres  -->    le ficher SQL du lien GitHub

# Toujours dans les répertoires tomcat & postgres jai créée dans chacun un fichier Dockerfile : 
$vi Dockerfile

# Dans le Dockerfile de tomcat entrer :  
FROM tomcat:8-jre8      
COPY ./fichier_code_copié /usr/local/tomcat/webapps

# Dans le Dokerfile de postgres entrer :  
FROM postgres:9.5   
COPY ./ficher_sql_copié /docker-entrypoint-initdb.d/  

# maintenant construire limage postgres :
$docker build -t donner_un_nom_a_limage . 

# Puis construire limage tomcat :
$docker build -t  donner_un_nom_a_limage .

NB : Pour vérifier si les images sont bien créées faire la commande : 
$docker images

# Après la construction des images, créer les containers :  
- Pour postgres :
$docker run -d --name donner_un_nom_au_container nom_de_limage_postgres

- Pour le tomcat :
$docker run -d --name donner_un_nom_au_container -p choix_du_port:8080 --link nom_du_container_postgres nom_de_limage_tomcat

NB : Pour vérifier si les containers sont bien en cours dexécution entrer la commande suivante :  
$docker ps

# Après avoir fait tout ça tester maintenant votre application dockerisé 
- Aller sur votre navigateur et entrer le lien suivant :
Votre_adresse_ip:votre_port_choisi/dbprojet/accueil.jsp   

Et tout fonctionne.  
