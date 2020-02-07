# Second Part

1) Dans cette partie vous devrez faire une navigation en ```view to view``` en utilisant ```stacknavigator```.

   Premièrement vous devez installer un package :

   ```
   npm install @react-navigation/native
   npm install --save react-navigation-stack
   expo install react-native-gesture-handler react-native-reanimated react-native-screens react-native-safe-area-context @react-native-community/masked-view
   ```
   
   Ensuite créez un fichier nommé ```js/navigation/Navigations.js```

   Dans ce fichier vous devrez ajouter un import pour utiliser le navigateur.
    
   ```
   import { createAppContainer } from 'react-navigation';
   import { createStackNavigator} from 'react-navigation-stack';
   ```
   
   Et importer le chemin du fichier que vous allez utiliser comme vue.
    
   ```
   import MainPage from '../MainPage'
   ```
      
   Créez la fonction de navigation comme ceux-ci:

   ```
   const AppStackNavigator = createStackNavigator({
      MainPage: {
        screen: MainPage,
      },
   },{
      mode: Platform.OS === 'ios' ? 'modal' : 'card',
      headerMode: 'none',
   })
   ```
  
   Exportez le :
 
   ```
   export default createAppContainer(AppStackNavigator);
   ```
    
   Et enfin allez dans votre ```App.js```, ajoutez un import :
   
   ```
   import Navigations from './js/navigation/Navigations'
   ```
   
   Et changez ```<MainPage/>``` par ```<Navigations/>```
    
   Félicitation vous l'avez fait ! 
 
   Maintenant vous devez ajouter deux autres vues dans votre navigation. 
 
   Vous avez tous les éléments necessaire depuis le début du WorkShop pour vous aider à la faire.

   Que la force soit avec vous 
