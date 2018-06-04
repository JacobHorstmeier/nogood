Table of Contents:
<!-- look up canvas for html for some design application -->

1.1 - Media Queries
1.2 - Animations
1.3 - Transitions

------------------------------------------------------------------------------------------------------

[1.1] Media Queries
<!-- regular phone design css above -->
<!-- tablet size -->
@media(min-width: 500px){
    .m_box {
        width: 400px;
        background-color: red
    }
    h1 {
        font-size: 100px;
    }
}
<!-- desktop size-->
@media(min-width: 800px){
    h1 {
        font-size: 150
    }
}
<!-- for desktop first designs you would use max-width 500px in your query, essentially just a backwards version of our query -->
<!-- the and keyword can allow you to return to previous styling -->
<!-- @media(min-width: 500px) and (max-width: 900px){
    .m_box {
        width: 400px;
        background-color: red
    }
    h1 {
        font-size: 100px;
    }
} -->

ALWAYS PUT MEDIA QUERIES AT THE BOTTOM:
cascade effect will make it so the query is overwritten if there are styles underneath

example code is basically saying as soon as it hits 500px, we are going to change the style. Media Queries are similar to if statements.
if you are a minimum of 500px wide, then do these styles


Media queries allow us to set a different css if a condition is met

desktop first based design gets tricky as you scale down to a mobile phone
Mobile first is quickly becoming best practice

------------------------------------------------------------------------------------------------------

[1.2] Animations

USE @keyframes FOR ANIMATIONS
very difficult to animate components that havent been created yet (react motion library helps with this for complex animations)
from and to are useful for simple animations but %'s are better
Animations are similar to functions in Javascript
transform: translate (x,y) for the y value a negative number means the object in question will go up
<!-- spin is just the name for the animation -->
<!-- iteration meaning how many times should this run -->
<!-- the default behavior of an animation will return to its original state when done. Unless you use infinite, it will never have a chance to return to OG styling -->
<!-- timing-function means that it will stay the same speed forever -->
.a_box {
    width: 400px;
    height: 300px;
    background-color: green;
    animation-name: spin;
    animation-duration: 5s;
    animation-iteration-count: infinite;
    animation-timing-function: linear;
} 

@keyframes spin {
    0%{
        background-color: green;
        transform: rotate(0deg);
       
    }
    50% {
        background-color: yellow;
        
    }
    100% {
        background-color: green;
        transform: rotate(359deg);
    }
}
<!-- @keyframes spin {
    from{
        background-color: green;
        transform: rotate(0deg);
                                    transform is how we move the animation around
    }
    to {
        background-color: yellow;
        transform: rotate(359deg);
    }
} -->



------------------------------------------------------------------------------------------------------


[1.3] Transitions
 
Transitions cannot be looped
Transition does not work with display: None (transition needs to have a starting and ending value. Display None is treated as non existant)
transitions that are separated by a few miliseconds look real nice 
when doing transistions it is a very good idea to not assume that it will use the default value (define its starting point)

.title {
    position: relative;
    right: 0;
    transition: 1s;
}

ul {
    height: 17px;
    overflow: hidden;
    transition: 1.5s;
}

@media(min-width: 600px){
    h2 {
        display: none;
    }
    ul{
        overflow: visible;
        position: -500px;
        display: flex;
        justify-content: space-between;
        width: 60vh;
    }
    main {
        display: flex;
        flex-direction: row;

    }
    .title {
        position: -500px;
    }

}

For Using transitions in Javascript:
<!-- 
class App extends Component{
    constructor(props) {
        super(props)
        this.state = {
            expand: false
        }
    }
}
render() {
    return (
        <div className="App">
            <header className="App-header">
                <img src={logo} alt="hamburger menu" onClick={()=>this.setState: !this.state.expand}>
                <ul className={`nav ${this.state.expand ? 'expand': null}}>
                    filler material
                </ul>
    )
}
by creating a true false onClick ternary and using the transition element in our css styling, we can create smooth transistions by switching the class name on and off respectively
 -->
