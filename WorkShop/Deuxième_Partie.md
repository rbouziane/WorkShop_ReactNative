# Deuxième Partie

---

1) Dans cette partie, vous devrez faire une navigation en ```view to view``` en utilisant ```stacknavigator```.

   Premièrement, vous devez installer un package :

   ```
   npm install @react-navigation/native
   npm install --save react-navigation-stack
   expo install react-native-gesture-handler react-native-reanimated react-native-screens react-native-safe-area-context @react-native-community/masked-view
   ```
   
   Ensuite, créer un fichier nommé ```js/navigation/Navigations.js```

   Dans ce fichier, vous devrez ajouter un import pour utiliser le navigateur.
    
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
  
   Exportez-le :
 
   ```
   export default createAppContainer(AppStackNavigator);
   ```
    
   Et enfin allez dans votre ```App.js```, ajoutez un import :
   
   ```
   import Navigations from './js/navigation/Navigations'
   ```
   
   Et changez ```<MainPage/>``` par ```<Navigations/>```
    
   Félicitations : vous l'avez fait !
   
   <p align="center">
      <img width="50%" height="50%" src="/img/yvan-govain.gif">
   </p>
 
   Maintenant vous devez ajouter deux autres vues dans votre navigation.
   
   Remettez sur chaque page les 3 boutons, ```Page Principale```, ```Page 2``` et ```Page 3```
      
   Faites en sorte que le bouton correspondant à la page où vous vous trouvez soit 2x plus grand que les autres.
   
   Pour changer d'écran lorsque l'on clique sur un ```<Button>``` on ajoute :
   
   ```
   <Button onPress={() => this.props.navigation.navigate("MainPage")}>
   ```
      
   Vous avez tous les éléments nécessaires depuis le début du WorkShop pour vous aider à faire la navigation.

   Que la force soit avec vous.
   
   <p align="center">
      <img width="50%" height="50%" src="/img/léodagan.gif">
   </p>
   
2) Dans cette partie du workshop, nous allons voir comment utiliser des Api dans notre application React Native.

   Pour ce faire nous allons utiliser la méthode ```Fetch```
   
   Tout se passera dans votre fichier ```MainPage.js```
  
   On n'oublie pas les include, je vous connais.
   
   ```
   import { StyleSheet, Text, View, FlatList, ActivityIndicator } from 'react-native';
   ```
   
   <p align="center">
      <img width="45%" height="45%" src="/img/bye.gif">
   </p>
   
   On a deux petits nouveaux ```Flatlist``` et ```ActivityIndicator``` pas d'inquétude : je vais vous expliquer tout ça.
   
   On ajoute aussi :
   
   ```
   import React, { Component } from 'react';
   import { render } from 'react-dom';
   import Constants from 'expo-constants';
   ```
   
3) Dans notre ```class``` nous allons ensuite créer votre premier ```constructor```
  
   ```
   constructor() {
      super();
      this.state = {
         isLoding: true,
         dataSource: []
      }
   }
   ```
  
   C'est dans celui-ci que nous allons créer nos variables.

   Bien, nous pouvons passer à ce qui nous intéresse l'appel de l'API.
  
   Nous allons utiliser une Api regroupant des noms de Pokémons, voilà le lien : ```https://pokeapi.co/api/v2/pokemon/```

   Voici donc la fonction qui va nous permettre d'appeler notre api :
  
   ```
   componentDidMount () {
       fetch('https://pokeapi.co/api/v2/pokemon/').then((response) => response.json())
      .then((responseJson) => {
         console.log(responseJson),
         this.setState({
            isLoding: false,
            dataSource: responseJson
         })
      })
   }
   ```
  
   Avec ```fetch``` nous faisons appel à notre Api via le ```then((response))``` qui nous permet d'indiquer comment nous voulons 
   récupérer les informations ici sous forme de .json. 
  
   Le ```console.log``` est optionnel mais je vous conseille de le laisser.
  
   Il va vous permettre de savoir si vous recevez bien les bonnes infos. 
  
   Nous modifions pour finir les variables que nous avons créées dans notre ```constructor``` ```isloding``` qui passe à ```false``` comme nous avons bien récupéré nos données et ```dataSource``` qui nous permet de stocker nos infos.

4) Il est temps d'afficher nos infos, vous ne pensez pas ?!

   ```
   render () {
      if (this.state.isLoding) {
         return (
            <View style={styles.container}>
                <Text> loading</Text>
                <ActivityIndicator size="large" animating />
           </View>
          )
      } else {
        return (
         <View style={styles.container}>
            <Text> Api </Text>
            <FlatList
                  data={this.state.dataSource.results}
                  renderItem={({item}) => <Text>{item.name}</Text>}>
            </FlatList>
         </View>
            );
         }
      }
    ```
    
   Ici nous avons créé un ```if/else``` qui nous permet de savoir si notre code a bien chargé les éléments de notre appel Api
   pour commencer si le code rentre dans le ```if``` ça nous donnera cela :
   
   <p align="center">
      <img width="50%" height="50%" src="/img/loading.png>
   </p>
   
   L'indicateur de chargement est possible via le component ```ActivityIndicator```
   
   Pour le ```else``` si vous avez bien fait votre taff, il vous affiche normalement ceci :
   
   <p align="center">
      <img width="50%" height="50%" src="/img/api.png>
   </p>
   
   Le plus important ici est le ```Flatlist``` qui nous permet de lister nos données, nous donnons ensuite à ```data``` le chemin du dossier ```results```, l'endroit où nous allons trouver les noms de nos Pokémons.
   
   La ligne suivante nous permet de dire à notre programme d'afficher seulement les noms de nos Pokémons.
   
5) Un peu de ```style```

   Pour en finir avec notre page, nous allons faire un peu de ```style```, vous avez déjà des balises ```style``` dans ce code ex :
   
   ```
   <View style={styles.container}>
   ```
   
   Cela va rendre notre code un peu plus "jolie"
   
   ```
   const styles = StyleSheet.create({
   container: {
    flex: 1,
    justifyContent:'space-around',
    marginTop: Constants.statusBarHeight,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
      },
   });
   ```
   
   <p align="center">
      <img width="45%" height="45%" src="/img/nick-young.gif">
   </p>
   
   Non sérieusement, c'est très laid, c'est pour cela que ça va être à vous de vous amuser avec le ```style```.
   
   Faites en sorte d'ajouter du ```style``` qui vous plaira.
   
   Si vous voulez vous entrainer avec d'autres API, essayez d'afficher des données avec celle-ci : https://github.com/sin0light/api-kaamelott
   
FIN
