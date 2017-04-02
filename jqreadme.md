
    <script>
            $(function () {
                var txt = $("<p></p>").text("Hi");
                $("#demo").after(txt);
                var a = $("<span> Baba</span>");
                $("#txt").append(a);
            });
    </script>


# 3 - Manipulating CSS

## 3.1 - Adding & Removing Classes

### Manipulating CSS

#### addClass() 

jQuery has several methods for CSS manipulation.
The addClass( ) method adds one or more classes to the selected elements.
For example:

HTML: 

    <div>Some text</div>


CSS: 

    .header {
      color: blue;
      font-size:x-large;
    }


JS:

    $(function () {
        $("div").addClass("header");
    });


The above code assigns the div element the class "header".

> To specify multiple classes within the addClass() method, just separate them using spaces. For example, $("div").addClass("class1 class2 class3").

#### removeClass()

The removeClass() method removes one or more class names from the selected elements.
For example:

    $("div").removeClass("red");

The code above removes the class "red" from the div element.

> Again, multiple class names can be specified by separating them using spaces.

#### toggleClass()

The toggleClass() method toggles between adding/removing classes from the selected elements, meaning that if the specified class exists for the element, it is removed, and if it does not exist, it is added.
To demonstrate this in action, we will handle a button click event to toggle a class. We will learn more about events and their syntax in the coming modules.

HTML:
 
    <p>Some text</p>
    <button>Toggle Class</button>

CSS:

    .red { 
      color:red; 
      font-weight: bold;
    }


JS:

    $(function() {
      $("button").click(function() {
        $("p").toggleClass("red");
      });
    });


>The code above toggles the class name "red" upon clicking the button.

## 3.2 -  CSS Properties

Similar to the html() method, the css() method can be used to get and set CSS property values.
For example:

HTML:

    <p>Some text</p>
    
CSS:

    p {
      background-color:red;
      color: white;
    }

JS:

    $(function() {
      alert($("p").css("background-color"));
      $("p").css("background-color", "blue");
    }); 


>The code above alerts the background-color property of the paragraph and then sets it to blue.

## Multiple Properties

To set multiple CSS properties, the css() method uses JSON syntax, which is: 


    css({"property":"value","property":"value",...});


As you can see, the syntax consists of "property":"value" pairs, which are comma separated and enclosed in curly brackets { }.

For Example: 

    $("p").css({"color": "red", "font-size": "200%"});

This will set the color and font-size properties of the paragraph.

>You can specify any number of properties using this JSON syntax.

## 3.3 - Dimensions

The width() and height() methods can be used to get and set the width and height of HTML elements.

Let's set both the width and height of a div to 100px, as well as set a background color for it:

    $("div").css("background-color", "red");
    $("div").width(100);
    $("div").height(100);
 
 The width() and height() methods get and set the dimensions without the padding, borders and margins.
 The innerWidth() and innerHeight() methods also include the padding.
 The outerWidth() and outerHeight() methods include the padding and borders.
 Check out this image to understand how they work:
 
 Image see;

![Dimensions](https://api.sololearn.com/DownloadFile?id=3120)

The following example demonstrates how the methods work:
 
HTML:
 
    <div></div> 
    

CSS:
 
    div {
           width: 300px;
           height: 100px;
           padding: 10px;
           margin: 20px;
           border: 3px solid blue;
           background-color: red;
           color: white;
         }
            
JS:

    $(function() {
      var txt = "";
      txt += "width: " + $("div").width() + " ";
      txt += "height: " + $("div").height() + "<br/>";
      txt += "innerWidth: " + $("div").innerWidth() + "  ";
      txt += "innerHeight: " + $("div").innerHeight() + "<br/>";
      txt += "outerWidth: " + $("div").outerWidth() + "  ";
      txt += "outerHeight: " + $("div").outerHeight();
        
      $("div").html(txt);
    });
    
> Run the code to see the values returned by the dimension methods.