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
    
2) Learn how to use UI components for React Native.

   We will use here ```NativeBase.io```
   
   Go to https://docs.nativebase.io/docs/GetStarted.html and install NativeBase
   
   ``` npm install native-base --save```
   
   ``` expo install expo-font ```
   
   In app.js remove all the code and add this:
   
   ```
   import React from 'react';
   import { AppLoading } from 'expo';
   import { Container, Text } from 'native-base';
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
           <Text>Open up App.js to start working on your app!</Text>
         </Container>
      );
     }
   }
   ```
   
   This part load all we need to load native base:
   
   ```
    async componentDidMount() {
      await Font.loadAsync({
         Roboto: require('native-base/Fonts/Roboto.ttf'),
         Roboto_medium: require('native-base/Fonts/Roboto_medium.ttf'),
         ...Ionicons.font,
       });
       this.setState({ isReady: true });
    }
   ```
   And this part pause the app until all the font was load:
   
   ```
   if (!this.state.isReady) {
      return <AppLoading />;
   }
   ```
   
