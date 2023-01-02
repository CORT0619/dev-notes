always do typography first 

add padding to section, footer, header 

add line-height to text 

use a container within section, header, footer and set a max-width, width (min(width, max-width) 

give images a max-width of 100% and display: block; 

em is more consistent between browsers when users are zooming in and out (em for media queries) 

  

flex-basis (the ideal width you want something to be) 

  

css custom properties 

  

:root { 

--clr-primary-300: #FFF; 

} 

  

body { 

color: var(--clr-primary-300); 

} 

 

 

 * + * is the adjacent sibling selector (any element that has a sibling before it) 

 

.split > * + * { 

 Margin-left: 2em; 

} -- if there is an element with a sibling before it then add a left margin on it 