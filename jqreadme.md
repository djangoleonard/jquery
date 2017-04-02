```
<script>
        $(function () {
            var txt = $("<p></p>").text("Hi");
            $("#demo").after(txt);
            var a = $("<span> Baba</span>");
            $("#txt").append(a);
        });
</script>`

```

# 3 - Manipulating CSS

## 3.1 - Adding & Removing Classes

### Manipulating CSS

jQuery has several methods for CSS manipulation.
The addClass( ) method adds one or more classes to the selected elements.
For example:

HTML: 

```
<div>Some text</div>
```

CSS: 

```
.header {
  color: blue;
  font-size:x-large;
}
```

JS:

```
$(function () {
    $("div").addClass("header");
});
```

The above code assigns the div element the class "header".

>To specify multiple classes within the addClass() method, just separate them using spaces. For example, $("div").addClass("class1 class2 class3").

