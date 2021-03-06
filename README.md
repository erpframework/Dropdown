Dropdown
========

Very simple and lightweight (~1.6KB) jQuery plugin that turns an ordinary list of links into a drop down menu.  Can easily be combined with the [responder](https://www.github.com/Lane/Responder) plugin to create simple responsive navigation.

## Demo ##

1. [Basic Demo](http://www.laneolson.ca/sandbox/dropdown/demo.html) - This demo contains the basic dropdown menu
2. [Responsive Demo](http://www.laneolson.ca/sandbox/dropdown/responsive-demo.html) - This demo shows a responsive dropdown based on device width.  Uses the [responder](https://www.github.com/Lane/Responder) plugin.

## Basic Usage ##

### HTML ###
    <nav>
    	<ul>
    		<li><a href="#">Link One</a></li>
    		<li><a href="#">Link Two</a></li>
    		<li><a href="#">Link Three</a></li>
    		<li><a href="#">Link Four</a></li>
    		<li><a href="#">Link Five</a></li>
    	</ul>
    </nav>
  
### CSS ###

This is just the css used in the demo, feel free to use your own.

    nav { border: 2px solid #000; margin: 0px 20px;}
    nav ul { padding: 0; margin: 0; list-style: none; }
    nav ul li a { display: block; padding: 10px; background: #fff; color: #000; text-decoration: none; }
    nav ul li a:hover { background: #000; color: #fff; }
    nav ul li a strong { float: right; font-size: 8px; margin-top: 5px; }

### Javascript ###

Include the jQuery library and dropdown plugin before the closing body tag.  Also add this script right before the body tag:

    <script type="text/javascript">
      $(document).ready(function()
      {
      	$('nav').dropdown();
      });
    </script>
    

## Responsive Usage ##

### HTML ###
    <nav>
        <ul>
    		<li><a href="#">Link One</a></li>
    		<li><a href="#">Link Two</a></li>
    		<li><a href="#">Link Three</a></li>
    		<li><a href="#">Link Four</a></li>
    		<li><a href="#">Link Five</a></li>
    	</ul>
    </nav>
  
### CSS ###

This is just the css used in the demo, feel free to use your own.

    nav { border: 2px solid #000; margin: 0px 20px;}
    nav ul { padding: 0; margin: 0; list-style: none; }
    nav ul li a { display: block; padding: 10px; background: #fff; color: #000; text-decoration: none; }
    nav ul li a:hover { background: #000; color: #fff; }
    nav ul li a strong { float: right; font-size: 8px; margin-top: 5px
    
    /* Expand navigation for desktop */
    nav.desktop ul li a { display: none; }
    nav.desktop ul li ul li { display: inline; }
    nav.desktop ul li ul li a { display: inline-block; }

### Javascript ###

Include the required libraries/plugins (jQuery, dropdown, responder) and add this before the closing body tag:

    <script type="text/javascript">
        $(document).ready(function()
        {
            var navElement = $('nav');
            navElement.dropdown().responder({ 
                breakpoints: [
                    new $.responsive.Breakpoint(0, "mobile", function() { 
                       navElement.trigger('createdropdown'); 
                    }),
                    new $.responsive.Breakpoint(767, "desktop", function() { 
                        navElement.trigger('destroydropdown'); 
                    })
                ]
            });
        });
    </script>