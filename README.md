# TO52_VR_Drone_simulator
Compiler l’api, l’interface et autres spécifications sur le projet

Compiler l’api Airsim : 

- Installer gradle sur le Pc
 - Ouvrir l’invité de commande dans le dossier contenant le fichier gradlew.bat 
 - Entrer la commande de build : « .\gradlew clean build » ou « .\gradlew build »
 

Compiler l’interface Sarl-Airsim:

1.	Avoir compilé org.msgpack version 0.6.12,    org.msgpack-core version 0.8.20,   org.msgpack.rpc version 0.7.1 (à partir du lien « https://mvnrepository.com/artifact/com.github.stampery/msgpack-rpc/0.7.1 »)

2.	Pour le fichier .jar du org.msgpack.rpc (obtenu en compilant), placez le dans un dossier « lib » créé dans le dossier « src » du projet.

3.	Si besoin, installer également un « slf4j provider » avec le lien suivant (« https://mvnrepository.com/artifact/org.slf4j/slf4j-api »). Utilisez la version 2.0.9 idéalement. Vérifiez après la compilation du slf4j que le fichier correspondant ait bien été créé dans le dossier m2 de votre Pc. (/windows/utilisateur/…/.m2/repository/org/)


4.	Les trois dépendances sont ajoutées avec les lignes suivantes du pom.xml, le path du org.msgpack.rpc doit être complété avec le path de votre dossier :
<dependency>
	<groupId>org.msgpack.rpc</groupId>
	<artifactId>msgpack-rpc</artifactId>
	<scope>system</scope>
	<version>0.7.1</version>
	<systemPath>C:\…\src\lib\msgpack-rpc-0.7.1.jar</systemPath>
</dependency>
<dependency>
	<groupId>org.msgpack</groupId>
	<artifactId>msgpack</artifactId>
	<version>0.6.12</version>
</dependency>
<dependency>
	<groupId>org.msgpack</groupId>
	<artifactId>msgpack-core</artifactId>
	<version>0.8.20</version>
</dependency> 




Lancer le programme Sarl à partir du fichier .jar créé par la compilation :

-	Ouvrez un invité de commande dans le dossier contenant le fichier .jar compilé (dans le dossier \target) et entrez la commande suivante : 
java -cp .\sarl-airsim-interface-0.0.1-SNAPSHOT-cli.jar io.sarl.sre.janus.boot.Boot io.sarl.airsim.BootAgent
-	Cette commande lancera le fichier .jar « sarl-airsim-interface-0.0.1-SNAPSHOT-cli.jar » en utilisant l’environnement « io.sarl.sre.janus.boot.Boot » et en utilisant le fichier « io.sarl.airsim.BootAgent » comme point d’entrée du programme. Le programme prend quelques secondes à démarrer.
Changer le nombre de drones OU problèmes sur les noms/nombres de drones
-	Vérifier le nombre et les noms des drones dans le fichier « settings.json » situé dans le dossier Airsim  vérifiez également que leurs noms soient les mêmes que ceux du fichier « settings_20drones_circle.json » situé dans src/main/ressources du dossier de l’interface sarl/airsim. Recompilez l’interface si besoin.

Utiliser AirLink pour la simulation :

-	Nécessite un compte Meta
-	Installer l’application Oculus sur le PC et se connecter et lancer l’application
-	Allumer le casque VR
-	Se connecter sur le même réseau que le PC
-	Si besoin ajoutez votre casque actuel dans la liste de vos casques VR dans l’application Oculus sur PC en suivant les étapes assez simples
-	Aller dans les paramètres du casque et cliquez sur Quest Link 
-	Cochez la case « Activer AirLink » 
-	Votre PC devrait s’afficher dans la liste des appareils disponibles, si oui cliquez dessus et valider le code sur le PC et sur le casque. Si votre PC ne s’affiche pas, vérifiez votre réseau et si votre appareil est bien affiché comme « connecté/ détecté » dans la liste de vos casques sur l’application oculus de votre PC (ajoutez le dans la liste si besoin).
-	Si tout se passe comme prévu, vous devriez arriver sur le menu AirLink dans le casque ; A ce moment, lancez Unreal sur votre PC pour utiliser l’application et lancez le projet. Utilisez le mode ‘VR Preview’ disponible en cliquant sur la flèche déroulante à côté du lancement général du projet unreal.
-	Le projet devrait maintenant être visualisable depuis le casque.
