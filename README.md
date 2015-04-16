# React Style Guide
A style guide for managing sane react components.

From using React for a month, here are my initial thoughts.

# React.js
## Components
  1. Don't get fancy with manipulating child DOM elements. Map over them and create child components instead.
    ```javascript
    render: function() {
    var people = this.props.people.map(function (person,position) {
      if (person){
        return (
          <Person
            person = {person}
            handleUpdate = {this.handleUpdate}
            style = {this.stageStyles(position)}
            key = {person.id}/>
        );
      }
    }, this);

    return (
      <ul>
        {people}
      </ul>
    )
    }
    ```
  2. Once you see duplicated functionality in your components, use a Mixin. DRY.
  3. Don't change state in a child component without letting the parent component know.
  4. Deeply nested components.. are really hard and can be confusing at times.
  5. Class methods, should do one thing. (Single Responsibility Principle)
  6. Learn about .bind(); because you're most likely going to be using a scoped ```this``` in a function inside of a function. 
    ```javascript
    
    render: function(){
      var editPositionState = function () {
        return this.props.stage.position === this.state.editPosition;  // this.props is undefined
      };
      var editPositionState = function () {
        return this.props.stage.position === this.state.editPosition;  // this.props works!
      }.bind(this);
      // or you can do it the lame way and grab this.props
      // before a function and assign it to a variable.
    }
    ```
  7. Make sure the ```render``` method is at the end of the file. And use multi-line if a component has more than two properties.
      ```javascript
      
      <Component
        propertyOne={...}
        propertyTwo={...}
        propertyThree={...}
        …
      />
      ```
  8. Use less state and more ```this.props``` in your render method.
  
## Comments
  1. Write a comment at the top of the file of who the parent is.
  
## Mixins
  1. Use more mixins.
  2. Can you use mixin for duplicated renders?
  3. I like to prefix mixin methods with ```_mxn_```, so in my components I write ```this._mxn_functionName``` and I know it's from a mixin.
  4. 
  
## CSS styles in your components
  I still think about this a lot but it's very nice and useful when you're creating dynamic css styles for your components.
  1. abstract your css into a class method. ``` cssStyles: function(){...} ```

## tools
  1. React dev console chrome extension
  2. react-rails gem (if you're using rails)
  3. an editor that supports vertical split screens for managing hiearchy and thinking about data-flow.



# React Native
  - TBA
