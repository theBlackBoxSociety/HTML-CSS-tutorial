<sub><sup>
- [HTML elements, tags and attributes](#html-elements-tags-and-attributes)
	- [Elements and tags](#elements-and-tags)
	- [Attributes](#attributes)
- [Looking at the HTML of a website](#looking-at-the-html-of-a-website)
- [Hierarchical relations between elements](#hierarchical-relations-between-elements)
- [Whitespace in HTML documents](#whitespace-in-html-documents)
- [Organizing files](#organizing-files)
- [Rules for filenames](#rules-for-filenames)
- [URL's](#urls)
	- [Absolute URL's:](#absolute-urls)
	- [Relative URL's:](#relative-urls)
- [Basic structure of an HTML document](#basic-structure-of-an-html-document)
	- [Doctype](#doctype)
	- [`<html>`](#html)
	- [`<head>`](#head)
	- [`<body>`](#body)
- [How to check if your HTML is correct?](#how-to-check-if-your-html-is-correct)
- [Exercise: fix a badly made HTML page](#exercise-fix-a-badly-made-html-page)
- [Commonly used HTML elements](#commonly-used-html-elements)
	- [Inline vs block-level elements](#inline-vs-block-level-elements)
	- [Headings](#headings)
	- [Paragraphs and breaks](#paragraphs-and-breaks)
	- [Lists](#lists)
	- [Images](#images)
	- [Links](#links)
	- [Comments](#comments)
	- [Entities](#entities)
	- [Text formatting](#text-formatting)
	- [Tables](#tables)
	- [Structural elements](#structural-elements)
- [Exercise: turn some content into a website](#exercise-turn-some-content-into-a-website)
- [Homework](#homework)
</sub></sup>

# HTML

- = Hypertext Markup Language
- meaning and structure: paragraphs, lists, tables, links, ...
- hypertext: links connect pages
- markup: syntax to give meaning to content

## HTML elements, tags and attributes

![elements, tags and attributes](./img/element-tag-attribute.png)

### Elements and tags

- HTML elements are the building blocks of HTML pages.
- `<p>`, `<table>`, ...
- +- 100 different elements
- Naming is important: an element is not the same as a tag.

Start and end tags:

- An element usually has a start and end tag, an opening and closing tag.
- For example: `<p>` and `</p>`.
- A start (= opening) tag starts with `<` and ends with `>`.  
- An end (= closing) tag starts with `</` and ends with `>`.
- Not all tags have closing tags. For example: `<br>`, a break, or a new line. Another example: `<img>`.

Tag names:

- Tags have names, for example the name of the `<p>` tag is `p`.
- The names are not case-sensitive, but lowercase is more common.

Overview of all HTML tags: https://developer.mozilla.org/en-US/docs/Web/HTML/Element

### Attributes

- Some elements have attributes.
- Attributes are used to add extra info to an element.
- For example: `<img src="logo.png">`. The `<img>` element requires a `src` (source) attribute to let the browser know which image to load.
- Attribute always have the form `name="value"`. You can also use single quotes, but double quotes are more common.
- Attributes always appear at the start tag, never at the end tag.
- Some attributes are required, while others are optional. For example: the `src` attribute is required for an `<img>` tag. The `width` attribute for an `<img>` is optional.
- An element can have multiple attributes, separated by a space. The order is not important. For example: `<img src="logo.png" width="100" height="200">`.

## Looking at the HTML of a website

You can look at the HTML of any page and see how it's made:

- In most browsers, you can right-click on an element, and then select 'Inspect element'. A panel will open and show you the source of that element.
- You can see the entire HTML source of a webpage by right-clicking on the page in your browser, and then select 'View page source'.

## Hierarchical relations between elements

Elements can contain other elements. For example:

```html
<p>This is some text, and this is in <b>bold</b>.</p>
```

The nesting can go deeper:

```html
<p>This is some text, and this is in <b><i>bold and in italics</i></b>.</p>
```

We can also reformat this to show the hierarchy more clearly:

```html
<p>
    This is some text, and this is in
        <b>
            <i>
                bold and in italics
            </i>
        </b>
    .
</p>
```

Now it's more clear that there are 3 levels in piece of HTML, with a hierarchy between them. This will be important later when we talk about CSS.

There are rules about which sub-elements an element can contain. For example, a `<p>` can contain `<b>` and `<i>` elements, but not a `<table>` element.

Elements must also be properly nested. This is wrong for example:

```html
<b><i>bold and in italics</b></i>
```

The element that is opened last has to be closed first.

Browser are very forgiving. If you make a mistake, they will try to guess what you meant. In many cases, your page might work even if it contains errors. However, you should always avoid these situations, because it will lead to frustration and confusion when you start applying CSS and JS.

## Whitespace in HTML documents

- Whitespace = spaces, tabs, line break (new line).
- Browser ignore almost all whitespace.

For example:

```
<p>Hello world!</p>
```

Renders exactly the same as

```
<p>


Hello                       world!
                </p>
```

Use whitespace to make the hierarchy clear between the elements. It makes the code more readable, and there is less chance of mistakes.

For example:

```html
<table><tr><td>Item 1</td><td>€5</td><td>3</td></tr><tr><td>Item 2</td><td>€7</td><td>11</td></tr></table>
```

This is correct HTML but it's not very readable. It can be rewritten as:

```html
<table>
    <tr>
        <td>Item 1</td>
        <td>€5</td>
        <td>3</td>
    </tr>
    <tr>
        <td>Item 2</td>
        <td>€7</td>
        <td>11</td>
    </tr>
</table>
```

The result in the browser will be exactly the same, but the code is much more readable.

This piece of HTML has 3 levels. Each level is indented with a specific number of tabs. It's easy to see where an element belongs inside the structure by looking at the number of tabs in front of each element.

- level 0: `<table>`, 0 tabs
- level 1: `<tr>` inside `<table>`, 1 tab
- level 2: `<td>` inside `<tr>`, 2 tabs

Using indentation (tabs or spaces) is not required, but it helps a lot.

## Organizing files

No fixed rules. Typical directory structure of a website:

- `index.html` -> the home page
- `another_page.html`
- `img/` -> directory with images used on the site
- `css/` -> directory with stylesheets
- `js/` -> directory with JavaScript files

## Rules for filenames

HTML documents typically use the extension `.htm` or `.html`. The last one is more common.

The following rules apply to HTML documents, and other files, like images, CSS, JS, ...:

- It's best to avoid spaces in filenames. Use a dash `-` or an underscore `_` instead. Reason: spaces are not allowed in URL's.
- Use lowercase for filenames. Reason: the server your site is on might be case-sensitive, meaning: `Index.html` and `index.html` are two different documents. This could mean that your site works on your computer, but that links and images are broken when you put it online. Avoid confusion by using lowercase everywhere.

## URL's

URL's are used for links, images, ...

A URL can absolute or relative.

### Absolute URL's:

- For example: `https://google.be`, `https://kask.be/img/logo.png`, `http://mysite.com/js/app.js`, ...
- Start with `http://` or with `https://`.
- Advantage: they work everywhere. You can move your HTML document to another directory, another server, ... and the URL will still work.
- Disadvantage: a lot of repetition and typing.

### Relative URL's:

- For example: `about_us.html`, `img/logo.png`, `/`, `../data/projects.json`, ...
- Don't start with http:// or with https://.
- They only work in a specific place - they are relative to a document. If you move the document to another directory, the links won't work anymore.
- Advantage: relative URL's are shorter and more flexible. If you change the domain name of your site, then you have to change the relative URL's.
- Disadvantage: if you move a page, you have to update all the links pointing to that page.

You need to include the path to the file you want. For example, suppose you have the following directory structure:

- `index.html`
- `img/`
    - `img/logo.png`

If you want to include `logo.png` in `index.html`, you would use the URL `img/logo.png`.

You can use `..` to mean 'one directory up'. For example, suppose you have this directory structure:

- `welcome.html`
- `pages/`
    - `about.html`

If you want to link from `about.html` to `welcome.html`, you use the URL `../welcome.html`.

You can repeat `..` as many times as necessary, for example: `../../../my_page.html`.

## Basic structure of an HTML document

This is a minimal HTML page:

```html
<!DOCTYPE html>     
<html lang="en">
    <head>
        <meta charset="utf-8">
        <title>This is the title</title>
    </head>
    <body>
        <h1>Hello world!</h1>
    </body>
</html>
```

### Doctype

- Necessary, but no need to worry about the details.
- Must be on the first line.
- Mostly needed for historical reasons. There are different versions of HTML. By using this `DOCTYPE`, we tell the browser we want to use HTML 5.

### `<html>`

- An HTML document contains HTML elements.
- The `<html>` element is the container for the whole page.
- There is a hierarchical relationship between the elements.
- The `<html>` element is at the top of hierarchy.
- It has two child elements: `<head>` and `<body>`.
- These are required. In other parts of the document you are free to include other elements, but inside `<html>` we need to use `<head>` and `<body>`.
- Always set the `lang` attribute of the `<html>` element so search engines and other software know what language your document is in.

### `<head>`

- The `<head>` element contains meta information, meaning info about the document itself.
- Most important: the `<title>` of the document.
- The title appears in the title bar of the browser window, and is used when you save a bookmark, or save the page.
- It's also very important for search engines. The title is used in the search results. Also, search engine will use the text of the `<title>` to rank search results. It's very important for SEO to give good titles to pages, and to make them unique.
- `<meta charset="utf-8">` means: use the UTF-8 character set, which allows you to use characters from most languages (including Chinese, Japanese, ...)
- Other things that can appear in the `<head>` element: references to stylesheets, reference to the favicon, ...

### `<body>`

- The `<body>` element contains the actual content: text, images, ...

## How to check if your HTML is correct?

- You can 'validate' your document = checking if the HTML is correct.
- Go to https://validator.w3.org.
- Click on the tab 'Validate by Direct Input'.
- Copy and paste the HTML and click 'Check'.
- Read the results and fix any errors.

## Exercise: fix a badly made HTML page

- You will fix a badly made HTML document. There are many errors: invalid nesting, missing elements, ...
- [Download the exercise](https://raw.githubusercontent.com/theBlackBoxSociety/HTML-CSS-tutorial/main/exercises/fix_incorrect_html/index.html) (Right-click and select 'Save link as')
- Check if your document is valid on https://validator.w3.org.
- Keep working on it until the validator says you have no errors and warnings.

## Commonly used HTML elements

### Inline vs block-level elements

HTML elements can be divided in 2 groups: block-level and inline.

Block-level elements:

- examples: `<p>`, `<h1>`, `<table>`, ...
- begin on a new line
- take up the full width of their parent element

Inline elements:

- examples: `<b>`, `<i>`, `<img>`, ...
- can be part of a line of text
- do no start a new line

### Headings

- `<h1>`, `<h2>`, `<h3>`, `<h4>`, `<h5>`, `<h6>`
- These are block-level elements.
- `<h1>` = most important title
- `<h2>` = subtitle
- Use headings to indicate the logical levels in your text.

### Paragraphs and breaks

- `<p>This is a paragraph.<p>`
- Use a break `<br>` to create a new line in a paragraph.
- Paragraphs are block level elements.

### Lists

- Very common. Also used for navigation items.
- Can be ordered (with a numbering) and unordered (no numbering).
- Lists are block level elements.

Unordered:

```html
<ol>
    <li>cookies</li>
    <li>milk</li>
    <li>bread</li>
</ol>
```

Ordered:

```html
<ul>
    <li>cookies</li>
    <li>milk</li>
    <li>bread</li>
</ul>
```

Lists can also be nested:

```html
<ol>
  <li>
    item 1
    <ol>
      <li>item 1a</li>
      <li>item 1b</li>
    </ol>
  </li>
  <li>item 2</li>
</ol>
```

### Images

- ```<img src="path_to_image" alt="alternative text for image">```
- The `src` attribute is required.
- Use relative paths for loading images within your website and absolute paths to link to an image on another website.
- `alt` attribute: a textual description of the image. This is very important to make your website accessible to anyone, including the visually impaired. A screen reader will read out the value of this attribute. It can also be used by search engines (they can't understand what's in the image).
- You can omit the description within the `alt` attribute if the image you are using is decorative and has no 'real meaning', for example a drop shadow, a separator, ...
- Images are inline level elements.
- Browsers support GIF, JPEG, PNG and SVG. You will need to convert other file formats to a supported format first, or the browser will not show it.

### Links

- `<a href="path_to_link">content that is looks like a  link</a>`
- `<a>` stands for 'anchor'
- The `href` ('hypertext reference') attribute is required.
- Use relative paths for linking files within your website and absolute path to link  to external resources and websites.
- `<a href="path_to_link" target="_blank">`
- Use the attribute `target="_blank"` to let the link open in a new tab or page.
- Links are inline level elements, so you can place a link within paragraphs, headers, lists, ...

Example of a simple link:

```html
Read more <a href="about_us.html">about us</a>.
```

Link to an external page that opens in a new window or tab:

```html
Our school <a href="https://kask.be" target="_blank">KASK</a>.
```

Linking an image:

```html
<a href="index.html">
    <img src="logo.png">
</a>
```

Email links:

- `<a href="mailto:hendrik@kask.be">send me a mail</a>`
- Clicking on the link will open a mail client (Outlook, Thunderbird, Apple Mail, ...)

### Comments

- `<!-- some comment  -->`
- Never shown by the browser.
- You can use this to clarify the structure of your document.
- Useful to temporarily hide something while working on a page.

### Entities

- Some characters have a special meaning.
- For example `<` is the start of the tag.
- We cannot use these characters directly because we would confuse the browser. We need to use 'entities'. (They need to be 'escaped'.)

Common entities:

- `&gt;` for `>` (`gt` stands for greater than)
- `&lt;` for `<` (`lt` stands for lesser than)
- `&amp;` for `&` (`amp` stands for ampersand)

### Text formatting

- `<strong>`: bold
- `<em>`: italic
- `<hr>`: horizontal rule

### Tables

Example:

```html
<table>
    <tr>
        <td>
            Row 1, column 1
        </td>
        <td>
            Row 1, column 2
        </td>
        <td>
            Row 1, column 3
        </td>
    </tr>
    <tr>
        <td>
            Row 2, column 1
        </td>
        <td>
            Row 2, column 2
        </td>
        <td>
            Row 2, column 3
        </td>
    </tr>
</table>
```

- Under the `<table>` element, create a `<tr>` for each row. `tr` = table row.
- Inside each `<tr>`, create a `<td>` element. `td` = table data.
- For the column titles, you can use a `<th>` instead of a `<td>`. `th` = table heading.

### Structural elements

These can help structuring your document:

- `<header>`: the top part of the page, which usually contains the main navigation, a logo, the search, ... Normally the header doesn't contains any actual content. Not to be confused with the `<head>` element.
- `<footer>`: the bottom part of the page, which usually contains copyright info, links to social media, legal disclaimers, ... This part also doesn't contain any actual content.
- `<main>`: the actual content of the page. Use only once per page.

Usually these elements are directly under the `<body>` element:

```html
<!DOCTYPE html>     
<html lang="en">
    <head>
        <meta charset="utf-8">
        <title>This is the title</title>
    </head>
    <body>
        <header>
            <!-- logo, navigation, search, ... -->
        </header>
        <main>
            <!-- the actual content of a page -->
        </main>
        <footer>
            <!-- credits, copyright info, ... -->
        </footer>
    </body>
</html>
```

## Exercise: turn some content into a website

- You will make a mini-website with 2 pages: a homepage and an about page.
- Create a new, empty folder for this. Create the necessary files and directories. The images should be in a separate folder.
- Each page should have a navigation on top, with links to the homepage, the about page, and a link to the KASK site. The logo should also be on top of every page, and it should link to the homepage. You can download the logo here: [exercises/content_to_website/This is our logo.jpeg](https://github.com/theBlackBoxSociety/HTML-CSS-tutorial/blob/main/exercises/content_to_website/This%20is%20our%20logo.jpeg) (right-click > save link as).
- Each page should also have a footer, which mentions 'Made by your name here' and your email address. Your email address should be a link. (Yes, you will duplicate some code. It's fine for now.)
- Remember: we work with HTML only now, and HTML is for structure, not for layout or design. For the moment it's OK if the logo and navigation are under each other instead of next to each other.
- The homepage should have a list of your three favorite website. The links should work. Also include a table where you explain what HTML, CSS and JS are used for. The columns should be 'Technology' and 'Function'. There should be 3 rows, one for each technology. For 'function', choose between structure, design and interaction.
- The about page needs to have the text in [exercises/content_to_website/about.txt](https://raw.githubusercontent.com/theBlackBoxSociety/HTML-CSS-tutorial/main/exercises/content_to_website/about.txt) (right-click > save link as). Use the appropriate HTML elements to make the structure of the text clear.
- Use proper indentation (tabs) so your code is readable.
- Validate both HTML pages using https://validator.w3.org. There should be no errors.

## Homework

- HTML review: https://www.w3schools.com/html/default.asp
- HTML quiz: https://www.w3schools.com/quiztest/quiztest.asp?qtest=HTML
- Read through https://www.w3schools.com/css/default.asp
