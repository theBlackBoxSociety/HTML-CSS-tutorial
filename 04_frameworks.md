Note: this is unfinished.

# What is a CCS Framework?

- It's a set of re-usable components that are common in websites. For example: menu systems, buttons, dropdowns, ...
- Everything is designed consistently, so you can combine these components, and the end-result should look decent.
- Basically, it's a bunch of CSS files with predefined classes.
- For example: a class called `button`. If you apply this class to a `<a href>` you will immediately have a nice looking button. 
- A framework is a starting point. Usually you will customize the look and feel.

# Possible frameworks

- https://getbootstrap.com
- https://tailwindcss.com
- https://foundation.zurb.com
- 

Many companies, apps, ... also have their own framework.

# Why use a framework?

- It helps you create a decent-looking website quickly. It contains a basic design - nothing amazing, but good enough as a starting point, especially for wireframes.
- It make certain things a bit easier, for example column and responsive layouts.
- It's useful if you work with other people - it creates a set of conventions and a structure.

# Getting started

- Make an HTML page as usual.
- Connect to page to the Foundation CSS using a `<link>` element in the `<head>`. 

This is exactly the same as what we did before. The only difference is that we will use an absolute URL to the CSS stylesheet, so that we don't have to download it. The URL of the CSS file is:

```
https://cdn.jsdelivr.net/npm/foundation-sites@6.5.3/dist/css/foundation.min.css
```

It can also be found on https://foundation.zurb.com/sites/docs/installation.html.

So a basic page would be:

```html
<!DOCTYPE html>     
<html lang="en">
    <head>
        <meta charset="utf-8">
        <title>This is the title</title>
        <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/foundation-sites@6.5.3/dist/css/foundation.min.css"> 
    </head>
    <body>
        <h1>Hello world</h1>
    </body>
</html>
```

You should notice that font is different after connecting the HTML page to the Foundation CSS. It should have changed from the default Times New Roman to a sans-serif font.

# Grid

See https://foundation.zurb.com/sites/docs/xy-grid.html.

- A grid consists of rows and columns (or cells).
- It's a classic tool for designers. They use grids to create balanced, harmonious layouts. 
- The Foundation grid has 12 columns per row.
- The Foundation grid simplifies the creation of more complex layouts, for example: a narrow sidebar on the left and a wider area for main content on the right.
- You don't need a framework to work with a grid. It's a bit easier though.

# First example

```html
<div class="grid-x grid-padding-x">
    <div class="cell medium-3">
        sidebar
    </div>
    <div class="cell medium-9">
        <h1>Title</h1>
        <p>Some content</p>
    </div>
</div>
```

We have 2 `<div>`'s - one for each part:

- One `<div>` for the sidebar, on the left side. It's not that wide.
- One `<div>` for the main content, on the right side. It's wider.

It works like this:

- First we need to create a row. We do this by adding a `<div class="grid-x">`. (Yes, there's also `grid-y`, but let's ignore that for now.)
- We add the class `grid-padding-x` to that `<div class="grid-x">` to make sure we have some whitespace between the columns.
- Then, inside the row with `class="grid-x"`, we add a `<div>` for every part. Every cell must have `class="cell"`.
- To set the size of cell, we add another class: `medium-x`. The `x` is a number between 1 and 12. 
- There are 12 columns per row. So `medium-3` will create a cell that is 25% (3/12) of the available width.
- The total of all the cells has to be 12. Since we used already used 3 columns for the sidebar, so we have 12 - 3 = 9 remaining for the main content.
- The `medium` part in the class name `medium-3` means that Foundation will only use columns on screen resolutions that are at least medium. If you view this page on a smaller resolution (try resizing the browser window), the cells will be stacked vertically.

Another example with three equal size cells:

```html
<div class="grid-x grid-padding-x">
    <div class="cell medium-4">
        left
    </div>
    <div class="cell medium-4">
        middle
    </div>
    <div class="cell medium-4">
        right
    </div>
</div>
```

## Nesting grids

Grids can also be nested, so you can have a grid inside a grid. In that case, you just start with another row that is 12 columns wide:

```html
<div class="grid-x grid-padding-x">
    <div class="cell medium-3">
        sidebar
    </div>
    <div class="cell medium-9">
        main
        <div class="grid-x grid-padding-x">
            <div class="cell medium-6">
                left
            </div>
            <div class="cell medium-6">
                right
            </div>
        </div>
    </div>
</div>
```

## Block grids

- Block grids automatically create new rows as necessary.
- You just tell Foundation how many cells per row you want.
- Adding the class `medium-x` means: x cells per row on medium and higher resolutions.
- Adding the class `small-x` means: x cells per row on small (phone) resolutions.
- Very useful if you want to show a series of items, like projects with a thumbnail, images in a photo gallery, ...  

```html
<div class="grid-x grid-padding-x small-2 medium-3">
    <div class="cell">cell</div>
    <div class="cell">cell</div>
    <div class="cell">cell</div>
    <div class="cell">cell</div>
    <div class="cell">cell</div>
    <div class="cell">cell</div>
</div>
```

# Forms

See https://foundation.zurb.com/sites/docs/forms.html.

- Foundation has pretty good default styling for forms.
- Use `<p class="help-text">` for adding help texts to forms. 

Wrap form elements in `<label>`s. Foundation will automatically turn the label in a block-level element, so that it starts on a new line.

For example:

```html
<label>
    First name
    <input type="text" name="first_name">
</label>
```

# Buttons

See https://foundation.zurb.com/sites/docs/button.html.

You can easily turn a link into a button, just by adding the class `button` to it.

```html
<a href="about.html" class="button">
    Learn more
</a>
```

It can also be applied to:

- `<input type="submit">`
- `<button>`

Other useful button classes:

- Size: `tiny`, `small`, `large`, ... 
- Color: `secondary`, `alert`, `warning`, ... 

# Menu

See https://foundation.zurb.com/sites/docs/menu.html.

Add a class `menu` to a `<ul>` to turn it into a horizontal menu:

```html
<ul class="menu">
  <li><a href="#">One</a></li>
  <li><a href="#">Two</a></li>
  <li><a href="#">Three</a></li>
  <li><a href="#">Four</a></li>
</ul>
```

Add the class `vertical` to the `<ul>` to turn it into a vertical menu.

Very important: also show the users where they are. So: indicate which menu item is active. In Foundation, this can be done by adding a class `is-active` to the `<li>`:

```html
<ul class="menu">
  <li class="is-active"><a>Home</a></li>
  <li><a>About</a></li>
  <li><a>Nachos</a></li>
</ul> 
```

# Breadcrumb

See https://foundation.zurb.com/sites/docs/breadcrumbs.html.

```html
<ul class="breadcrumbs">
    <li><a href="#">Home</a></li>
    <li><a href="#">Features</a></li>
    <li class="disabled">Gene Splicing</li>
    <li>Cloning</li>
</ul>
```
