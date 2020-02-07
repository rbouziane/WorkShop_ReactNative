# First Part

---
<p align="center">
   <img width="50%" height="50%" src="/img/hello-there.gif">
</p>

Alors bien ou quoi ?

Prêts à faire vos premiers pas en ```React Native``` ?

1) On va d'abord faire l'une des choses les plus importantes en ```React Native```, apprendre à changer l'écran de démarrage et l'icône    d'application.

   Bon, alors je sais que c'est pas ouf :sweat_smile: mais c'est l'une des premières choses à faire quand on commence une application.
   
   Allez dans le fichier ```app.json```, c'est la partie qui nous intéresse :
   
   ```
   "icon": "./assets/icon.png",
    "splash": {
      "image": "./assets/splash.png",
      "resizeMode": "contain",
      "backgroundColor": "#ffffff"
    }
    ```
    
    Changez le chemin de ```"icon"``` avec l'image que vous voulez. 
    
    Comme vous pouvez le voir, dans expo, l'icône de l'application a changé.
    
    Faites la même chose avec le chemin de ```"splash:image"``` et changez la couleur de ```"backgroundColor": "#ffffff"```
    
    Vous pouvez mettre ```#000000``` si vous n'avez pas d'idées.
    
    Maintenant : relancez l'application et regardez le résultat.
    
    Magnifique non ?
    
<p align="center">
   <img width="45%" height="45%" src="/img/the-office-no.gif">
</p>
    
2) On va maintenant apprendre à installer des ```UI components``` pour ```React Native```

   On va utiliser ici ```NativeBase.io```
   
   Allez sur https://docs.nativebase.io/docs/GetStarted.html et installez NativeBase
   
   ``` npm install native-base --save```
   
   ``` expo install expo-font ```
   
   ```NativeBase``` est maintenant installé.
   
   Et il faut vérifier que ça fonctionne.
   
   Dans ```app.js``` retirez tout le code et ajoutez celui-ci :
   
   ```
   import React from 'react';
   import { AppLoading } from 'expo';
   import { Container, Text, View } from 'native-base';
   import * as Font from 'expo-font';
   import { Ionicons } from '@expo/vector-icons';
   
   export default class App extends React.Component {
      constructor(props) {
          super(props);
          this.state = {
              isReady: false,
          };
      }
   
      async componentDidMount() {
         await Font.loadAsync({
            Roboto: require('native-base/Fonts/Roboto.ttf'),
            Roboto_medium: require('native-base/Fonts/Roboto_medium.ttf'),
            ...Ionicons.font,
         });
         this.setState({ isReady: true });
      }
   
      render() {
         if (!this.state.isReady) {
            return <AppLoading />;
         }
   
         return (
            <Container>
              <View style={{flex: 1, alignItems: 'center', justifyContent: 'center'}}>
                <Text>Open up App.js to start working on your app!</Text>
              <View/>
            </Container>
         );
      }
   }
   ```
   
   Normalement l'application devrait ressembler à ça :

<p align="center">
   <img width="35%" height="35%" src="/img/app_first_launch.png">
</p>

3) Avant d'utilisez ```Nativebase``` nous devons faire en sortes de bien hiérarchiser notre application.

   Ça nous permettra de faciliter la navigation de "vue en vue" que nous verons dans la partie 2.
   
   Pour commencez crée un dossier à la racine que vous appelerez ```js```
   
   Dans ce dossier crée un fichier que vous nommerez ```MainPage.js```
   
   Dans ce fichier copier collé le code du fichier ```App.js```
   
   Retirez toute fois :
   
   ```
   constructor(props) {
      super(props);
      this.state = {
         isReady: false,
      };
   }
   
   async componentDidMount() {
      await Font.loadAsync({
         Roboto: require('native-base/Fonts/Roboto.ttf'),
         Roboto_medium: require('native-base/Fonts/Roboto_medium.ttf'),
         ...Ionicons.font,
      });
      this.setState({ isReady: true });
   }
   ```
   
   et
   
   ```
   if (!this.state.isReady) {
      return <AppLoading />;
   }
   ```
   
   Ainsi que les imports dont nous n'avons plus besoin :
   
   ```
   import { AppLoading } from 'expo';
   import * as Font from 'expo-font';
   import { Ionicons } from '@expo/vector-icons';
   ```
   
   Pensez aussi à changez le nom de la class dans :
   
   ```
   export default class App extends React.Component {
   ``` 
   
   Passons au fichier ```App.js```
   
   Dans celui-ci retirez et ajoutez ces lignes :
   
   ```
   import { Container, Text, View } from 'native-base' #à retirez
   ```
   
   ```
   <Container>
      <View style={{flex: 1, alignItems: 'center', justifyContent: 'center'}}>      #à retirez
         <Text>Open up App.js to start working on your app!</Text>
      <View/>
   </Container>
   ```
   
   ```
   <MainPage/> #à ajoutez dans le return
   ```
   
   ```
   import MainPage from './js/MainPage' #à ajoutez
   ```
   
   Vous devriez avoir la même chose qu'à la fin du 2)
   
