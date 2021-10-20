# Slider with Custom Speed for each slide

The slider have been made using slick 
https://kenwheeler.github.io/slick/

for my project I needed to change the speed the slider pause on each slide
as some Sponsors were more important than others

to do that I changed the speed of the slider on the event afterChange
so after the main slide has change

each slide (div) has an attribute called data-time that is where I store the time for each slide
so on the event afterChange I go and grab that valuse and assign it to the slider speed

Now I also needed the slider to only move when visible
I had a very long page and need the slider to start only when the user get down to it
and to start from the mos timportant images that were positioned at the beginning so on the start I would also make the slider start from the slide 1
by assigning to the global varialbe startslick the value 1
