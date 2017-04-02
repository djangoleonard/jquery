
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

### Removing Content

The empty() method is used to remove the child elements of the selected element(s). For example:

HTML:
 
    <div>
       <p style="color:red">Red</p>
       <p style="color:green">Green</p>
       <p style="color:blue">Blue</p>
    </div>

CSS:

    div {
      background-color: aqua;
      width: 300px;
      height: 200px;
    }

JS:

    $("div").empty();
    
> This removes all the three child elements of the div, leaving it empty.

Empty the second child element of the element with id="nav"

    var e = $("#nav").children();
    e.eq(1).empty();
    
What is the output of this code?

    <div><p>1</p></div>
    <div>2</div>
    <script>
    alert($("p").parent().siblings().eq(0).text());
    </script>
    (2)

How many siblings does the \<p\> element with the id="txt" have in the following HTML?

     <div>
     <p></p>
     <p id="txt"></p>
     <p></p>
     </div> 
     (2)

# 5 - Events

## 5.1 - Handling Events

JQuery provides an efficient way to handle events. Events occur when the user performs an action, such as clicking an element, moving the mouse, or submitting a form.

When an event occurs on a target element, a handler function is executed.

For example, let's say we want to handle the click event on an element with id="demo" and display the current date when the button is clicked. Using pure JavaScript, the code looks like: 

    var x = document.getElementById("demo");
    x.onclick = function () {
      document.body.innerHTML = Date();
    }

The same event could be handled using jQuery with the following code:

    $("#demo").click(function() {
      $("body").html(Date());
    });

As you can see, the jQuery code is shorter and easier to read and write.

Notice, that the event name is provided without the "on" prefix (i.e., onclick in JavaScript is click in jQuery).

> The function that is executed when an event is fired is called the event handler.

### Common Events


The following are the most commonly used events:

**Mouse Events**

**click** occurs when an element is clicked.

**dblclick** occurs when an element is double-clicked.

**mouseenter** occurs when the mouse pointer is over (enters) the selected element.

**mouseleave** occurs when the mouse pointer leaves the selected element.

**mouseover** occurs when the mouse pointer is over the selected element.

**Keyboard Events**

**keydown** occurs when a keyboard key is pressed down.

**keyup** occurs when a keyboard key is released.

**Form Events:**

**submit** occurs when a form is submitted.

**change** occurs when the value of an element has been changed.

**focus** occurs when an element gets focus.

**blur** occurs when an element loses focus.

**Document Events:**

**ready** occurs when the DOM has been loaded.

**resize** occurs when the browser window changes size.

**scroll** occurs when the user scrolls in the specified element.

As an example, let's change the content of a div when the user types in an input field. To do that, we need to handle the **keydown** event, which occurs when a key on the keyboard is pressed:

HTML:

    <input type="text" id="name" />
    <div id="msg"></div>
    
JS:

    $("#name").keydown(function() {
      $("#msg").html($("#name").val());
    });
    

The code above handles the keydown event for the element with id="name" and assigns the content of the div with id="msg" the value of the input field.

> The event names are self-explanatory, so just experiment to see them in action.

### Handling Events


Another way to handle events in jQuery is by using the on() method.

The on() method is used to attach an event to the selected element. For example: 

    $( "p" ).on( "click", function() {
      alert("clicked");
    });

As you can see, the event name is passed as the first argument to the on() method. The second argument is the handler function.

> The on() method is useful for binding the same handler function to multiple events. You can provide multiple event names separated by spaces as the first argument. For example, you could use the same event handler for the click and dblclick events.

Handle the submit event for the form element using the on() method:


$("form").on("submit", function() {
  // some code
});

### off()

You can remove event handlers using the off() method.

For example:

    $("div").on("click", function() { 
      alert('Hi there!'); 
    }); 
    $("div").off("click");

> The argument of the off() method is the event name you want to remove the handler for.

## 5.2 - The Event Object

