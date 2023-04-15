---
layout: post
title:  "Colour: a Fun Way to Enhance User Experience"
date:   2009-04-06 18:40:19 -04:00
---

Bruce Mau's Optimism Palette

Recently I was hired to do some contracting work with Bruce Mau Design and learned a valuable lesson about colors and websites.

One of BMD’s designers Jim Shedden asked me to update their www.brucemaudesign.com site so that when the user navigated to a new page the colour of certain elements would change.  At first I wasn’t totally sold on the idea but gladly accepted the task.

It was a pretty cut and dry type of task that required some javascript.  Since their site does not use any dynamic page generation and does not have any server side scripting this was the best option.  Let it be known though that everything you do with CSS in a dynamic server context should be done on the server so that there is no latency when the page refreshes.

On the top right hand side of this post you can see the source image that Jim sent me.  These were the colours that he wanted to use whenever the page would refresh.

First thing to point out is the beauty of the colours.  They are very well chosen and complement each other very well.  This is why you hire designers and pay them very well, there is an art and science that go into choosing good colours and creating a good design, luckily, many great designers have an eye or intuition for what works so don’t need to be taught the science.

Now onto the javascript.  Even though this task really didn’t require a library, I still opted to use jQuery since… well… it’s awesome.  The basic idea was to create a an array of colours and pick one randomly each time a page was loaded.  The colour would then be applied to an array of jQuery CSS selectors and the desired effect would be a complete colour change each time. Here is an idea of what the javascript code looks like in production.

{% highlight javascript %}
// jQuery Colourizer
// Kent Fenwick 2009
// Use it when you want to add a splash of random colour to your page

// Create the colour array
var color_array = ["#ce521d","#ca4b89","#006b89","#3e2d7e","#61902c", "#faa31a", "#6e002a", "#4981b3",
                   "#980069", "#2dacbf", "#ee1d25", "#9cb46f", "#9a869e", "#ee008c", "#00a895",
                   "#7b181a", "#ffd63c", "#b46638", "#bcd634", "#f4ea00", "#32b6c0", "#e8ac1c",
                   "#ea2d50", "#3c7022", "#0085cc", "#97C83B"];
// Pick a random colour of the array
var random_color = color_array[Math.floor(Math.random()*color_array.length)];
// Choose some jQuery CSS selectors of elements whose colour you want to change
var colour_selectors = [".manifesto li", "a.work", "#books h2", "div.work-item a", ".news-item h4 a"];
// Choose some jQuery CSS selectors of elements whose background colour you want to change
var bg_colour_selectors = ["#navigation_bar", "#navigation li"];
// loop over the Colour Selectors and apply the new random color
jQuery.each(colour_selectors, function(i,val){
	// use each val and apply the colour css property
	$(val).css("color",random_color);
});

// loop over the Background Colour Selectors and apply the new random color
jQuery.each(bg_colour_selectors, function(i,val){
	// use each val and apply the background colour css property
	$(val).css("background-color",random_color);
});
{% endhighlight %}

You start by declaring some colours, pick your CSS selectors and then use jQuery’s iterator function to apply the desired CSS property to the specified page elements. Easy right!

There are some gotchas, you want to make sure you optimize which CSS selectors you use so that you don’t end up having CSS conflicts.  In my case there were quite a few properties in the CSS files that had to be cleaned up before this script would work as it was supposed to.  Also, if your page is really big or your connection is really slow there is a chance that the script will take a second to run.  This is why you should do it dynamically on the server if you can.  However, there is something to be said for using fun little scripts like this to add personality to your web page. It also degrades nicely so if the user has JS disabled, they will see the default colours from the CSS files which isn’t bad at all.

The final effect can be viewed by going to brucemaudesign.com and exploring the site to see the colours change.

This was a very simple idea with a relatively simple implementation that goes a long way to providing character and personality to a website.  I think this is one of the easiest ways to have fun on the page and keep your users in anticipation as they wonder what colour they are going to experience next.  Thanks Jim and Bruce Mau for asking me to do it for you.  It was great fun.

PS: I will be releasing this as a jQuery plugin in a little bit with some improvements and other configurations options so if you have any ideas or are a jQuery plugin enthusiast I would love to hear from you.

Thanks very much,

Take care,

Kent