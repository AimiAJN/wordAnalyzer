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

//Done by Khairun Nuwwarah (1520982)
render() {
    return (
      <View style={styles.container}>
        <Text>WORD ANALYZER</Text>
        <Text></Text>
        <TextInput onChangeText={(word)=>this.setState({word})} placeholder="Insert Word"/> 
        <Button onPress={() => this.analyzeWord()} title="Analyze"></Button>      
        <Text>Word : {this.state.word}</Text>
        <Text>No of Consonants : {this.state.countCons}</Text>
        <Text>No of Vowels : {this.state.countVow}</Text>
        <Text>No of Characters : {this.state.countChar}</Text>
        {/* <Text>{this.state.array.length}</Text> */}
    </View>
    );
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    backgroundColor: '#F5FCFF',
  },
  welcome: {
    fontSize: 20,
    textAlign: 'center',
    margin: 10,
  },
  instructions: {
    textAlign: 'center',
    color: '#333333',
    marginBottom: 5,
  },
});
