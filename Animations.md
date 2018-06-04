USE @keyframes FOR ANIMATIONS
from and to are useful for simple animations but %'s are better
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


Animations are similar to functions in Javascript
