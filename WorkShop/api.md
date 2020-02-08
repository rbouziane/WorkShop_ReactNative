1) Dans cette partie du workshop nous alont voir comment utiliser des Api dans notre aplication React Native pour ce faire nous alont
   utiliser la méthode "Fetch"
   comancer pas crée un nouveau fichier
   ```
   js/api.js
   ```
   On oublie pas les include, Je vous connais.
   ```
   import { StyleSheet, Text, View, FlatList, ActivityIndicator } from 'react-native';
   ```
   [gif] ???
   On a deux petit nouveaux "Flatlist" et "ActivityIndicator" pas d'inquetude je vais vous expliqué tout ca
   
   on oublie pas les copain 
   ```
   import React, { Component } from 'react';
   import { render } from 'react-dom';
   import Constants from 'expo-constants';
   ```
   
2) Creation de notre page
   bien mitenanant que nos hédeur sont en place nous alont crée un nouvelle class
   ```
    export default class App extends Component{
    
    }
   ```
   dans cette class alont ansuite crée votre premier constructeur
  ```
    constructor() {
      super();
      this.state = {
      isLoding: true,
      dataSource: []
    }
  }
  ```
  Tous constructeur démare pas "super()", et se trouve dans votre "class App".
  N'oublier pas de faire des test régulier pour voir si vous n'avais pas fais d'ereur
  Bien nous pouvont passer a se qui nous interese l'appelle de l'API.
  nous allont utiliser une Api regroupant des nom de Pokemon voici le lien 
  ```
  https://pokeapi.co/api/v2/pokemon/
  ```
  voisi donc la fonction qui va nous permetre d'apellet notre api
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
  Avec "fetch" nous feson apelle a notre Api via le then((response)) nous permet de lui indique comment nous voulont 
  recupere les informations ici sous forme de .json, le "console.log" est optionelle mais je vous conseille de le leser 
  il vas vous permetre de savoir si vous recever bien les bonne infos. nous modifion pour finir les variable que nous avont                       crée dans notre constructeur "isloding" qui passe a false vue que nous avont bien récupere nos données et "dataSource" qui nous   permet de stocker nos infos.

3) Il est temps d'afficher nos infos vous pensais pas ?!
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
   ici nous avont crée un if/else qui nous permet de savoir si notre code a bien charger les element de notre apelle Api
   pour comancer si le code rentre dans le "IF" cella nous donner cella 
   [image loading]
   l'indicateur de chargement et possible viea "ActivityIndicator".
   
   Le code rantre dans le "else" si vous avez bien fait votre taff, il vous afiche normalement cesi
   [image api]
   
   le plus important ici et le "Flatlist" qui nous permet de lister nos donner, nous demandon esuite a date d'aller dans le dossier results ou nous alont trouver les nom de nos Pokemon, la ligne suivante nous permet de dire a notre programe d'afficher selement les noms de nos Pokemon
4) Un peut de "style"
   pour en finir avec notre page nous alont faire une peut de "style" vous avais deja des balise "style" dans ce code ex:
   ```
   <View style={styles.container}>
   ```
   cela vas rendre notre code un peut plus "jolie"
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
   N'esiter pas a faire des tests et a vous amusser avec le "style"
   
 

   
