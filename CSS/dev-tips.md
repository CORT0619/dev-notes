font sizes
----------
- use rem (relative to the font-size of our root (html) element - defaults to 16px usually)
- rem are better than using pixels because they adapt to the user's system and browser preferences, using pixels makes things more set
- alternative: set the font size on the html element to 62.5% (sets base font size to 10px) instead of using rem (base 16)
 ie. you want font size to be 21px set font size to 2.1 rem -> 2.1rem*10px = 21px


widths
------
- usually best to use percentages; include a max-width; viewport width may be good at times


ch unit
-------
- equal to the number 0 of any given font; generally don't want to go beyond 75 characters per line for readability so use ch to make sure your line doesn't go beyond the 75 characters per lines


### height
- if you need a height, consider a min-height instead so no overflow; consider a percentage, rem, or viewport height (issues on mobile devices - keyboard)


### padding/margin
- either em or rem, depends if you want the padding/margin to be consistent in spite of the element it's being set on or if you want to adjust based on that element's font size
- use em for padding on buttons so if you change the font-size the padding with adjust and grow with the fontsize


### document flow
--------------
- give all text elements (p tags, lists, headings, etc.) margin-top 1rem and it'll be consistent throughout the document or you can change it to 1em and the spacing will be bigger for headings because they have a larger font size


### media queries
-------------
- use em for consistency across all browsers, safari does something different if you use rem or pixels compared to other browsers

pixels
------
- shouldn't need to use them very often

video:
- https://www.youtube.com/watch?v=N5wpD9Ov_To