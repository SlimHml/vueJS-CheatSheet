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
Ici, le **v-model** est branché sur **l'input** et sur **newCat** dans **data**, qui est à la base, un **string vide**, le **v-on:click** branché sur le bouton va déclencher l'évènement **addKitty**, qui fait appel à une **fonction** écrite dans **methods**, cette fonction va push dans **cats**, qui est, je le rappelle **un tableau d'objets**, un nouvel **objet** "**stringifié**" avec comme clé **name** et comme valeur le contenu de **l'input**

![alt text](./images/screenVue6.png)

Ici, on a ajouté un nouvel **écouteur d'évènement**, qui est sur keyup, si on ne précise pas une touche, n'importe quelle touche activera **addKitty**, d'où la précision **.enter** pour indiquer seulement la touche **entrée**

![alt text](./images/screenVue7.png)

Simple modification afin de **clean** l'input, la methode **addKitty** se voit ajouter une string vide sur **l'input** où est branché le **v-model**

![alt text](./images/screenVue8.png)
il est possible d'ajouter des **filters**, ici indiqué par les **pipes** dans **l'interpolation**, juste après le **v-for**, ces indiquations vont **trigger** la **fonction** capitalize puis la **fonction** kittify

![alt text](./images/screenVue9.png)

Une **computed property** est une fonction "**greffée**", qui permet d'alléger

En effet, une propriété calculée sera réévaluée uniquement quand certaines de ses dépendances auront changé. Cela signifie que tant que **newCat** n’a pas changé, les multiples accès à la propriété calculée **kittifyName** retourneront immédiatement le résultat précédemment calculé sans avoir à réexécuter la fonction.

Nous pouvons aussi utiliser une méthode, mais celle-ci peut être couteuse en performance sur de grands tableaux, la doc de VueJS à propos des **computed properties** est à revoir

Mais grosso modo, il s'agit d'améliorer les performances dans certains cas

![alt text](./images/screenVue11.png)