Every event handling function can receive an event object, which contains properties and methods related to the event:
**pageX**, **pageY** the mouse position (X & Y coordinates) at the time the event occurred, relative to the top left of the page.
**type** the type of the event (e.g. "click").
**which** the button or key that was pressed.
**data** any data that was passed in when the event was bound.
**target** the DOM element that initiated the event.
**preventDefault()** prevent the default action of the event (e.g., following a link).
**stopPropagation()** Stop the event from bubbling up to other elements.

> You can check out our JavaScript course for more information on event properties.

You can check out our JavaScript course for more information on event properties.

HTML: 

    <a href="https://www.sololearn.com">Click me</a>
    
JS:

    $( "a" ).click(function(event) {
      alert(event.pageX);
      event.preventDefault();
    });

The code above alerts the mouse position at the time of the click and prevents following the link.

> As you can see, the event object is passed to the event handler function as an argument.

Handle the keydown event on the input field and alert which key was pressed.

    $("input").keydown(function(event) {
      alert(event.which);
    });
    
### Trigger Events

We can also trigger events programmatically using the trigger() method. 

For example, you can trigger a click event without the user actually clicking on an element: 

    $("div").click(function() {
       alert("Clicked!");
    });
    $("div").trigger("click");


This code triggers the click event for the selected element.

> The trigger() method cannot be used to mimic native browser events, such as clicking on a file input box or an anchor tag. Only events in the jQuery event system can be handled.

## 5.3 - Creating a To-Do List

### To-Do List

Let's create a To-Do list project using the concepts we have learned.

The To-Do list will be able to add new items to a list, as well as remove existing items.

First, we create the HTML: 

    <h1>My To-Do List</h1>
    <input type="text" placeholder="New item" />
    <button id="add">Add</button>
    <ol id="mylist"></ol>

> Clicking the button should add the value of the input field to our <ol> list.

### To-Do List

Now, having the HTML ready, we can start writing our jQuery code.

First, we handle the click event for the button: 

    $(function() {
      $("#add").on("click", function() {
        //event handler
      });
    });
    
Inside the event handler we select the value of the input field and create a new <li> element, adding it to the list:

    var val = $("input").val();
    if(val !== '') {
      var elem = $("<li></li>").text(val);
      $(elem).append("<button class='rem'>X</button>");
      $("#mylist").append(elem);
      $("input").val(""); //clear the input
    }
    
The code above takes the value of the input field, assigns it to the val variable. The if statement checks that the value is not blank and then creates a new <li> element. A button for removing it is added, after which the newly created element is added to the \<ol id="mylist"\> list.

Here's the complete code in action: 

    $(function() {
      $("#add").on("click", function() {
        var val = $("input").val();
        if(val !== '') {
          var elem = $("<li></li>").text(val);
          $(elem).append("<button class='rem'>X</button>");
          $("#mylist").append(elem);
          $("input").val("");
        }
      });
    });

> The remove button is not working yet. We will handle it in the next section!

### To-Do List

All that is left to do is handle the click event on the class="rem" button and remove the corresponding <li> element from the list.

    $(".rem").on("click", function() {
      $(this).parent().remove();
    });
    
Remember, this is the current object. The code above removes the parent of the current object, which in our case is the parent of the remove button, the <li> element.

The complete code: 

    $(function() {
      $("#add").on("click", function() {
        var val = $("input").val();
        if(val !== '') {
         var elem = $("<li></li>").text(val);
         $(elem).append("<button class='rem'>X</button>");
         $("#mylist").append(elem);
         $("input").val("");
         $(".rem").on("click", function() {
          $(this).parent().remove();
         });
        }
      });
    });
    
> The To-Do List was just a short demonstration of how to handle events and build a simple project.

# 6 -  Effect

## 6.1 - Hide/Show, Fade, Slide

### Show/Hide

jQuery has some easy-to-implement effects to create animations.
The **hide()** and **show()** methods are used to hide and show the selected elements.
The **toggle()** method is used to toggle between hiding and showing elements.

For example: 

    $(function() {
      $("p").click(function() {
        $("div").toggle();
      });
    });


