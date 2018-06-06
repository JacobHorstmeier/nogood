React Draggable lets you drag and drop items anywhere
you can throw an axis on it to lock it to a certain axis
items that are rendered lower than other elements will always render on top of other elements
you can set a grid to say exactly how many pixels to move each "move"
can set bounds to never go outside of the parent div




import React, { Component } from 'react';
import Draggable from 'react-draggable'
import './App.css';


class ReactDraggable extends Component {
  constructor() {
    super()


  }
  render() {
    return (
      <div className="App">
        <Draggable
          // axis='y'
          // grid={[50, 50]}
          // bounds={{left: 200, right: 200}}
        >
          <div className='yellowDiv'>Yellow</div>
        </Draggable>
        <div className='greenParent'>
          <Draggable bounds='parent'>
            <div className='orangeDiv'></div>
          </Draggable>
        </div>
      </div>
    );
  }
}

export default ReactDraggable