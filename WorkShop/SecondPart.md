# Second Part

1) Dans cette partie vous devrez faire une navigation en ```view to view``` en utilisant ```stacknavigator```.

   Premièrement vous devez installer un package :

   ```
   npm install --save react-navigation
   ```
   
   Ensuite créez un fichier nommé ```js/navigation/Navigations.js```

   Dans ce fichier vous devrez ajouter un import pour utiliser le navigateur.
    
   ```
   import { createBottomTabNavigator } from 'react-navigation-tabs'
   ```
   
   Et importer le chemin du fichier que vous allez utiliser comme vue.
    
   ```
   import App from "./App.js
   import MainPage from './js/MainsPage.js'
   ```
      
   Créez la fonction de navigation comme ceux-ci:

   ```
   const Tabs = createBottomTabNavigator ({
      App: {
         screen: app,
         tabBarOptions: {
            showIcon: false
         }
      }
   })
   ```
   
 5) Maintenant vous devrez l'exporter
 
    ```
    export default createAppContainer(Tabs);
    ```
    
 Felicitation vous l'avais fait ! 
 
 Maintenant vous devez ajouter deux autres vues dans votre navigation. 
 
 Vous avez tous les elements necessaire depuis les débuts du WorkShop pour vous aider à la faire.

 Que la force soit avec vous 
