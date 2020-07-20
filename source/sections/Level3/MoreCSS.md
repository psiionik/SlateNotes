# More CSS

<!-- TOC -->

- [More CSS](#more-css)
    - [Box Model](#box-model)
    - [Border](#border)
        - [Border-style](#border-style)
        - [Border-width](#border-width)
        - [Border-color](#border-color)
        - [Border-radius](#border-radius)
    - [Margin](#margin)
    - [Padding](#padding)
    - [Box Sizing](#box-sizing)
    - [Display](#display)
        - [Inline](#inline)
        - [Block](#block)
        - [None](#none)
    - [Positioning](#positioning)
        - [Static](#static)
        - [Relative](#relative)
        - [Absolute](#absolute)
        - [Fixed](#fixed)
        - [Sticky](#sticky)
    - [Floating](#floating)
        - [Clearing](#clearing)
    - [Tables](#tables)
    - [Centering](#centering)
    - [Lists](#lists)
        - [list-style-type](#list-style-type)
        - [list-style-image](#list-style-image)
        - [list-style-position](#list-style-position)
    - [Filters](#filters)
        - [Blur](#blur)
        - [Opacity](#opacity)
        - [Grayscale](#grayscale)
        - [Sepia](#sepia)
        - [Invert](#invert)
        - [Brightness](#brightness)
        - [Contrast](#contrast)
        - [Saturate](#saturate)
    - [Typography](#typography)
        - [text-transform](#text-transform)
        - [text-decoration](#text-decoration)
        - [text-align](#text-align)
        - [line-height](#line-height)
    - [Error Handling](#error-handling)
    - [Custom Properties](#custom-properties)
        - [Creating variables inside elements](#creating-variables-inside-elements)
        - [Variables scope](#variables-scope)
        - [Fallback values for var()](#fallback-values-for-var)

<!-- /TOC -->

## Box Model

* In HTML and CSS, every element is essentially a box
* The box model explains how elements are presented and manipulated in CSS
* There are 4 areas in the CSS box model
    * From inside to outside
    1. Content Area
    2. Padding Area
    3. Border Area
    4. Margin Area
* Ex.

![Box Model Image](resources/BoxModel.png "Box Model")

* Setting width or height sets the content area not the padding, border, or margin areas

## Border

* The border is the thin area between the padding and margin
* Essentially, editing this area allows for editing the perimeter of the element
* Can work on borders using these properties:   
    1. border-style
    2. border-color
    3. border-width
    4. border-radius
* Can set images for borders with border-image

### Border-style

* **border-style** property allows for picking the style of border
    * Ex.
        * dotted
        * dashed
        * solid
        * double

![Borders Image](resources/Borders.png "Border styles")

### Border-width

* **border-width** allows for specifying the width of hte lines of the border
    * word values are:
        * thin
        * medium
        * thick
    * length values using "em" or "px" can also be used

### Border-color

* **border-color** is utilized to set the color of the border
* Default color is the element's text color

### Border-radius

* **border-radius** is used to set rounded corners in the border
* Value that is passed is the radius of the circle on the corners used to round the border

* Ex.

<style>
    .border {
        width: 100%;
        height: 100px;
        border-style: dotted solid dashed double;
        border-radius: 10px;
        border-color: red;
    }
</style>


<p class="border">
    Border example with border-radius, border-width, border style, and border-color
</p>

## Margin

* A CSS property that is used to add space around an element
* Margin adds space outside an element border
* Padding on the other hand adds space inside an element border
* Margin have 4 properties that can be specified:
    1. margin-top
    2. margin-right
    3. margin-bottom
    4. margin-left
* margin is typically utilized to add small amounts of spacing or for centering elements by using "auto"
    * Ex.
    ```
    .class {
        margin: 0 auto
    }
    ```
* This makes the top and bottom margin 0 px while letting the browser automatically decide the spacing of the left and right margins for the element
* Ex.

<style>
    .margin {
        margin: 0 auto;
        width: 300px;
        height: 100px
    }
</style>

<p class="margin">
    Some Test for margin centering using "auto"
</p>

* Margin is also allowed to have negative values on the properties which makes it extend the opposite way

## Padding

* Padding is the same as margin except that it adds space to the area inside the element border
* Margin adds space outside the element border
* Padding adds space inside the element border
* Similar to margin, it has 4 properties:
    1. padding-top
    2. padding-right
    3. padding-bottom
    4. padding-left
* Ex.

<style>
    .padding {
        width: 300px;
        height: 300px;
        padding: 30px 30px;
        background-color: orange;
    }
</style>

<p class="padding">
    Some text to demonstrate padding
</p>

## Box Sizing

* By default, the browsers calculate width and height of an element before the padding, border, and margin
* It gets complicated so there is a "box-sizing" property that allows for 2 property values:
    1. border-box
    2. content-box
* "border-box" changes the box-sizing such that the width and height calculation include the padding and the border
* Recommended to "reset" the CSS for every element to this setting since it is more intuitive
    * Ex.
    ```
    *, *::before, *::after {
        box-sizing: border-box;
    }
    ```
* Ex.

<style>
    .border-box {
        width: 300px;
        height: 100px;
        box-sizing: border-box;
        background-color: pink;
    }
</style>

<p class="border-box">
    Example testing out "border-box"
</p>

## Display

* "Display" property determines how the element is displayed by the browser
* 3 types of display elements (excluding "grid", "flex", "table")
    1. block
    2. inline
    3. none

### Inline

* With "inline" as the property value, the elements don't have any margin or padding applied as well as height and width
* It appears "inline" with the elements that precede and come after it

### Block

* Some elements are automatically set as "block" elements by the browser
* Block elements are those that take up 100% of the width of the screen
* They also stack on top of each other when placed one after another 
* The width and height properties are actually utilized and can also set the margin and padding

### None

* Display "none" hides the visibility of the element on the page
* The element will still be in the HTML code, but will not be rendered by the browser

## Positioning

* Property that determines where elements appear on the screen and how they appear
* Can have 5 values:
    1. static
    2. relative
    3. absolute
    4. fixed
    5. sticky

### Static

* This is the default setting that follows the normal page structure created from and HTML document

### Relative

* Allows for positioning using 4 properties:
    1. top
    2. left
    3. right
    4. bottom
    * Called offset properties tha accept a length as value
* Position relative allows for positioning the element relative to the parent element that is containing it

![Relative Position Image](resources/PositionRelative.png "Position Relative")

* Here we can see that the .box class (yellow) can be specified its position relative to the parent container which is the pink box

### Absolute

* Position absolute takes the element outside of the normal HTML flow and allows for manual positioning
* Only the (x, y) starting point is preserved
    * The starting point is the starting point of the closest container that is not static

![Absolute Position Image](resources/PositionAbsolute.png "Position Absolute")

### Fixed

* Position fixed is the same as position absolute except that the starting coordinates (x, y) are always positioned relative to the window
instead of the first non-static container
* Also fixed elements are not affected by scrolling, they will remain on the page even if scrolling occurs

### Sticky

* Position sticky is the same as fixed except that it stays at the top of the screen when the screen's scrolling has reached that element's scrolling point
* This means that it will act like static until its scrolling point is reached and then act like fixed at the top of the screen if the user keeps scrolling

## Floating

* Floating allows you to remove an element from the normal page flow and used to be the old way to create "modern" layouts
    * Kind of not utilized as much because of "Grid" and "Flexbox"
* Supports 3 values:
    1. left
    2. right
    3. none (default)
* Normally, the browser renders things like imgs and spans inline together one after another, meaning imgs will show in the middle of the text or not formatted
    * Can be fixed with floats
    * Ex.
    ![Floating Image](resources/Floating.png "Floating")
* Floated elements are removed from the normal flow of the page and the content flows around it

### Clearing

* Floating multiple elements will make them just stack next to each other horizontally
    * If space runs out at it will start a new line
* There is a property called "clear" that remedy's this and allows for horizontally floated elements to be stacked vertically
* Ex.
![Clearing Image](resources/Clearing.png "Clearing")
* For clearing use:
    * "left" to clear left floats
    * "right" to clear right floats
    * "both" to clear both left and right flaots
    * "none" (default)

## Tables

* Tables used to be heavily utilized to create fancy page layouts but are not really utilized except for creating tables because of "grid" and "flexbox"
* Can easily style every other row to have a different color utilizing :nth_child(odd) or :nth_child(even) selector
* Ex.

<style>
    table, th, td {
        border: 1px solid #333;
    }

    tbody tr:nth-child(odd) {
        background-color: #af47ff;
    }
</style>

<table>
  <thead>
    <tr>
      <th scope="col">Name</th>
      <th scope="col">Age</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th scope="row">Flavio</th>
      <td>36</td>
    </tr>
    <tr>
      <th scope="row">Roger</th>
      <td>7</td>
    </tr>
    <tr>
      <th scope="row">Syd</th>
      <td>10</td>
    </tr>
  </tbody>
</table>

## Centering

* Centering is normally a confusing thing without the aid of CSS grid and Flexbox
* For centering horizontally:
    * For text:
        * Just set "text-align" to center which automatically centers all text
        * Ex.
        ``` 
        p {
            text-align: center
        }
        ```
    * For block elements:
        * Set the width of the element and then set margin to "0 auto"
        * Ex.
        ```
        div {
            width: 50%;
            margin: 0 auto;
        }
        ```

## Lists

* Lists can be styled by CSS using the following properties:
    * list-style-type
    * list-style-image
    * list-style-position

### list-style-type

* "list-style-type" is used to set a predefined marker such as:
    * "square"
    * "disc"
    * "circle"

### list-style-image

* "list-style-image" can be used to bring in a custom image marker

### list-style-position

* "list-style-position" lets you add a marker inside or outside (default) the list content
* This brinsg the marker in the flow of the page instead of outside of it

* Ex. Using the list-style-type = circle and list-style-posion = inside

<style>
    .li-custom {
        list-style-type: circle;
        list-style-position: inside;
    }
</style>

<ul>
    <li class="li-custom">
        <span>item</span>
    </li>
    <li class="li-custom">
        <span>item</span>
    </li>
    <li class="li-custom">
        <span>item</span>
    </li>
    <li class="li-custom">
        <span>item</span>
    </li>
</ul>

## Filters

* Filters allow for "photoshop" like operations onto the elements
* Normally in photoshop it gets applied to only images, but it can be applied to any element
* The different filter values are:
    * blur()
    * opacity()
    * grayscale()
    * sepia()
    * invert()
    * brightness()
    * saturate()

### Blur

* Bluring merges the pixels together to blur what gets rendered
* Pass in a length value that specifies the blur radius
* Ex.

<style>
    .filterblur {
        filter: blur(2px);
    }
</style>

<div>
    <img class="filterblur" src="./resources/coffeefilter.jpg" />
</div>

### Opacity

* Takes a value from 0 - 1 or percentage that determines the image transparency
* There is an "opacity" property, but setting opacity in this manner is better because some implementations are hardware accelerated
* Ex.

<style>
    .filteropacity {
        filter: opacity(0.4);
    }
</style>

<div>
    <img class="filteropacity" src="./resources/coffeefilter.jpg" />
</div>

### Grayscale

* Takes a value from 0 - 1 or 0% - 100% which determines how gray the element becomes
* Ex.

<style>
    .filtergrayscale {
        filter: grayscale(1.0);
    }
</style>

<div>
    <img class="filtergrayscale" src="./resources/coffeefilter.jpg" />
</div>

### Sepia

* Takes a value from 0 - 1 or 0% - 100% which determines how much of the sepia filter gets added
* Ex.

<style>
    .filtersepia {
        filter: sepia(1.0);
    }
</style>

<div>
    <img class="filtersepia" src="./resources/coffeefilter.jpg" />
</div>

### Invert

* Takes a value from 0 - 1 or 0% - 100% that determines the amount of inversion
* 0.5 or 50% of inversion will always result in a gray image because 50% is in the middle of the color wheel
* Ex.

<style>
    .filterinvert {
        filter: invert(1.0);
    }
</style>

<div>
    <img class="filterinvert" src="./resources/coffeefilter.jpg" />
</div>

### Brightness

* Takes a value from 0 - 1 or 0% - 100% that determines how bright the image is and can reach a total white element greater than 100%
* Ex.

<style>
    .filterbrightness {
        filter: brightness(0.2);
    }
</style>

<div>
    <img class="filterbrightness" src="./resources/coffeefilter.jpg" />
</div>

### Contrast

* Takes a value from 0 - 1 or 0% - 100% that adds contrast to the image
* Values greater than 100% adds more contrast to the image
* Ex.

<style>
    .filtercontrast {
        filter: contrast(2.0);
    }
</style>

<div>
    <img class="filtercontrast" src="./resources/coffeefilter.jpg" />
</div>

### Saturate

* Takes in a value from 0 - 1 or 0% - 100% that alters the saturation of the image where 100% gives an unchanged image and anything more than 100% adds more saturation
* Ex.

<style>
    .filtersaturation {
        filter: saturate(3.0);
    }
</style>

<div>
    <img class="filtersaturation" src="./resources/coffeefilter.jpg" />
</div>

## Typography

* There are some CSS properties that get applied to typography
* Here are a few of them:
    * text-transform
    * text-decoration
    * text-align
    * line-height

### text-transform

* Allows for transforming the case of the text
* There are 4 possible values:
    1. Capitalize - capitalizes the first letter of each word
    2. Uppercase - makes all of the lettrs uppercasee
    3. Lowercase - makes all of the letters lowercase
    4. None - applies no changes but can override parent's text-transform styles to prevent inheriting

### text-decoration

* Used to add decorations to the text
* Can be combined with additional decorations and color 

<style>
    .text-deco {
        text-decoration: underline wavy red;
    }
</style>

<p class="text-deco">
    Example with text-decoration "underline wavy red"
</p>

### text-align

* Changes where the text starts or the origin (0, 0) of the box that contains it
* Possible values are:
    * start
    * end
    * left
    * center
    * justify
* Ex.

<style>
    .text-al {
        text-align: center;
    }
</style>

<p class="text-al">
    Example with text-align "center"
</p>

### line-height

* Allows you to change the height of the spacing between each line

## Error Handling

* Error handling in CSS is different from that of traditional languages such as Javascript
* Normally in languages like Javascript, when an error is reached, the program stops and then an error message is printed out
    * In CSS, the line that is errored is skipped and the next readable line is skipped as well
* Ex.
```
p {
  font-size: 20px
  color: black;
  border: 1px solid black;
}
```
* Here font-size and color are skipped, but the border rule is kept

## Custom Properties

* CSS allows for defining variables, but they work a bit differently than traditional variables such as those in Javascript
* Setting variables centralized in a file is useful because it allows for setting consistent definitions across all CSS files
* Setting variables are done by prepending "--" to a variable name
* Ex.
```
:root {
    --primary-color: yello;
}
```
* Can access variable using "url()"
* Limited in that the variable value can only be valid CSS value

### Creating variables inside elements

* Variables can be defined within any element
* Ex.
```
:root {
  --default-color: red;
}

body {
  --default-color: red;
}

main {
  --default-color: red;
}

p {
  --default-color: red;
}

span {
  --default-color: red;
}

a:hover {
  --default-color: red;
}
```
* Depending on where it was defined, the scope of the variable changes

### Variables scope

* The scope of a variable is avaiable to that selector and to all of the children of that selector
* Ex.
```
.class {
    --variable: value;
}
```
* The variable is available to all of its children
* Can set variables in the ":root" selector which is the root of the DOM elements
    * Means the variable will be available to every element in the page
* Variables can also be reassigned
* CSS variables are also case sensitive

### Fallback values for var()

* Fallback values for var() can be set by adding a second parameter to the function
* Ex.
```
.class {
    margin: var(--variable, 30px);
}
```


