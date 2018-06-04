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