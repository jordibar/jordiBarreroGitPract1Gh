# jordiBarreroGitPract1Gh
# RESPUESTAS DEL EJERCICIO 1 DE LA PRIMERA PRÁCTICA DE GIT

### ¿Qué comando utilizaste en el paso 11? ¿Por qué?

He utilizado el siguiente comando:

```
git reset --hard HEAD~1
```

La razón de utilizar --hard es que queríamos perder los cambios realizados en el working copy.


### Qué comando o comandos utilizaste en el paso 12? ¿Por qué?

Si hacemos un git log no nos aparece el commit al que queremos regresar, por lo que tenemos que utilizar git reflog. Este comando nos muestra una lista de los commits que hemos ido haciendo y cómo hemos llegado al commit.
Lo importante aquí es obtener el identificador único del commit que nos interesa y lo aplicamos al siguiente comando:

```
git reset --hard identificadorUnico
```

### El merge del paso 13 ¿causó algún conflicto? ¿Por qué?

No causa ningún conflicto ya que la rama master no ha sido modificada desde que se creó la rama styled como hija de master.

### El merge del paso 19 ¿causó algún conflicto? ¿Por qué?

Sí que se produce un conflicto ya que en ambas ramas se había modificado el mismo documento aplicándole contenido distinto, por lo que tenemos que resolver este conflicto antes de poder hacer el merge.

### El merge del paso 21 ¿causó algún conflicto? ¿Por qué?

No causa ningún conflicto ya que la rama master no ha sido modificada, por lo que se copia el contenido de git-nuestro.md haciendo un merge Fast-Forward.

### ¿Qué comando o comandos utilizaste en el punto 25?

Se ha utilizado el comando:

```
git log --graph --decorate --pretty=oneline
```

Con este comando vemos las ramas a la derecha y nos muestra un git log resumido, sin autor ni fecha...

### El merge del punto 26 ¿Podría ser Fast-Forward? ¿Por qué?

Se ha utilizado el comando:

```
git merge --no-ff title
```

Este merge sí que podría ser Fast-Forward ya que estamos mergeando un commit hijo y no hemos modificado el padre, por lo que avanzando el puntero de la rama que absorbe a la rama absorbida sería suficiente.

### ¿Qué comando o comandos utilizaste en el punto 27?

El primer comando utilizado ha sido:

```
git reflog
```

Con reflog podemos coconer el ID del commit al que queremos movernos, en nuestro caso, el previo a hacer merge.

A coninuación no movemos a este commit con el identificador y git reset:

```
git reset idDelCommit
```

Lo hacemos sin --hard para mantener el Working Copy, al hacerlo se nos muestra un aviso 'unstaged changes after reset' ya que el archivo git-nuestro.md de nuestro Working Copy todavía contiene el título, cuando en realidad, en el commit en el que estamos no lo tenía.
Lo podemos verificar con:

```
cat git-nuestro.md
```

### ¿Qué comando o comandos utilizaste en el paso 28?

Para descartar los cambios en nuestro Working Copy utilizamos el comando:

```
git checkout -- git-nuestro.md
```

Lo que hacemos es recuperar el estado del archivo tal y como está en el repo, descartando los cambios hechos en nuestro Working Copy.

Podemos verificarlo haciendo:

```
cat git-nuestro.md
```

###¿Qué comando o comandos utilizaste en el punto 29?
El comando utilizado ha sido:

```
git branch -D title
```

Al eliminar una rama en el grafo significa que desaparece el puntero, no se borran commits ni se pierde información.


### ¿Qué comando o comandos utilizaste en el punto 30?
1) Empezamos con el comando git reflog para copiar el id del commit al que queremos movernos.


2) Nos movemos al commit

```
git checkout idCommit
```

Git nos informa de que estamos en 'Detached HEAD' ya que estamos en un commit y no en una rama.

3) Creamos una rama provisional:

```
git branch provisional
```

4) Nos movemos a la rama master:

```
git checkout master
```

5) Hacemos un merge para que master absorba los cambios del commit anterior:

```
git merge provisional
```

6) Eliminamos la rama creada proviosional, ya no la necesitamos:

```
git branch -D provisional
```


### ¿Qué comando o comandos utilizaste en el punto 32?

Aquí podríamos utilizar reset o checkout.

Priemro copiamos el Id del commit que nos interesa desde reflog
Se ha utilizado reset --hard para modificar lo que hay en el Working Copy.

```
git reset --hard idDelPrimerCommit
```



###¿Qué comando o comandos utilizaste en el punto 33?
Hacemos lo mismo que en el punto anterior, con el reflog copiamos el Id del commit que nos interesa y nos movemos con reset --hard

```
git reset --hard idDelUltimoCommit
```



