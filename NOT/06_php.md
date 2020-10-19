Note: this is unfinished.

# Avoiding duplication

- Problem: as soon as you have more than 1 page, you start to duplicate a lot of code. 

For example, the 'first' part of all HTML documents in a site will probably be the same for all pages. The `<head>`, the navigation, ... all this is the same for every page. (Except the `<title>`, but let's ignore this for now).

```html
<!DOCTYPE html>
<html>
    <head>
        <title>About me</title>
    </head>
    <body>
        <ul>
            <li><a href="/">Home</a></li>
            <li><a href="/about.html">About</a></li>
        </ul>
```

You could say the same about the 'last' part of every HTML document. It could look like this:

```html
        <p>
            Site made by <a href="mailto:hednrik.leper@hogent.be">Hendrik Leper.</a>
        </p>
    </body>
</html>
```

- This is annoying if you want to make changes, because you have to apply the changes in multiple places. For example: if you want to add a link in the navigation, or you want to make a change to the footer, every page has to be updated.
- Solution: create separate files for repeating elements. We will make a file for the 'first' part of every document, and we will keep the HTML for it in that file. A common name for this file is `header.php`. Then, in every page of our site, we will just say: 'show the contents of `header.php` here'.
- Advantage: only 1 file (`header.php`) has to be updated when changes are needed.
- We will do the same for the 'bottom' part: we will store this in a file called `footer.php`.

# Why PHP?

- Problem: we need a system to include code from other files in our HTML pages.
- HTML itself doesn't support this.
- There are any different ways to solve this problem. You could use JavaScript, Python, Ruby, ... Here we will use PHP.

# What is PHP?

- PHP is programming language. You can use it to connect to databases, resize images, send email, ...
- It's very popular. 
- Facebook and WikiPedia are built in PHP. 
- WordPress and Drupal use PHP.
- It's installed on almost all webservers.
- It's also installed by default on Mac. It also runs on Windows.

# Using PHP

We don't have time to go deep into PHP. Here are 3 important points for our purposes:

- The extension is different: PHP files have the extension `.php`. So instead of working with files like `index.html`, 'about.html', ... we will now use `index.php`, `about.php`, ...
- The way you open the file is different: you need to use a special URL. You can't just open a `.php` file in your browser like you did before: the PHP code needs to be converted into HTML by a server. A webbrowser doesn't know how to do this. So, if you just drag a and drop a PHP file to your browser, or if you double-click on it, it's not going to work. You need to make sure your PHP files are processed by the server.
- The place where you store the files is different. You can't just save the file where you want. 

- There are different types of webservers. The most popular are Apache and nginx. These servers can work to together with PHP, and can translate the PHP code in HTML.
- If you are on a Mac, Apache and PHP are already installed. If you're on Windows, you have to install them first, for example from https://www.apachefriends.org.
