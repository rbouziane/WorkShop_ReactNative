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
   