4) Utilisons maintenant ```NativeBase```
   
   Voilà la doc: https://docs.nativebase.io/ 
   
   On utilisera ici le component ```<Button>```
   
   Allez dans le fichier ```js/MainPage.js```
   
   D'abord : ajoutez ```Button``` à ```import { Container, Text, View } from 'native-base';```
   
   On peut maintenant utiliser ce component.
   
   Remplacez ce code :
   
   ```
   <Container>
      <View style={{flex: 1, alignItems: 'center', justifyContent: 'center'}}>
         <Text>Open up App.js to start working on your app!</Text>
      <View/>
   </Container>
   ```
   
   Par celui-ci :
   
   ```
   <Container>
      <Button rounded light>
         <Text>Light</Text>
      </Button>
      <Button rounded>
         <Text>Primary</Text>
      </Button>
      <Button rounded success>
         <Text>Success</Text>
      </Button>
      <Button rounded info>
         <Text>Info</Text>
      </Button>
      <Button rounded warning>
         <Text>Warning</Text>
      </Button>
      <Button rounded danger>
         <Text>Danger</Text>
      </Button>
      <Button rounded dark>
         <Text>Dark</Text>
      </Button>
   </Container>
   ```
   
   Vous devriez avoir quelque chose comme ça :
   
   <p align="center">
      <img width="30%" height="30%" src="/img/button_page.png">
   </p>

   Mais je sais ce que vous vous dites.

   <p align="center">
      <img width="30%" height="30%" src="/img/kevin-hart.gif">
   </p>
   
   Oui c'est moche et mal aligné surtout si vous avez une encoche.
  
5) C'est pour cela que maintenant nous devons gérer la ```flexbox``` de notre application.

   L'une des choses les plus importantes en ```React Native``` est une bonne utilisation et surtout une bonne compréhension de la ```flexbox```
  
   Il faut d'abord comprendre comment la ```flexbox``` fonctionne.
   
   Pour vous mettre sur le bon chemin, ajoutez ça dans votre code entre tous les components ```Button``` :
   
   ```
   <View style={{flex: 1, alignItems: 'center', justifyContent: 'space-around'}}>
   ...
   ...
   </View>
   ```
   
   Vous devriez avoir quelque chose comme ça :
 
   <p align="center">
      <img width="30%" height="30%" src="/img/task-4-1.jpg">
   </p>
   
   Maintenant utilisez ceux-ci pour en apprendre un peu plus : https://facebook.github.io/react-native/docs/flexbox
   
   Et vous allez vous débrouillez par vous-même à cet endroit :grin:
   
   Ben oui, on ne va pas vous donner tout le code.

   Et essayez d'obtenir quelque chose comme ça :

   <p align="center">
      <img width="30%" height="30%" src="/img/task-4-2.jpg">
   </p>

   Si vous avez réussi à reproduire cet écran, c'est que vous avez compris comment la ```flexbox``` fonctionne.
   
   <p align="center">
      <img width="40%" height="40%" src="/img/dicaprio.gif">
   </p>
   
6) Utilisons maintenant le ```style``` en ```React Native```
   
   Celui-ci va nous permettre de changez la couleurs, la taille, l'opacity ... . De nos components.
      
   Pour cela il y a plusieurs manières :
      
   L'écrire directement dans nos components comme ceux-ci :
      
   ```
   <Text style={{fontSize: 19, fontWeight: 'bold}}>J'écris du text</Text>
   ```
      
   Ou en créent des const :
   ```
   const styles = StyleSheet.create({
      stylesText: {
         fontSize: 19,                 #placez votre const à la toute fin de votre fichier ou bien crée au fichier style contenant tous vos style que vous importerez par la suite
         fontWeight: 'bold
      },
   })
   <Text style={styles.stylesText}>J'écris du text</Text>
   ```
      
   Utilisez la deuxième méthode lorsque que vous avez plusieurs components necéssitant le même ```style```
      
7) À votre tour, utilisez ```NativeBase```, ```flexbox```, et le ```style``` pour réalisez 3 ```<Button>```
   
   Cela nous préparera pour la Navigation que sera en partie 2.
   
   Sur les 7 ```<Button>``` que contient votre écran supprimez en 4.
      
   Faites en sortes que les 3 boutons soit alignés au centre de l'écran.
      
   Changez les nom de vos boutons pour avoir ```Page Principale```, ```Page 2``` et ```Page 3```
      
   Faites en sorte que le bouton ```Page Principale``` soit 2x plus grand que les autres.
      
   Ils ne doivent pas avoir la même couleurs et vous devez également changez la couleurs de leurs textes, pour qu'ils en ait des différentes.
      
   Changez également la couleur d'arrière plan, vous pouvez prendre cette couleur ```#313130```
      
   Vous pouvez ajoutez d'autres ```style``` à vos boutons si vous en avez envie.
      
   <p align="center">
      <img width="40%" height="40%" src="/img/tien-tien-tien.gif">
   </p>
      
   Et oui, c'est la fin de la première partie.
      
   Vous savez maintenant comment :
   
      -changer l'écran de démarrage et l'icône d'application.
      
      -installer et utiliser des UI components, précisément ici ```NativeBase```
      
      -hiérarchiser notre application et crée de nouveau fichier ```React Native```
      
      -utilisez la ```flexbox``` ainsi que le ```style``` en ```React Native```   
