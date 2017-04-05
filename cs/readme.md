### Modifiying an element's text

    $(document).ready(function () {
                $("h1").text("Where to?");
            });

### Modifying each of their text nodes

    $(document).ready(function () {
                $("h1").text("Where to?");
                $("li").text("Orlando");
            }); 

    <h1>Where you want to go?</h1>
    <h2>Travel Destinations</h2>
    <p>Plan your next adventure.</p>
    <ul>
        <li>Rome</li>
        <li>Paris</li>
        <li class="promo">Rio</li>
    </ul>

### Selecting by unique ID

    $("#destinations");

### Selecting by Class Name

    $(".promo");
    
### Selecting descendants

    $("#destinations li").text("bursa");
    
### Selecting direct children

    $("#destinations > li");

### Selecting multiple elements

    $(".promo, #france");

### CSS-like pseudo classes

    $("#destinations li:first");
    Rome
    $("#destinations li:last");
    Rio
    $("#destinations li:odd");
    Paris
    $("#destinations li:even");
    Rome and Rid
    
### Filtering by traversing

    Wrong
    $("#destinations li");
    Correct
    $("#destinations").find("li");
    Wrong
    $("li:first");
    Correct
    $("li").first();
    Wrong
    $("li:last");
    Correct
    $("li").last();
    
 ### Walking the DOM   
    
    $("li").first();
    $("li").first().next();
    $("li").first().next().prev();
    $("li").first();
    $("li").first().parent();

### Walking the DOM up and down

    $("#destinations").children("li");
    All li selected
    children(), unlike find(), only selects direct children
    
### Appending to the DOM
    
    Wrong
    var price = "From $399.99";
    Wrong
    var price = "<p>From $399.99</p>";
    Correct
    var price = $('<p>From $399.99</p>');
    
.append(<element>)
.prepend(<element>)
.after(<element>)
.before(<element>)

    $(document).ready(function () {
                var price = $('<p>From $399.99</p>');
                $('.vacation').before(price);
            });
    
    $('.vacation').before(price);
    Puts the price node before .vacation   
         
    $('.vacation').after(price);
    Puts the price node after .vacation
    
    $('.vacation').prepend(price);
    Adds the node to the top of .vacation
    
    $('.vacation').append(price);
    Puts the price node at the bottom of .vacation

### Removing from the DOM

    $(document).ready(function () {
                var price = $('<p>From $399.99</p>');
                $('.vacation').append(price);
                $('button').remove();
            });
            
    Removes the <button> from the DOM
    
### Appending to the DOM

    $(document).ready(function() {
                var price = $('<p>From $399.99</p>');
                $('.vacation').append(price);
                $('button').remove();
            });
    
    Appends in the same place
    
    $('.vacation').append(price);
    is the same
    price.appendTo($('.vacation'));

.appendTo(<element>)
.prependTo(<element>)
.insertAfter(<element>)
.insertBefore(<element>)

### Passing in a function

    $(document).ready(<event handler function>);
    The ready method takes an event handler function as argument
    
    function() {
    // executing the function runs the code
    // between the braces
    }
    We create a function with the function keyword
    
    $(document).ready(function() {
    // this function runs when the DOM is ready
    });
    And we pass this function as an argument to the ready method.
    
### Watching for Click
    
    $(document).ready(function() {
    // runs when the DOM is ready
    });
    
    Target all buttons
    Watch for any clicks
    $('button').on('click', function() {
    // runs when any button is clicked
    });
    Run the code inside of this function
    
    runs when the DOM is ready
    $(document).ready(function() {
        $('button').on('click', function() {
        // run this function on click
        });  
    });
    runs when a button is clicked
    
### Removing from the DOM

    $(document).ready(function () {
                $('button').on('click', function () {
                    var price = $('<p>From $399.99</p>');
                    $('.vacation').append(price);
                    $('button').remove();
                });
            })
            
### Traversing from $(this)
    
    $(document).ready(function() {
                $('button').on('click', function() {
                    var price = $('<p>From $399.99</p>');
                    $(this).after(price);
                    $(this).remove();
                });
            });
    Add the price as a sibling after button
    
