# Slider with Custom Speed for each slide

The slider have been made using slick 
https://kenwheeler.github.io/slick/

for my project I needed to change the speed the slider pause on each slide
as some Sponsors were more important than others: red are the most important 600ms, blue medium 400ms, green 100ms

![image](https://user-images.githubusercontent.com/22336407/139303146-e059e6b4-98f9-41e2-a94b-486249123448.png)

to do that I changed the speed of the slider on the event afterChange
so after the main slide has change

the time is defined in the attribute data-time in the html
```rd
        <div data-time="600">
            <div class="captionDiv">
              <strong>sponsor 1</strong><br/>              
              <em>desc sponsor 1</em><br/>
            </div>
            <a href="#" target="_blank">
              <img src="/img/SPONSOR1.png" alt="img sponsor 1"/>
            </a> 
        </div>
````
the slide time change is in the function afterChange
```rd
        jQuery('.carousel_footer_sponsor').slick({
            ...
        }).on("afterChange", function(e, slick) {
              slideTime = $('div[data-slick-index="'+ slick.currentSlide + '"]').data("time");
              jQuery('.carousel_footer_sponsor').slick("setOption", "autoplaySpeed", slideTime);
      });
````

each slide (div) has an attribute called data-time that is where I store the time for each slide
so on the event afterChange I go and grab that valuse and assign it to the slider speed


Now I also needed the slider to only move when visible
I had a very long page and need the slider to start only when the user get down to it
and to start from the mos timportant images that were positioned at the beginning so on the start I would also make the slider start from the slide 1
by assigning to the global varialbe startslick the value 1

```rd
        jQuery(window).scroll(function() {
           var hT = jQuery('.carousel_footer_sponsor').offset().top,
               hH = jQuery('.carousel_footer_sponsor').outerHeight(),
               wH = jQuery(window).height(),
               wS = jQuery(this).scrollTop();
           if (wS > (hT+hH-wH)){ 
        startSlick();
           }else{
        pauseSlick();
            }
        });
````



