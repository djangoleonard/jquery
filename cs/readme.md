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





















