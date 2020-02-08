1) Dans cette partie du workshop nous alons voir comment utiliser des Api dans notre aplication React Native.

   Pour ce faire nous alons utiliser la méthode ```Fetch```
   
   Tous ce passera dans votre fichier ```MainPage.js```
  
   On oublie pas les include, Je vous connais.
   
   ```
   import { StyleSheet, Text, View, FlatList, ActivityIndicator } from 'react-native';
   ```
   
   <p align="center">
      <img width="45%" height="45%" src="/img/bye.gif">
   </p>
   
   On a deux petit nouveaux ```Flatlist``` et ```ActivityIndicator``` pas d'inquétude je vais vous expliquer tout ça.
   
   On ajoute aussi :
   
   ```
   import React, { Component } from 'react';
   import { render } from 'react-dom';
   import Constants from 'expo-constants';
   ```
   
2) Dans notre ```class``` nous allons ensuite créer votre premier constructeur
  
   ```
   constructor() {
      super();
      this.state = {
         isLoding: true,
         dataSource: []
      }
   }
   ```
  
   C'est dans celui-ci que nous créons nos variables.

   Bien nous pouvons passer à ce qui nous intérrese l'appelle de l'API.
  
   Nous allons utiliser une Api regroupant des noms de Pokemon, voici le lien : ```https://pokeapi.co/api/v2/pokemon/```

   Voici donc la fonction qui va nous permettre d'apeller notre api :
  
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
  
   Avec ```fetch``` nous faisons appelle à notre Api via le ```then((response))``` qui nous permet d'indiquer comment nous voulons 
   récupérer les informations ici sous forme de .json. 
  
   Le ```console.log``` est optionel mais je vous conseille de le laisser.
  
   Il va vous permettre de savoir si vous recevez bien les bonnes infos. 
  
   Nous modifions pour finir les variables que nous avons crée dans notre constructeur ```isloding``` qui passe à ```false``` comme nous avons bien récupéré nos données et ```dataSource``` qui nous permet de stocker nos infos.

3) Il est temps d'afficher nos infos vous pensez pas ?!

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
    
   Ici nous avont créé un ```if/else``` qui nous permet de savoir si notre code à bien chargé les éléments de notre appel Api
   pour comencer si le code rentre dans le ```IF``` ça nous donnera cela :
   
   [image loading]
   
   L'indicateur de chargement est possible via le components ```ActivityIndicator```
   
   Pour le ```else``` si vous avez bien fait votre taff, il vous affiche normalement ceux-ci :
   
   [image api]
   
   Le plus important ici et le ```Flatlist``` qui nous permet de lister nos données, nous donnons ensuite à ```data``` le chemin du dossier results, l'endroit où nous allons trouver les noms de nos Pokémons.
   
   La ligne suivante nous permet de dire à notre programme d'afficher seulement les noms de nos Pokémons.
   
4) Un peu de ```style```

   Pour en finir avec notre page nous allons faire un peu de ```style``` vous avez déjà des balises ```style``` dans ce code ex :
   
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
   
   Non sérieusement, c'est très moche, c'est pour ça que ça va être à vous de vous amuser avec le ```style```.
   
   Faites en sorte de rendre de faire un style qui vous plaira.
   
   Si vous voulez vous entrainer avec d'autres API, en voila déjà une : https://github.com/sin0light/api-kaamelott
