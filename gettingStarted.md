# react - *getting started*

## What's react
> A javascript library for building user interfaces 
- Library not a framework
- Does one job and "does well", building user interface
- Declarative
    - as dev describe user interface using react's dom API
    - react takes that discription and creates dom elements
    - without react, need to work with native web APIs to build UI
    - tell what we want not how to do it.
- People think of react as the *V* in *MVC*, not entirely correct
  ([GraphQL](graphql.org))

### design concepts
#### components
- Describe UI using components
- Like functions
- input property/state, output description of UI
- reusable and composable
- can manage a private state as opposed to pure functional paradigm

#### reactive updates
- react will react when input/state changes and change output
- updates DOM when needed

#### virtual views in memory
- write HTML in javascript (JSX: converts html markup into react api which
  updates dom)
- doesn't *enhance* HTML (with loops etc like ng)
- virtual DOM useful (check Pete Hunt's talk)

### react component
#### function component (stateless)
```javascript
const Button = (props) => {
    return (
        <button>{props.label}</button>
    );
};
ReactDOM.render(<Button label="Go!" />, <parent>);
```
`props` here is properties that's passed say from parent. `props` are
immutable.

#### class component (stateful)
```javascript
class Button extends React.Component {
    handleClick = () => {
        this.prop.onClickFunction(this.prop.incrementValue);
    }

    render () {
        return (
            <button onClick={this.handleClick}>
                {this.state.counter}
            </button>
        );
    }
}

const Result = (props) => {
    return (
        <div>props.counter</div>
    );
}

class App extends React.Component {
    // component property
    state = { counter: 0 };

    // above can also be done as
    // constructor(prop) {
    //    super(prop);
    //    this.state = { counter: 0};
    // }
    
    incrementCounter = (incrementValue) => {
        this.setState((prevState) => ({
            counter: prevState.counter + incrementValue
        }));
    }

    render() {
        return (
            <div>
                <Button incrementValue={1}
                onClickFunction={this.incrementCounter} />
                <Button incrementValue={1}
                onClickFunction={this.incrementCounter} />
                <Button incrementValue={1}
                onClickFunction={this.incrementCounter} />
                <Button incrementValue={1}
                onClickFunction={this.incrementCounter} />
                <Result counter={this.state.counter} />
           </div>
        );
    }
}

ReactDom.render(<App />, <parent>)
```
class component has `props` as well as state.
class component as a `setState` method that batch updates DOM. There is
potential for race condition so use a function that accepts previous state to
avoid issues.
instead of inline functions, recommended approach is to have methods


## 2 - Working with Data

Install react-devtools to analyze any react app.

Important decision: Component structure. No bad answer, but good or better
answers. Comes with experience.

If not top level component and doesn't provide any interactivity, start the
component as a function component. Lots of advantages compared to class
component.

`className` attribute to add class to element.
`style` attribute that accepts a JS object with style properties. Looks like
inline styling but has the power of JS

`...` operator takes the properties of an object and makes it available to the
component. Reduces typing.




