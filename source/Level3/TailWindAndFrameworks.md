# TailWind CSS and Frameworks

<!-- TOC -->

- [TailWind CSS and Frameworks](#tailwind-css-and-frameworks)
    - [Introduction](#introduction)
    - [Tailwind First Time](#tailwind-first-time)
    - [Tailwind Margin / Padding Cheatsheet](#tailwind-margin--padding-cheatsheet)
    - [Tailwind Width Cheatsheet](#tailwind-width-cheatsheet)
    - [Tailwind Fonts Cheatsheet](#tailwind-fonts-cheatsheet)
    - [Tailwind Colors Cheatsheet](#tailwind-colors-cheatsheet)

<!-- /TOC -->

## Introduction

* There are many frameworks that exist for CSS 
    * Bootstrap
    * Tailwind
* Tailwind ties each HTML class to one CSS instruction
    * To style elements you specify the HTML class rather than writing the CSS by hand
* Leads to a lot of HTML classes, but tradeoff is don't have to write CSS

## Tailwind First Time

* Ex. Using the ```<link href="https://unpkg.com/tailwindcss@^1.0/dist/tailwind.min.css" rel="stylesheet">``` to get the Tailwind CSS framework
<head>
  <link href="https://unpkg.com/tailwindcss@^1.0/dist/tailwind.min.css" rel="stylesheet">
</head>

<body>
  <form action='/test' method='POST' class="mx-auto text-center mt-10 w-1/2">
    <p>
      <label class="block mb-3">Name</label>
      <input class="w-full border border-gray-400 border-solid p-2 mb-3" name='name' required />
    </p>
    <p>
      <label class="block mb-3">Email address</label>
      <input class="w-full border border-gray-400 border-solid p-2 mb-3" type='email' name='email' required />
    </p>
    <p>
      <label class="block mb-3">Blog URL</label>
      <input class="w-full border border-gray-400 border-solid p-2 mb-3" type='url' required placeholder='https://www.example.com' />
    </p>
    <p>
      <label class="block mb-3">Notes</label>
      <textarea class="border border-gray-400 p-3 w-full" rows='3' placeholder='Anything you want to tell us!'></textarea>
    </p>
    <p>
      <button type='submit' class="mt-5 p-3 pr-5 pl-5 bg-green-500 text-white rounded-lg">Save</button>
    </p>
  </form>
</body>

* There is a [Tailwind CSS Intellisense](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss) plugin for VS Code 

## Tailwind Margin / Padding Cheatsheet

* [Link to cheatsheet](https://thejsbootcamp.com/fWpWQfJ6UAMRiAXAvbB9/12-tailwind/03/)

## Tailwind Width Cheatsheet

* [Link to cheatsheet](https://thejsbootcamp.com/fWpWQfJ6UAMRiAXAvbB9/12-tailwind/04/)

## Tailwind Fonts Cheatsheet

* [Link to cheatsheet](https://thejsbootcamp.com/fWpWQfJ6UAMRiAXAvbB9/12-tailwind/05/)

## Tailwind Colors Cheatsheet

* [Link to cheatsheet](https://thejsbootcamp.com/fWpWQfJ6UAMRiAXAvbB9/12-tailwind/06/)
