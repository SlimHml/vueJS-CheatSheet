### VueJS Débutant

![alt text](./images/screenVue1.png)

Ici, l'id "Root" dans le HTML est branché à l'élément dans l'instance de VueJS, celà permet de l'intéraction avec le DOM

Le **v-model** est une directive connecté à **L'input** et branché à **L'email** indiqué dans la **Data** de **l'instance de vue** permet de faire transiter les infos dans les deux sens, **:class** permet d'appliquer une classe CSS (ici sous condition ternaire, sous 2 le cadre est **rouge**, au dessus il passe au **vert**)

**onclick** est un **écouteur d'évènement** qui déclenche une alerte dans ce cas ci, et le bouton est **:disabled** si le contenu de l'input est inférieur à 2, celui-ci sera **incliquable**

![alt text](./images/screenVue2.png)

Ici, **l'interpolation** (les doubles accolades, ou moustaches) permet d'adapter le contenu de la balise <p> (dans ce cas-ci) au contenu de **email** indiqué dans la data, l'email **cats@cats.com** écrit en dur permet juste de démontrer que le v-once bloque **toute nouvelle tentative de modification dans l'input**

![alt text](./images/screenVue3.png)

Ici, on indique dans la data **cats**, qui est un **tableau**, des noms de chats écrits en dur

Grâce à la directive **v-for**, branchée à une **li** dans ce cas-ci, javascript va boucler dans **cats**, on utilise ensuite une **interpolation** afin de display les noms de chats sous forme de **li** de l'index 0 du **tableau** jusqu'au dernier

![alt text](./images/screenVue4.png)

Ici même chose, nous pouvons boucler dans un tableau **d'objets**, on indique dans **l'interpolation** que l'on veut boucler dans le **nom** des chats par un "**.quelquechose**"

![alt text](./images/screenVue5.png)
Ici, le **v-model** est branché sur l'input et sur **newCat** dans **data**, qui est à la base, un **string vide**, le **v-on:click** branché sur le bouton va déclencher l'évènement **addKitty**, qui fait appel à une **fonction** écrite dans **methods**, cette fonction va push dans **cats**, qui est, je le rappelle **un tableau d'objets**, un nouvel **objet** "**stringifié**" avec comme attribut **name** le contenu de **l'input**
