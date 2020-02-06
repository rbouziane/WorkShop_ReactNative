# Second Part
    dans cette partie vous devais faire une navigation en "vue a vue" en utilisant "stacknavigator"
    premierement vous devais installer le paker en utilisant la comande "npm" (asurer vous que votre serveur soit etain)
1) premierement vous devais installer le paker en utilisant la comande "npm" (asurer vous que votre serveur soit etain)
```
   npm install --save react-navigation
```
2) mintenan crée un fichier nomée "componenet/navigation.js"

3) dans ce fichier vous devais ajouter
    1) l'import pour utiliser le navigateur 
      ```
      import { createBottomTabNavigator } from 'react-navigation-tabs'
      ```
    2) et le chemin du fichier que vous aller utiliser comme vue
      ```
      import app from './componenet/app.js'
      ```
4) Crea la "fonction" de navigation comme suite

   ```
   const Tabs = createBottomTabNavigator ({
    App: {screen: app},
   }, {
      tabBarOptions: {
          showIcon: false
      }
   })
   ```
 5) Mintenan vous devais L'exporter
    ```
    export default createAppContainer(Tabs);
    ```
Felicitation vous l'avais fait ! mintenant vous devais ajoutée deux autre vue dans votre navigation, vous avais tous les element dans cette exemple pour vous aider a le faire.
```
que la force soit avec vous 
```
