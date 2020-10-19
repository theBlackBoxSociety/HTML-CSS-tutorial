*---[ A crashcourse in Code]---*
# HTML, CSS & JS

# requirements
- a browser
- a text editor

## Browsers

- There are standards for HTML, CSS and JS, but each browser implements these in their own way. You can never be completely sure that a page will look exactly the same in all browsers.
- Chrome for desktop is not the same as Chrome for mobile. Same with Safari.
- You should test your work in different browsers, and on different devices.

- On desktop, a page should at least work in Chrome, Firefox and Safari.
- On mobile, you should test in Chrome and Safari.
- Testing is especially important with CSS and JavaScript.

Most popular browsers (Oct 2020)

On desktop:    
- Chrome (Windows + Mac): 70%
- Firefox (Windows + Mac): 8%
- Safari (Mac only): 8%
- rest: Edge (Windows only), Internet Explorer (Windows only), Opera (Windows + Mac), ...
See https://gs.statcounter.com/browser-market-share/desktop/worldwide.

On mobile:    
- Chrome (iOS + Android): 61% + 7% (Samsung Internet) = 68% 
- Safari (iOS): 20%
See https://gs.statcounter.com/browser-market-share/mobile/worldwide.

See https://gs.statcounter.com for more statistics.

## Text editor
You are free to choose.

Recommendations:
 
- https://atom.io
- http://brackets.io
- https://www.sublimetext.com

Pick one editor and learn it well, especially the shortcuts.

# 3 layers in a webpage

A webpage is like a cake with 3 layers:

- HTML = structure
- CSS = design
- JavaScript = interaction

Each technology has its responsibility.

# HTML
*HTML is a markup language. It’s not a programming language because it doesn’t understand logic. It simply contains information about the structure and display of a document.*

- The bottom layer.
- This layer is all about structure, semantics, meaning.
- Use HTML to tell people and machines how the page is structured.


Examples:

- `<h1>` = this is the most important title
- `<h2>` = this is a subtitle
- `<p>` = just a paragraph

- HTML is very important for machines (software, computers):
- If HTML is used properly, a search engine (like Google) can understand the structure of the document. For example, if the search engine sees `<h1>` tags, it know that this text is important.

You can easily abuse HTML and use it for design. A classic bad example is using HTML tables to make columns in the page.

A good web designer never uses HTML for design.

# CSS
*CSS, or Cascading Style Sheets, is used to apply visual design to HTML elements. Cascading refers to the parent-child structure of CSS. A style set on a parent element will also apply to its child elements, unless a child has style rules that override that of the parent.*

- CSS = aka 'stylesheets'.
- CSS determines what the page looks like.

CSS is not required to make a webpage. If you don't add a stylesheet yourself, the browser's default stylesheet will be used.

# JavaScript

- JS: used for interaction
- For example: animations, popups, form validation, ...
