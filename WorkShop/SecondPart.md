# Second Part

Dans cette partie vous devrez faire une navigation en "view to view" en utilisant "stacknavigator".

1) Premièrement vous devez installer un package en utilisant la commande "npm".

   ```
   npm install --save react-navigation
   ```
   
2) Maintenant crée un fichier nommé "component/navigation.js".

3) Dans ce fichier vous devrez ajouter
    1) L'importer pour utiliser le navigateur.
    
       ```
       import { createBottomTabNavigator } from 'react-navigation-tabs'
       ```
      
    2) Et importer le chemin du fichier que vous aller utiliser comme vue.
    
       ```
       import app from './component/app.js'
       ```
      
4) Crée la "fonction" de navigation comme ici:

   ```
   const Tabs = createBottomTabNavigator ({
    App: {screen: app},
   }, {
      tabBarOptions: {
          showIcon: false
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
