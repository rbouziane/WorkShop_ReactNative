# First Part

---
<p align="center">
   <img width="50%" height="50%" src="/img/hello-there.gif">
</p>

Alors bien ou quoi ?

Prêt à faire vos premiers pas en React Native ?

1) On va d'abord faire l'une des choses les plus importantes en React Native, apprendre à changer l'écran de démarrage et l'icon    d'application

   Bon je sais c'est pas ouf :sweat_smile: mais c'est l'une des première chose à faire quand on commence une application.
   
   Aller dans le fichier ```app.json```, c'est la partie qui nous intéresse:
   
   ```
   "icon": "./assets/icon.png",
    "splash": {
      "image": "./assets/splash.png",
      "resizeMode": "contain",
      "backgroundColor": "#ffffff"
    }
    ```
    
    Changez le chemin de "icon" avec l'image que vous voulez. 
    
    Comme vous pouvez le voir, dans expo l'icône de l'application à changé.
    
    Faites la même chose avec le chemin de "splash:image" et changez la couleur de "backgroundColor": "#ffffff".
    
    Vous pouvez mettre ```#000000``` si vous n'avez pas d'idées.
    
    Maintenant relancez l'application et regardez le resultat.
    
    Magnifique non ?
    
<p align="center">
   <img width="45%" height="45%" src="/img/the-office-no.gif">
</p>
    
2) On va maintenant apprendre à installer des UI components pour React Native.

   On va utiliser ici ```NativeBase.io```
   
   Allez sur https://docs.nativebase.io/docs/GetStarted.html et installez NativeBase
   
   ``` npm install native-base --save```
   
   ``` expo install expo-font ```
   
   NativeBase est maintenant installez.
   
   Il faut maintenant verifiez que ça fonctionne.
   
   Dans ```app.js``` retirez tous le code et ajoutez celui-ci:
   
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
   
   Normalement l'application devrait ressemblez à ça:

<p align="center">
   <img width="35%" height="35%" src="/img/app_first_launch.png">
</p>
   
3) Utilisons maintenant NativeBase
   
   Voila la doc: https://docs.nativebase.io/ 
   
   On utilisera ici le component ```<Button>```
   
   D'abord ajoutez ```Button``` à ```import { Container, Text, View } from 'native-base';```
   
   On peux maintenant utiliser ce components.
   
   Remplacez ce code:
   
   ```
   <Container>
      <View style={{flex: 1, alignItems: 'center', justifyContent: 'center'}}>
         <Text>Open up App.js to start working on your app!</Text>
      <View/>
   </Container>
   ```
   
   Par ça:
   
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
   
   Vous devriez avoir quelque chose comme ça:
   
   <p align="center">
      <img width="30%" height="30%" src="/img/button_page.png">
   </p>

   Mais je sais ce que vous vous dites.

   <p align="center">
      <img width="30%" height="30%" src="/img/kevin-hart.gif">
   </p>
   
   Oui c'est moche et mal aligné surtout si vous avez une encoche.
  
4) Learn how to change the app style.
   
   One of the most important thing with React Native is to know how to use the style.
  
   We will here learn how flexbox work.
   
   To put you on the right way add this:
   
   ```
   <View style={{flex: 1, alignItems: 'center', justifyContent: 'space-around'}}>
   ...
   ...
   </View>
   ```
   Into all the buttons components.
   
   You should the something like that:
 
<p align="center">
   <img width="30%" height="30%" src="/img/task-4-1.jpg">
</p>
   
   Now use this docs to know more about flexbox: https://facebook.github.io/react-native/docs/flexbox

   And try to obtain something like that:

<p align="center">
   <img width="30%" height="30%" src="/img/task-4-2.jpg">
</p>

   You know now of flexbox work.
