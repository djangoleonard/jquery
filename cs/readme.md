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















