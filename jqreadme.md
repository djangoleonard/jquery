
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

# 4 - Manipulate DOM
## 4.1 - The DOM

When you open any webpage in a browser, the HTML of the page is loaded and rendered visually on the screen.

To accomplish this, the browser builds the Document Object Model (DOM) of that page, which is an object oriented model of its logical structure.

The DOM of an HTML document can be represented as a nested set of boxes: 

![the dom](https://api.sololearn.com/DownloadFile?id=3042)

The DOM represents a document as a tree structure where HTML elements are interrelated nodes in the tree.

Nodes can have child nodes. Nodes on the same tree level are called siblings.

jQuery traversing is the term used to describe the process of moving through the DOM and finding (selecting) HTML elements based on their relation to other elements.

> jQuery makes it easy to traverse the DOM and work with HTML elements.

## DOM Traversal

For example, consider the HTML represented by the following structure: 

![dom traversal](https://api.sololearn.com/DownloadFile?id=3085)

The \<html\> element is the parent of <body> and an ancestor of everything below it.

The \<body\> element is the parent of the \<h1\> and \<a\> elements.

The \<h1\> and \<a\> elements are child elements of the \<body\> element and descendants of \<html\>.

The \<h1\> and \<a\> elements are siblings (they share the same parent)

### Summary

An ancestor is a parent, grandparent, great-grandparent, and so on.
A descendant is a child, grandchild, great-grandchild, and so on.
Siblings share the same parent.

> Understanding the relationship between the DOM elements is important to be able to traverse the DOM correctly.

## DOM Traversal

Query has many useful methods for DOM traversal.

The parent() method returns the direct parent element of the selected element. For example:

HTML:
 
    <div> div element
      <p>paragraph</p> 
    </div>

JS:

    var e = $("p").parent();
    e.css("border", "2px solid red");

The code above selects the parent element of the paragraph and sets a red border for it.

> Run the code to see it in action.

### Traversing

The parent() method can only traverse a single level up the DOM tree.

To get all ancestors of the selected element you can use the parents() method. For example:

HTML: 

    <body>  body
      <div style="width:300px;"> div
        <ul> ul
          <li> li
            <p>paragraph</p>
          </li>
        </ul>   
      </div>
    </body>

JS:

    $(function() {
      var e = $("p").parents();
      e.css("border", "2px solid red");
    });
    

The code above sets a red border for all parents of the paragraph.

Some of the most used traversal methods are presented below: 

![traversal methods](https://api.sololearn.com/DownloadFile?id=3044)

### Traversing


The eq() method can be used to select a specific element from multiple selected elements.

For example, if the page contains multiple div elements and we want to select the third one: 

    $("div").eq(2);

> The index numbers start at 0, so the first element will have the index number 0.


HTML:

    <p>a</p><p>b</p><p>c</p>

JS:

    $(function () {
         alert($("p").eq(1).text());
    });

## 4.3 - Removing Elements

### Remove Elements

We remove selected elements from the DOM using the remove() method. For example:

HTML: 

    <p style="color:red">Red</p>
    <p style="color:green">Green</p>
    <p style="color:blue">Blue</p>
    
JS:

    $("p").eq(1).remove();

This removes Green, the second paragraph element.

You can also use the remove() method on multiple selected elements, for example $("p").remove() removes all paragraphs.

> The jQuery remove() method removes the selected element(s), as well as its child elements.