### Using .closest(<selector>)

    $(document).ready(function() {
                $('button').on('click', function() {
                    var price = $('<p>From $399.99</p>');
                    $(this).closest('.vacation').append(price);
                    $(this).remove();
                });
            });

    Adds the <p> node at the bottom of .vacation

### Traversing and Filtering

    <li class="vacation onsale" data-price='399.99'>
    <h3>Hawaiian Vacation</h3>
    <button>Get Price</button>
    <ul class='comments'>
        <li>Amazing deal!</li>
        <li>Want to go!</li>
    </ul>
    </li>
    All data attributes begin with ‘data-’
    
jQuery Object Methods
.data(<name>)
.data(<name>, <value>)

    $('.vacation').first().data('price');
    All data attributes begin with ‘data-’
    "399.99"

### Refactoring ‘Get Price’

    var amount = $(this).closest('.vacation').data('price');
    var price = $('<p>From $'+amount+'</p>');
    Joins two strings to create the price

### Reusing jQuery Objects

    $(document).ready(function () {
                $('button').on('click', function () {
                    var vacation = $(this).closest('.vacation');
                    var amount = vacation.data('price');
                    var price = $('<p>From $'+amount+'</p>');
                    vacation.append(price);
                    $(this).remove();
                });
            })
    We’ll only query the DOM once for this element

### On With a Selector
    $(document).ready(function() {
    $('button').on('click', function() {
    ...
    });
    });
    If we add new buttons anywhere, they will trigger this click handler
    
    
    $('.vacation button').on('click', function() {});
    Correct
    $('.vacation').on('click', 'button', function() {});
    Only target a ‘button’ if it’s inside a ‘.vacation’

### Filtering for Vacations On sale

    $('#filters').on('click', '.onsale-filter',
    function() {
    $('.vacation').filter('.onsale')
    // add a class to these vacations
    });

Class Manipulation
.removeClass(<class>)
.addClass(<class>)

    $('.vacation').filter('.onsale').addClass('highlighted');
---
    $('#filters').on('click', '.onsale-filter', function() {
            $('.vacation').filter('.onsale').addClass('highlighted');
        });
---
    $('#filters').on('click', '.expiring-filter', function() {
            $('.vacation').filter('.expiring').addClass('highlighted');
        });


### On DOM Load

### Using slideDown to Show Elements

    $(document).ready(function () {
                $('.confirmation').on('click', 'button', function() {
                    $(this).closest('.confirmation').find('.ticket').slideDown();
                });
            });
            
    Searches up through ancestors
    Searches down through children
    
jQuery Object Methods
.slideDown()
.slideUp()
.slideToggle()

### Alert and Length

alert('Hello');

$('li').length;

-->3

To query how many nodes are on a page.

### Mouse Events

click

dblclick

focusin

focusout

mousedown

mouseup

mousemove

mouseout

mouseover

mouseleave

mouseenter

    $(document).ready(function() {
                $('.confirmation').on('click', 'button', function() {
                    $(this).closest('.confirmation').find('.ticket').slideDown();
                });
            });
            $('.confirmation').on('mouseenter', 'h3', function() {
                $(this).closest('.confirmation').find('.ticket').slideDown();
            });
            
### Refactoring Handler Functions

    $(document).ready(function() {
                    $('.confirmation').on('click', 'button', function() {
                        $(this).closest('.confirmation').find('.ticket').slideDown();
                    });
                });
                $('.confirmation').on('mouseenter', 'h3', function() {
                    $(this).closest('.confirmation').find('.ticket').slideDown();
                });
     This code is duplicated, how can we refactor this?
---
    function showTicket () {
        $(this).closest('.confirmation').find('.ticket').slideDown();
    }
    
    
    function showTicket () {
        $(this).closest('.confirmation').find('.ticket').slideDown();
    }
    $(document).ready(function() {
        $('.confirmation').on('click', 'button', showTicket);
        $('.confirmation').on('mouseenter', 'h3', showTicket);
    });
    Don’t add () at the end - that would execute the function immediately
    
    
                