Ici, nous abordons la notion de composant, il est crée dans ce cas ci, dans une instance "**component**", avec le nom du composant (cat-list), nous avons utilisé la directive **v-bind** dans le HTML dans la **balise auto fermante** incluse dans la balise racine (#root), avec dans son template la même **li** contenant le **v-for**, un **v-bind** à un endroit nécessite que l'on le lie grâce au **props** dans le script de l'endroit où nous incluons ce fameux **composant**

![alt text](./images/screenVue12.png)

Ci-dessus, il s'agit des cycles de vie. Voir les cycles de vie, **IMPORTANT**

[Cycles de vie VueJS](https://fr.vuejs.org/v2/guide/instance.html)

![alt text](./images/screenVue13.png)

Ci-dessus, nous abordons vue CLI, **vue create 'nom du dossier'** crée un boiler plate (en fonction des parametres de création), avec une arborescence préconçue, le point d'injection se trouve sur une **id** app dans le /public HTML, monté à partir de main.js, qui a sa source en **App.vue**, ici, deux fichiers de **composants** (dans components) ont été crées (**Header.vue et QuestionBox.vue**), ceux-ci ont été exportés dans une balise script, puis importés dans **App.vue**, dans le script donc, via "**import xxx from 'xxx'**, utilisés dans une balise auto fermante dans le **template** (non affiché sur le screenshot) puis exportés dans la section **components** du script d'**App.vue** afin que le main.js l'injecte dans l'**HTML**

L'ordre dans lequel sont "**utilisés**" les composants dans le template compte, le **Header** appelé **avant**, sera donc au dessus de **QuestionBox** appelé **en dessous**

![alt text](./images/screenVue14.png)

Ci-dessus, nous avons un exemple de **consommation d'API**, nous indiquons dans le script d'**App.vue** quand nous **souhaitons** exécuter la fonction anonyme, qui va **GET** les informations de l'**API** via l'**URL** et **fetch** (équivalent d'**Axios** mais qui est inné dans **Javascript**, donc **indépendant**)

Dans cet exemple, la **fonction** sera executée lors du **cycle de vie** **MOUNTED**.

![alt text](./images/screenVue15.png)

Le **console.log** du screenshot du dessus pose problème, en effet, il n'accepte pas de CL dans le script, pour régler ceci, il faut se rendre ici: ![alt text](./images/screenVue16.png) et insérer dans **rules** le **no-console: false ou 0**

![alt text](./images/screenVue17.png)

Nous obtenons effectivement une promesse dans le console.log

![alt text](./images/screenVue18.png)

Ci-dessus, une fonction **data** pond un **objet** contenant un **tableau** nommé **questions**, celui-ci sera rempli via la succession de .then, qui a parsé la réponse en **.json**, puis injecter ce **jsonData** dans le **tableau questions** avec le **.result** qui va bien, ce **.result** correspond à ce que l'**API** emet, celle-ci emet un code, et **result**, qui contient les **questions / réponses**

![alt text](./images/screenVue19.png)

Nous pouvons voir ci-dessus, dans le **Vue devtools** que le **tableau questions** détient **10 index** après chargement de la page, (ce nombre de questions générées a été spécifié sur le site de l'API consommée), et chaque **index** correspond à un **objet** avec les **clés / valeurs**

![alt text](./images/screenVue20.png)

Afin de remplir la **balise enfant** **QuestionBox** avec les questions / réponses, on va appliquer un **v-bind** (ici raccourcit avec " : ") à la balise du composant, le nom de la variable, ainsi que **[index]** (qui indique **0** dans la **data** afin d'afficher la première question du **tableau**), mais pour que cela fonctionne, il faut attacher un props dans **QuestionBox.vue** et y mettre une interpolation là où l'on veut que la donnée soit injectée

![alt text](./images/screenVue21.png)

Il y'a dont **l'interpolation** dans la balise où nous souhaitons y mettre nos questions, mais afin d'utiliser cette **variable**, le **props** a bien été collé dans le **script**, avec le nom de la **variable** contenu dans le **parent** (**App.vue**), et désignant sa **nature**, en l'occurence: **Object**

![alt text](./images/screenVue22.png)

La première question est donc affichée dans l'emplacement indiqué

![alt text](./images/screenVue24.png)

Ci-dessus, afin de pouvoir passer à la question suivante (donc index 1, puis 2, puis 3 etc), elle crée une **methods**, avec une **fonction** next, aec une simple **incrémentation**

![alt text](./images/screenVue27.png)

Ci-dessus Cette **fonction** est ensuite **v-bindée** dans la balise enfant **QuestionBox** aussi

![alt text](./images/screenVue25.png)

Ensuite, ci-dessus, elle attache un **écouteur d'évènement** avec la directive **v-on:click** (ici raccourcit avec **@click**) sur un bouton, qui déclenchera la **fonction next** (qui incrémente l'index de 1)

![alt text](./images/screenVue26.png)

Puis ci-dessus, enfin un **props** qui le lie au **v-bind** du **parent** (App.vue), avec sa nature: **Function**

Il y'a un soucis désormais, currentQuestion est **undefined**, car pendant un bref instant, la donnée est inexistante, elle va donc rajouter une condition, tant que la donnée n'est pas fetch (GET) et qu'elle est sauvegardée dans le **tableau**, le **composant** **QuestionBox** ne sera pas rendu, donc pour résumer:

Obtenir la data => la stocker dans le tableau => Afficher le composant avec les données en le forçant à attendre

![alt text](./images/screenVue28.png)

Donc elle applique un **v-if**, avec comme condition: si la longueur du tableau est vraie (donc non vide) alors tu sers le composant **QuestionBox**

Le bouton **next** fonctionne désormais correctement, la donnée est chargée dans le tableau avant le composant, tout va bien

### methods: Construction d'une URL

```
buildUrl: function( route, params ){
            Object.keys( params ).forEach( ( key, index ) => {
              route += ( index == 0 ? '?' : '&' ) + key + "=" + params[ key ]
            })
            return route
        },
```

Cette fonction prend deux paramètres, la route, et les params
La route de base est connue pour telle ou telle fonctionnalité, exemple: 'www.google.com', mais pour une route particulière, il faut
construire l'URL, on va décomposer la fonction ci-dessus

Les params est une convention, il est un objet qui contient les paramètres de notre URL, un forEach est donc appliqué afin d'itérer sur
chacunes de ses clés et de ses index.

Donc prenons comme exemple **params** qui contient ceci: {imgChienId:42, rigolo:"fun"}

Route+= (additionne à route ('www.google.com')) **?** si **l'index** de **params** est de 0, **&** ensuite. Le **&** s'additionne ensuite car la route est désormais "www.google.com?imgChienId=42" et que l'index à ce niveau == 1


La route sera donc construite comme ceci: www.google.com?imgChienId=42&rigolo=fun

Le **=**, la **clé** et la **valeur de la clé** s'insèrent entre les **?** et les **&** car on concatène la route avec la **clé** (+ key)
, le **=** (+ "=") puis la valeur de la clé dans l'ordre de l'itération **(+ params[ key ])** 

```
data(){
   top: [],         
}
getChiensData: function ( type = 'categorie' ) {
          let route     = 'animaux/chiens/' + type
          let params    = { type: type + '_wtf', top: 5 }
          // Construction de l'URL
          let url       = this.buildUrl( route, params )
          axios.get( url )
              .then( ( res ) => {this.top = res.data})
```
Ici, un cas d'utilisation de notre fonction précédente **buildUrl**, on crée un tableau vide dans data, de n'importe quel nom.
On déclare une nouvelle fonction dans methods, on déclare une variable contenant notre route de base pour cette requête api, en l'occurence animaux/chien/categorie.
On déclare nos params, un objet, type: type n'est pas forcément très lisible, mais dans ce cas que j'ai rencontré, je devais passer **categorie** dans un composant enfant afin d'afficher la data directement en arrivant sur la page pour des soucis pratiques
Sinon pour un cas classique, ne donnez pas de paramètres à la fonction.

Nous déclarons ensuite une variable qui appelle buildUrl dans le contexte environnant, le **this** fait donc appel à la fonction **buildUrl**, avec comme paramètres nos deux variables **route** et **params**, la fonction va les assembler et construire l'url que nous souhaitions

La requête API est ensuite executée sur **url** contenant notre url fraîchement crée, et utilise la promesse .then afin d'envoyer cette donnée dans notre tableau vide **this.top**
