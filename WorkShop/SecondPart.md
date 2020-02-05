# Second Part
    In this part you are going to make a navigation "vue to vue" using "stacknavigator"
1) First of all you must install the packadge using "npm" (make sur your serveur is not runing)
```
   npm install --save react-navigation
```
2) now create a new file name "componenet/navigation.js"

3) in this fille you muste include tow thing
    1) the navigator 
      ```
      import { createBottomTabNavigator } from 'react-navigation-tabs'
      ```
    2) and the file you whant to use as a vue 
      ```
      import app from './componenet/app.js'
      ```
4) Create the "createBottomTabNavigator" like so...

   ```
   const Tabs = createBottomTabNavigator ({
    App: {screen: app},
   }, {
      tabBarOptions: {
          showIcon: false
      }
   })
   ```
 5) Now you need to export the "createBottomTabNavigator"
    ```
    export default createAppContainer(Tabs);
    ```
That's it yout did it ! but it's not hover yet now your need to add tow more vue in your navigation (vue1 and vue2)
you have all the element in this step be step exempel to do it. May the force be with you.
