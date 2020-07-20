# CSS Basics

<!-- TOC -->

- [CSS Basics](#css-basics)
    - [Introduction to CSS](#introduction-to-css)
    - [Adding CSS to HTML page](#adding-css-to-html-page)
    - [Selectors](#selectors)
        - [Basic Selectors](#basic-selectors)
        - [Combining Selectors](#combining-selectors)
        - [Grouping Selectors](#grouping-selectors)
        - [Selectors by following Document Tree Structure](#selectors-by-following-document-tree-structure)
    - [Cascade](#cascade)
    - [Specificity](#specificity)
        - [Specificity Calculation](#specificity-calculation)
    - [Inheritance](#inheritance)
    - [Attribute Selectors](#attribute-selectors)
    - [Pseudo Classes](#pseudo-classes)
    - [Pseudo Elements](#pseudo-elements)
    - [Colors](#colors)
    - [Units](#units)
        - [Pixels](#pixels)
        - [Percentages](#percentages)
        - [Relative Units](#relative-units)
        - [Viewport Units](#viewport-units)
        - [Fraction Units](#fraction-units)
    - [URL()](#url)
    - [Calc()](#calc)
    - [Backgrounds](#backgrounds)
    - [Comments](#comments)

<!-- /TOC -->

## Introduction to CSS

* CSS is used to style an HTML page and the corresponding elements
* CSS file has 2 parts:
    1. Selector
    2. Declaration Block
* Declarations are made in property / value pairs where the property selects the type and the value changes the value
* A CSS rule set has a selector part and a declaration
    * Ex.
    ```
    p {
        font-size: 20px;
    }
    ```
* Can select more than one tag at a time
* For classes use "." before name
    * Ex.
    ```
    .my-class {

    }
    ```
* For Id us "#" before name
    * Ex.
    ```
    #my-id {

    }
    ```

## Adding CSS to HTML page

* CSS can be added to an HTML page in 3 ways:
    1. Using the ```<link>``` tag
        * Adds an external CSS file rules to the HTML page
        * Ex.
            ```
            <link rel="stylesheet" type="text/css" href="myfile.css">
            ```
    2. Using the ```<style>``` tag
        * Allow for adding some custom CSS tags to an HTML file
        * Ex.
            ```
            <style>
                CSS Rules
            </style>
            ```
    3. Inline styles
        * Can add specific inline styling to specific HTML elements
        * Ex.
            ```
            <div style="background-color: yellow">...</div>
            ```

## Selectors

* Selectors is the idea of selecting elements in the HTML tree to target for the CSS declaration rules
* Selectors can range from very basic to very specific

### Basic Selectors

* Basic selectors entail selecting a single HTML element either by tag, class name, or id
* Ex. To target ```<p>``` elements,
```
p {
    font-size: 20px;
}
```
* The same works for classes and Id
* Class
```
.class-name {
    rules...
}
```
* Ids
```
#id-name {
    rules...
}
```

### Combining Selectors

* Can target an element by class-name or id
* Ex.
    ```
        <p class="dog-name>
            Roger
        </p>
        ...
        p.dog-name {
            rules...
        }
    ```

* For targetting multiple classes, combine the class-names in the selector without spaces
* Ex.
```
.dog-name.roger {
    rules...
}
```

### Grouping Selectors

* Can combine selectors so that the rules apply to multiple elements by having a comma in between
* Ex.
```
p, .dog-name {
  color: yellow;
}
```

### Selectors by following Document Tree Structure

* Use spaces in between to target children of a targeted element
* Ex.
```
p span {
  color: yellow;
}
```
* This targets span elements that are children of p elements

## Cascade

* Cascading is an important topic within the realm of CSS in styling HTML pages
* There is a certain order and priority that gets applied for rules because sometimes there can be conflicting rules
* What it considers in the algorithm to figure the cascading are:
    * specificity
    * importance
    * inheritance
    * order in the file

## Specificity

* Specificity is determined by a system where the more specific rule will win
    * If two rules have the same specificity, the one that appears later in the file wins

### Specificity Calculation

* Specificity is calculated by utilizing a 4 number system
* There are 4 slots and all of them starts at 0
    * 0 0 0 0
    * The slot at the leftmost is the most important and the rightmost is the least important
    * Ex. 1 0 0 0 is higher specificity than 0 1 0 0
* Slot 1:
    * Slot 1 is incremented when there is an element selector
    * Ex.
    ```
    p {}                    /* 0 0 0 1 */
    span {} 				/* 0 0 0 1 */
    p span {} 			    /* 0 0 0 2 */
    p > span {} 			/* 0 0 0 2 */
    div p > span {} 		/* 0 0 0 3 */
    ```
* Slot 2:
    * Slot 2 is incremented by:
        1. class selectors
        2. pseudo-class selectors
        3. attribute selectors
    * Ex.
    ```
    .name {}				/* 0 0 1 0 */
    .users .name {}		    /* 0 0 2 0 */
    [href$='.pdf'] {}	    /* 0 0 1 0 */
    :hover {}				/* 0 0 1 0 */
    ```
* Slot 3:
    * Slot 3 is incremented by id selectors
    * Ex.
    ```
    #name {}					/* 0 1 0 0 */
    .user #name {}			    /* 0 1 1 0 */
    #name span {}			    /* 0 1 0 1 */
    ```
* Slot 4:
    * Slot 4 is incremented by inline styling
    * Inline styling will have the most precedence over any rule 
    * Ex.
    ```
    <p style="color: red">Test</p> /* 1 0 0 0 */
    ```

* !important can be used to override any styling precedence
* Ex.
```
p {
  font-size: 20px!important;
}
```
* By making this rule, this will take precendence over any CSS rule except for those that also have !important, which in that case will resolve using the specificity rules above
* Generally its better to not utilize id rules and !important as this can create issues if multiple CSS files are utilized in one HTML page
* Rather, more specific rules should be creating by combining selectors
* !important should only be utilized to see some kind of effect when testing

## Inheritance

* Some CSS properties inherit from parent to child without having to explicitly state the rule in the child while others don't
* For example, "font-family" gets inherited from the parent to child by default but "background-color" does not get inherited from parent to child
* To force properties to inherit, create a property rule in the parent and then have "inherit" as the value in the child
* Ex.
```
body {
    background-color: yellow;
}
p {
    background-color: inherit;
}
```
* There are also methods to prevent inheriting in the children or reverting

## Attribute Selectors

* There are also ways to specify selectors to target HTML elements by their attributes
* It is possible to target a certain element tag with a id attribute utilizing the "[]" syntax
* Ex.
```
p[id] {
    rules...
}
```
* This will select all ```<p>``` elements that have an "id" attribute regardless of value
* Attribute selectors can also be matching to some regex pattern or exact
* Ex.
```
p[id="my-id] {
    rules...
}
```
* In this case the CSS will only apply when the element is a ```<p>``` tag and the id attribute matches that string

## Pseudo Classes

* Pseudo classes are predefined keywords that are used to select elements based on their state or to target a specific child
* One of the most popular ones that are used is ":hover"
    * This targets an element if it is hovered over
* Ex. When links are clicked, they switch state to ":active" and ":visited"
```
a,
a:visited,
a:active {
  color: yellow;
}
```
* Can write the CSS selector utilizing pseudo-classes to make sure that the CSS stays regardless of the element's state
* :nth-child() is another option as it allows for targeting odd and even children
    * Often utilized to style lists such that the style is different for adjacent children

## Pseudo Elements

* Used to style a specific part of an element
* Syntax starts with "::"
* The most common one are "before" and "after" which allow you to add content before or after an element
    * Most commonly used for adding things like icons
    * Must specify the content property before inserting
* Ex.
```
p::before {
  content: url(/myimage.png);
}

.myElement::before {
	content: "Hey Hey!";
}
```

## Colors

* Colors can be added to HTML elements through:
    * color
    * background-color
    * border-color
* There are different ways to set colors:
    * Named colors - Something like "blue" that CSS has predefined to work when trying to set the color
    * RGB / RGBA - allows you to pick the rgb and alpha value
        * These values go from 0 - 255
        * Ex. rgb(0, 0, 0) will be black
        * The rgba() allows you to add transparency through the last channel
    * Hexadecimal Notation - in the form of "#ffffff" or "#fff" 
        * Express the numbers in 3 two digit numbers which range from 0 - 15 (0 - f)
        * Can also add two extra digits for the alpha channel at the end
    * HSL / HSLA - For hue, saturation, and lightness
        * This is the same as RGB / RGBA but it is just in another format

## Units

* Units are standardized definitions in CSS that allow to easily set lengths, paddings, margins, etc.

### Pixels

* Pixels are the most widely utilized measurement unit
* It doesn't exactly correspond to 1 exact pixel because of the difference in retinas of devices, but allows for a easy, standardized measurement
* Ex.
```
p {
    margin-top: 20px;
}
```

### Percentages

* Percentages allow you to define properties based on the parent's value
```
.parent {
    width: 400px
}
.child {
    width: 50%; /* = 200px */
}
```

### Relative Units

* Commonly used are relative units that are relative to a font-size
* "em" is the value assigned to that element's font-size
* "rem" is the same as "em" but it measures the root element's font-size
    * Allows for consistency across the entire document

### Viewport Units

* "vw" is the viewport width which takes a percentage of the viewport width
    * Ex. 50vw means 50% of the viewport width
* "vh" is the viewport height which takes a percentage of the viewport height
* "vmin" is the viewport minimum that represents the minimum between the height and width in terms of percentage
    * Ex. 30vmin is the 30% of the current width or height, whatever is smaller
* "vmax" is the same as "vmin" just maximum
* Viewport units are not inherited, meaning to set the height based on a viewport percentage, the parent's height does not need to be specified

### Fraction Units

* "fr" are fraction units that are utilized in CSS Grids to divide space into fractions

## URL()

* URLs are used to load resources such as images, gifs, mp4s, sound, etc.
* Ex.
```
div {
    background-image: url(test.png);
}
```
* The url provided can be a relative URL, external absolute URL, or can find from the root of the domain of the CSS

## Calc()

* calc() function allows for performing basic math operations on values
    * Especially useful for adding or subtracting a length from a percentage
    * Ex.
    ```
    div {
        max-width: calc(80% - 100px)
    }
    ```
* Returns a "length" value so it can be used anywhere that expects a pixel value
* Ex.

<style>
    .calc {
        background-color: cyan;
        width: calc(80% - 200px);
    }
</style>

<p class="calc">
    Width of element defined using the calc() function
</p>

## Backgrounds

* Backgrounds of elements can be set with numerous properties
* Most popular are:
    * background-color
    * background-image
    * background-attachment
    * background-size
    * background-repeat
* Ex.

<style>
    .background-example {
        background: linear-gradient(#ffffff, #F3F333);
        width: 100%;
        height: 100px;
    }
</style>

<p class="background-example">
    Background example with linear gradient
</p>

## Comments

* For commenting in CSS, only block comments are allowed
* The syntax is ```/*...*/```
* Ex.
```
#name { display: block; } /* Nice rule! */

/* #name { display: block; } */

#name {
	display: block; /*
	color: red;
	*/
}
```
* Helps since this allowed you to comment out multiple lines until ```*/``` is reached
* CSS doesn't have inline comments so only block comments can be used