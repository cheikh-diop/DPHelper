Requis : 
JRE 8 minimum , Distribution Linux / Matériels (Minimum requis pour compiler un programme Java )
IntellijIdea avec Maven installe .

Projet : dpHelper 

    -ressources :==> contient les programmes de pour tester le fonctionnement de l'extension.        

    -src        :==> contient le code source de l'outil .  
        -dpHelper

            -annotations :==>  contient les annotations pour les différents design pattern implémenté .
               
            -exceptions  :==>  contient l'ensemble des classes d'exceptions de l'extension .
           
            -generators :==>  contient l’ensemble des classes de génération de code spécifique à chaque pattern. 

            -tools      :==>  contient les classes utilitaires de gestions des messages erreurs.

              
            -verifiers     :==>  contient le code des vérificateurs pour chaque design pattern ainsi que le dossier fluentapi

                -fluentapi :==>  contient un ensemble de classe dont toutes les méthodes servent à effectuer des recherches 
				 dans les objets Element (dans le code)

                PatternVerifier.java  :==> Elle  est  l’interface  commune à  toutes  les  classes  de  Vérifications.  
					   Elle  contient  la  signature  de  la  méthode verifyAll(Collection<Element> annotatedElements) qui est appelée dans l
					   a fonction process de PatternProcessor sur les sous classes associées aux annotations traitées.        
                
            -visitors    :  :==> contient uniquement des visitor scanner. Ces visitor étendent tous une classe
				 abstraite principale qui implémente l’interface ElementScanner8 contenu dans javax.lang.model.util.
				 Chaque visiteur permet d’effectuer des comparaisons sur des parties différentes des éléments du code (modifiers, type, ...). 

            PatternsProcessor.java  :==> Classe principale du vérificateur .        

    -target :==> Contient les dossiers et fichiers generes apres la compilation
  
        PatternsHelper-1.0.jar      :==> Exécutable de l'outil qui est généré apres la compilation .
         
    -test    
        -coverTests         :==> contient les tests de couvertures réalisés pour les design patterns implemente .
               
        -unitTests          :==> contient les test unitaires pour les différents modules du projets .
            

    launchCompiler.sh       
    pom.xml :==> fichier de configuration du projet maven
    README

Il faut utiliser des annotations pour utiliser l'outils

-->Design Pattern Singleton 
	@Singleton : pour annoter une classe qui implémente le Singleton .
	@Singleton.SYNCHRONIZED : pour annoter une classe qui implemente le singleton avec la strategie synchronisee
-->Design Pattern ABSTRACT FACTORY 
	@AbstractFactory.Factory : pour annoter la fabrique abstraite .
	@AbstractFactory.Product: pour annoter l'interface produit abstrait .
-->Design Pattern VISITOR 
	@Visitor.Concret :  pour annoter la l'interface qui est implémenté par les visiteur concret .
	@Visitor.Visitable: pour annoter l'interface qui est implémenté par les classes a visite(les visitables) .
Nb : Dans la version actuelle de Dphelper pour le design pattern Observer et Decorator il faudrait annoter l'ensemble des composants 
-->Design Pattern OBSERVER 
	@Observer(Observer.ROLE.INTERFACE_OBSERVER) : pour annoter l’entité qui est implemente par les observer(Observateur ) .
	@Observer(Observer.ROLE.ABSTRACT_OBSERVABLE): pour annoter l’entité qui est implémenté par les Observable(acteur ).
	@Observer(Observer.ROLE.OBSERVER) : pour annoter les Observerconcret (les classes observateurs ).
	@Observer(Observer.ROLE.OBSERVABLE): pour annoter les Observableconcret (les classes acteurs ).
-->Design Pattern Decorator
	@Decorator(Decorator.ROLE.COMPONENT) : pour annoter l'interface qui est implémenté par la famille de classe a décoré .
	@Decorator(Decorator.ROLE.COMPONENT_CONCRETE): pour annoter les classes a décoré.
	@Decorator(Decorator.ROLE.DECORATOR) : pour annoter l'interface des décorateurs .
	@Decorator(Decorator.ROLE.DECORATOR_CONCRETE): pour annoter les décorateurs .


Lancer les quelques tests unitaires : mvn test
mvn -Dmaven.test.skip=true install

Compiler le projet (générer le fichier .jar) 
se placer dans le répertoire 
patternsHelper/
lancer la commande :==> mvn install -DskipTests

Faire une vérification sur un fichier Java

lancer la commande avec les paramètres qu'il faut :==> javac -cp chemin/../Extension.jar package/[nom_fichier].java

Faire une vérification sur une hiérarchie de classe 

lancer la commande avec les paramètres qu'il faut :==>javac -cp chemin/../Extension.jar package/*.java

----------------------------Auteurs-------------------------------- :
Hasssana Fikri---Talibe Balde---Bineta Diagne---Cheikh A B DIOP

Master Informatique Université de Bordeaux 2016/2017