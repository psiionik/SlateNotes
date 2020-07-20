# HTML and CSS Exercises

<!-- TOC -->

- [HTML and CSS Exercises](#html-and-css-exercises)
    - [Blog Markup with CSS Thoughts](#blog-markup-with-css-thoughts)
    - [Formatting Text](#formatting-text)
    - [Tables](#tables)
    - [Example Form](#example-form)

<!-- /TOC -->

## Blog Markup with CSS Thoughts

* For styling how nav bars look and things like adding "|" in between nav items, CSS is often a better choice
    * Utilize selectors such as ":last-child" or "::after" to add content or change colors

## Formatting Text

* Formatting text to have "bold" or "italic" is much easier when you use the ```<span>``` element inside the div that holds the content
    * Since ```<span>``` is inline, there is no difference in the visual content, but it becomes easier to select in CSS

## Tables

* Default tables are ugly, it can help to use CSS selectors to add borders as well as add padding / spacing within the cells

## Example Form

* When trying to make an element larger the better way than setting the width and height largers is to adding **padding** in all 4 directions.
* Ex.

<form action="/test" method="POST">
      <p>
        <label>Name</label>
        <input name="name" required />
      </p>
      <p>
        <label>Email Address</label>
        <input name="email" type="email" required />
      </p>
      <p>
        <label>Blog URL</label>
        <input type="url" required placeholder="www.example.com" />
      </p>
      <p>
        <label>Notes</label>
        <textarea rows="3" placeholder="Anything you want to tell us!"></textarea>
      </p>
      <p>
        <button type="submit">Save!</button>
      </p>
</form>

<style>
    body {
        font-family: system-ui;
    }

    form {
        width: 50%;
        margin: 0 auto;
        text-align: center;
    }

    label {
        display: block;
        margin-bottom: 5px;
    }

    input, textarea {
        width: 300px;
        padding: 10px;
    }

    button {
        background-color: green;
        border: none;
        color: white;
        padding: 10px 30px;
        border-radius: 4px;
        cursor: pointer;
        box-shadow: 2px 2px 5px 0px rgba(0,0,0,0.45);
    }
</style>