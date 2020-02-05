# First Part

---

1) Learn how to change splash screen and icon app.

   Go to ```app.json```, that the part which interests us:
   
   ```
   "icon": "./assets/icon.png",
    "splash": {
      "image": "./assets/splash.png",
      "resizeMode": "contain",
      "backgroundColor": "#ffffff"
    }
    ```
    
    Change the "icon" path with the icon image that you want. You can see that in expo your icon app change.
    
    Do the same thing with the "splash:image" path and change the "splash:backgroundColor" with ```#000000```
    
    Now relaunch the application and see the result.
    
2) Learn how to install UI components for React Native.

   We will use here ```NativeBase.io```
   
   Go to https://docs.nativebase.io/docs/GetStarted.html and install NativeBase
   
   ``` npm install native-base --save```
   
   ``` expo install expo-font ```
   
   In app.js remove all the code and add this:
   
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
   
   NativeBase is now install and now we can use it.
   
3) Learn how to use NativeBase for React Native.
   
   We will use for exemple the Button components from NativeBase.
   
   First Add ```Button``` to ```import { Container, Text, View } from 'native-base';```
   
   You can now use these components.
   
   Now replace this:
   
   ```
   <Container>
      <View style={{flex: 1, alignItems: 'center', justifyContent: 'center'}}>
         <Text>Open up App.js to start working on your app!</Text>
      <View/>
   </Container>
   ```
   
   By this:
   
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
      <img width="30%" height="30%" src="/img/task-4-1.png">
   </p>
   
   https://facebook.github.io/react-native/docs/flexbox
   
   ```
   
   ```
   
   ex:
   ```<View style={{flex: 1, alignItems: 'center', justifyContent: 'space-around'}}>```
   
   
   
