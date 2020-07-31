# React Native Multiple Select Modal Picker

Some of these libraries were used in this, kindly install these first. 

## Installation 

### 1) For installing [react-native-multiple-select](https://github.com/toystars/react-native-multiple-select)

`$ npm install react-native-multiple-select --save`

or use yarn

`$ yarn add react-native-multiple-select --save`

### 2) For installing react-native-vector-icons

`$ npm install react-native-vector-icons --save` 

and then

`$ react-native link react-native-vector-icons`

for linking to your current project.

## Usage

Either you can clone this repository, or you can copy directly the code from here. But be ensure to add and comfigure those NPM's packages.

import React from 'react';
import {
  SafeAreaView,
  StyleSheet,
  ScrollView,
  View,
  Text,
  StatusBar,
  TouchableOpacity,
  Modal
} from 'react-native';

import MultiSelect from 'react-native-multiple-select';

import Icon from 'react-native-vector-icons/FontAwesome';

class App extends React.Component {

  constructor(props) {
    super(props);
  this.state = {
    citySelected : [],
    CityisShownPicker : false,
  }
}

handleChange_City = (City) => {
  this.setState({ citySelected : City });
}


  render() {

    citiesarr = [{
      id: '0',
      name: 'New Delhi',
    }, {
      id: '1',
      name: 'Agra',
    }, {
      id: '2',
      name: 'Hyderabad',
    }, {
      id: '3',
      name: 'Mumbai',
    }, {
      id: '4',
      name: 'Chennai',
    }, {
      id: '5',
      name: 'Kanpur',
    }, {
      id: '6',
      name: 'Prayagraj',
    }, {
      id: '7',
      name: 'Goa',
    }, {
      id: '8',
      name: 'Pune',
    }];


    return (
      <SafeAreaView>
        <ScrollView>
            <View>

            <View style = {{ marginLeft : 0, marginTop : 10 }}>
              <TouchableOpacity
                    onPress={() => {
                        this.setState({ CityisShownPicker: !this.state.CityisShownPicker })
                    }}
                    style={{ height: 35, alignSelf : "center", borderWidth : 1.5, borderColor : "#800000", borderRadius : 10, flex : 1, flexDirection : "row", marginRight : 20 }}
                  >
                    <Text style = {{ paddingLeft : 10, paddingTop : 2, flex : 0.97}}>Select City</Text>
                    <Icon style = {{color : "#800000", paddingTop : 2, marginRight : 5}} size = {28} name={'arrow-circle-down'} />
                  </TouchableOpacity>
                  {this.state.CityisShownPicker ? 
                <View>
                <Modal
                animationType="slide"
                transparent={false}
                visible={this.state.CityisShownPicker}
                onRequestClose={() => {
                  this.setState({ CityisShownPicker: !this.state.CityisShownPicker });
                }}
                >
                <View style = {{ backgroundColor : "white", height : 40}}>
                  <TouchableOpacity onPress = {() => {
                  this.setState({ CityisShownPicker: !this.state.CityisShownPicker })
                }}>
                    <Icon style = {{color : "#800000", paddingTop : 2, alignSelf : "flex-end", marginRight : 10}} size = {28} name={'times-circle'} />
                  </TouchableOpacity>
                </View>
                <ScrollView style = {{ marginTop : 0}}>
                  <View style = {{ borderWidth : 0.5, borderColor : "#800000", borderRadius : 10, marginLeft : 5, marginRight : 5 }}>
              <MultiSelect
                styleMainWrapper = {{ marginLeft : 10, marginRight : 5, marginTop : 10 }}
                styleInputGroup = {{ borderWidth : 1.5, borderColor : "#800000", borderRadius : 10}}
                hideTags
                items={citiesarr}
                uniqueKey="id"
                ref={(component) => { this.multiSelect = component }}
                onSelectedItemsChange={this.handleChange_City}
                selectedItems={this.state.citySelected}
                selectText="Pick Items"
                searchInputPlaceholderText="Search Items..."
                //onChangeInput={ (text)=> console.log(text)}
                altFontFamily="ProximaNova-Light"
                tagRemoveIconColor="#CCC"
                tagBorderColor="#CCC"
                tagTextColor="#CCC"
                selectedItemTextColor="red"
                selectedItemIconColor="red"
                itemTextColor="#000"
                displayKey="name"
                searchInputStyle={{ color: 'black', marginLeft : 5 }}
                submitButtonColor="#CCC"
                submitButtonText="Submit"
              /></View>
              </ScrollView></Modal></View>
                         : null
                      }
                      </View>

            </View>
        </ScrollView>
      </SafeAreaView>
  )
  }
};

export default App ;


## Screenshots

![Alt Text](/1.png)    ![Alt Text](/2.png)   ![Alt Text](/3.png)  ![Alt Text](/4.png)
