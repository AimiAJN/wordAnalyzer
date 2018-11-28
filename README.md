//Done by Aimi (1529554)
import React, {Component} from 'react';
import {StyleSheet, Text, View, TextInput, Button} from 'react-native';

export default class App extends Component {

constructor(){
  super();
  this.state={
    word:'',
    array: [],
    countCons:0,
    countVow:0,
    countChar:0,
  };
}

analyzeWord() {

  this.setState({array:this.state.word.split("")}, () => {
  this.setState({countChar: this.state.array.length})

    for(var x=0; x<this.state.array.length; x++){
      const letter = this.state.array[x];
      letter.toLowerCase();
      if(letter=='a' || letter=='e' || letter=='i' || letter=='o' || letter=='u'){
        this.setState({countVow: this.state.countVow+=1})
      }
      else{
        this.setState({countCons: this.state.countCons+=1})
      }
    }
  });
}
