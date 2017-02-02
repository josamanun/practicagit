# PracticaGit

En este repositorio realizaremos la practica de Git.

### Provocación y resolución de un conflicto con git.

* Lo primero que hice fue crearme una rama nueva llamada feature y automaticamente moverme a ella

```java
$ git checkout -b feature
Switched to a new branch 'feature'
```

* Seguidamente hice un cambio en un comentario e hice commit

```java
$ git commit -m "comentario en la clase principal modificado"
[feature 2f98c43] comentario en la clase principal modificado
 1 file changed, 1 insertion(+), 1 deletion(-)
```

* Hice checkout a la rama master e hice un cambio tocando la misma linea que había tocado anteriormente en la otra rama

```java
$ git checkout master
Switched to branch 'master'
Your branch is up-to-date with 'origin/master'.

$ git commit -m "cambio en comentario en clase principal"
[master 8f85df1] cambio en comentario en clase principal
 1 file changed, 1 insertion(+), 1 deletion(-)
```

* Ahora intenté hacer un merge (fusión) con la rama feature de la siguiente manera y seguidamente me dio el conflicto:

```java
$ git merge feature
Auto-merging src/main/java/org/alemurrod/MaquinaExpendedora.java
CONFLICT (content): Merge conflict in src/main/java/org/alemurrod/MaquinaExpendedora.java
Automatic merge failed; fix conflicts and then commit the result.
```

* Lo que nos toca ahora es arreglar el conflicto, git no sabe con que archivo quedarse, por eso nos toca decidir a nosotros. Hay muchas maneras de hacerlo, podemos ir directamente al archivo y modificarlo y arreglarlo nosotros y también podríamos usar algunos comandos para hacer merge los cuales les dice a git como tiene que actuar en caso de conflicto. Yo primero aborté el merge anterior y volvi a realizar los pasos anteriores para crear el conflicto de nuevo, sin embargo, ahora utilizé el comando siguiente:

```java
$ git merge -s recursive -X ours feature
Merge made by the 'recursive' strategy. 
```

* El comando anterior le dice a git que cuando encuentre un conflicto se quede con lo que haya en el archivo de la rama en la que estemos en ese momento (ours = nuestr@). En este caso lo hice desde la rama master, entonces se quedaron los cambios de la rama master en la parte donde había conflicto.



---

A la hora de volver atrás cuando causé el conflicto lo hice de mala manera, usando para ello git reser hard con la id del commit al que quería volver, debido a esto han salido 2 o 3 commits más de lo que esperaba. 
Aunque al final conseguí resolver el conflicto de manera correcta, para la siguiente vez ya se los pasos a seguir y espero actuar de manera diferente.

