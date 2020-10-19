# Client vs server

- Forms are one of the main ingredients of web applications.
- Web applications are split up into 2 parts: the client and the server.

| | Client | Server |
| --- | --- | --- |
| Where? | Here, on the user's computer | There, on a computer somewhere else in the world, in a datacenter |
| Technology | HTML, CSS, JS | PHP, Java, JS, Ruby, ... |

Information can flow in both directions:

- From server to client: when you open a link to a webpage in your browser, the server sends back the HTML, CSS, images, ...
- From client to server: when you submit a form, you the send the data from your browser to the server.

# An example

```html
<h1>Contact</h1>
<form action="process_contact_form.php" method="post">
    <div>
        <label>
            Your name
            <br>
            <input type="text" name="your_name">
        </label>
    </div>
    <div>
        <label>
            Message
            <br>
            <textarea name="message"></textarea>
        </label>
    </div>
    <div>
        <input type="submit" value="Send">
    </div>
</form>
```

- HTML is used to create form elements.
- There are different types of form elements: single line text fields, multi-line textfields, buttons, ...
- The form elements must be inside a `<form>` element. It serves as a container for the form.

# Processing forms

- HTML is a markup language, not a programming language.
- You can use it to give meaning to documents, but it doesn't have programming logic.
- To process a form, you need a programming language.
- 'Processing a form' could mean: emailing the form data, storing them in database, doing a search in a database, ...
- Examples of common programming languages used on the web: PHP, Ruby, JavaScript, Java, ...
- In most cases, the form is processed on the server, not inside the browser itself.

Here is a simple example of a PHP script that can email form data from the example:

```php 
<?php
mail('bert@rekall.be', 'Message from ' . $_POST['your_name'], $_POST['message']);
header('Location: thanks.html');
exit;
```

- You would need to save this as `process_contact_form.php`, and place it on a server that can handle PHP scripts. 
- When the user clicks the submit button, the data is sent to `process_contact_form.php`. 
- The variables `$_POST['your_name']` and `$_POST['message']` will be replaced with the actual data that the user entered. Note that these correspond to the `name` attributes of the form elements.
- After sending the mail, the user will be redirected to `thanks.html`.

# Form validation

This is a simplified example. In a real situation, you would make sure that the `your_name` and `message` fields are not empty, and remove any type of input that could be dangerous. 

This is called 'form validation'. Examples are:

- Making sure that a text field contains an email address.
- Removing dangerous content from form data, to prevent hacking.
- Requiring that certain fields are not empty.
- ...

Validation can be done in 2 places:

- On the 'client', meaning in the browser, so using HTML en JavaScript.
- On the server, so in PHP or whatever programming language you are using.

Both have advantages and disadvantages:

- Client-side validation is quick. There is no need to send the data to the server first. Server-side validation by definition requires sending the data to the server first and examining it there. This is an extra step.
- As designers and developers, we never have full control over what happens on the client-side. Users can change HTML, disable JavaScript, ... This is not the case with server-side validation. A user can't change the way our server-side logic works. 

A good website or application will do both:

- Client-side validation because it's quick and interactive.
- Server-side validation because it guarantees clean data in the app.

# The `<form>` element

Basic structure:

```html
<form>
    <!-- form elements here -->
</form>
```

- `<form>` is a container for form elements.
- An HTML page can have multiple forms.

A `<form>` element has some important attributes.

## The `action` attribute

Example:

```html
<form action="process_contact_form.php">
```

- The value of the `action` attribute is a URL.
- When the user submits the form, the data will be sent to that URL. The form data will be available to the program at that URL.
- The program can then process the data. See the example above, with the PHP script that mails the form data.
- If you omit this attribute, then the form data will be submitted to the current page. This can be useful if you have a form inside a PHP page for example.

 ## The `method` attribute
 
 Example:
 
 ```html
<form method="post">
 ```

- There are only 2 possible values for the `method` attribute: `get` (the default) and `post`.
- If you omit this attribute, then `get` will be used.
- If submitting the form will have side-effects, then you should use `post`.
- A side-effect could be: something inside the database is changed (the name of a person is updated), an email is sent, a picture is deleted, ...
- If there are no side effects, then use `get`. Examples: doing a search, ...

When using `get`, the data will be visible in the URL as key/value pairs after submitting the URL. The advantage is that the user can bookmark the result of the form submission.

Here's a simple search form: 

```html
 <form action="search.php" method="get">
    <input type="text" name="search">
    <input type="submit" value="Search!">
</form>
 ```

After submitting the form, the URL in the browser's address bar will be:

```
search.php?search=ESDI
```

When using `post`, the form data is not visible in the URL, so it can't be bookmarked.

# General info about form elements

- There are many different types of form elements.
- They all have characteristics in common, so let's look at these first.

## The `name` attribute

Example:

```html
<input type="text" name="first_name">
 ```
- Most form elements require a `name` attribute.
- If you don't supply a value for it, then the form element will not be sent when the form is submitted.
- The value is important when processing the form. In the PHP for example, the value of the element above would be available as `$_GET['first_name']` or `$_POST['first_name']`.

## The `value` attribute

Example:

```html
<input type="text" name="first_name" value="Bert">
 ```

Used to set the initial value of text fields. For other field types (checkboxes, radio buttons, ...) this will usually correspond to the id of an option in the database.

## The `placeholder` attribute

Example:

```html
<input type="text" name="first_name" placeholder="Type your first name here, for example Bert">
 ```

- Works for text fields.
- Used to explain what kind data is expected.
- Will be removed once the user starts entering data.

## The `required` attribute

Example:

```html
<input type="text" name="first_name" required>
 ```

- Used to mark a field as required. 
- The browser will not let you submit the form if the field is empty.
- Note that this is client-side validation, to it's very easy to circumvent. Never rely on this if it's important that the field is really required.
- You should always visually indicate which fields are required. The convention is to add an asterisk in front of the label, for example `* First name`.

## The `readonly` attribute

Example:

```html
<input type="text" name="first_name" readonly>
 ```

- Used to make an element read-only. It cannot be changed.
- The data is still sent to the server.

## The `disabled` attribute

Example:

```html
<input type="text" name="first_name" disabled>
 ```

- Used to make an element read-only. It cannot be changed.
- The data will not be sent to the server.

## The `maxlength` attribute

Example:

```html
<input type="text" name="first_name" maxlength="255">
 ```

- Used to set the maximum allowed length of the data.
- Again, this is client-side validation, so it's not safe to rely on this.

## The `autofocus` attribute

Example:

```html
<input type="text" name="first_name" autofocus>
 ```

- Used to automatically set the focus on a field when the page is loading.
- Be careful with this because it might confuse the user.
- Best to only use this on pages where there is only 1 thing to do, for example a login page.

## The `<label>` element

- HTML is all about semantics, about using the correct elements to indicate what meaning each part has in your document.
- Form element need labels (descriptions) so that users know what to enter where.
- These descriptions should be inside `<label>` elements.
- By default, browsers don't make a visual distinction for `<label>`s. They look like regular text.
- But: when a user clicks on a label, the focus is placed inside the corresponding form element. It also helps visually impaired people to understand how they have to complete a form. 

A common usage is to wrap the description + the form element itself inside a `<label>` element. Example:

```html
<label>
    First name
    <br>
    <input type="text" name="first_name">
</label>
 ```

You are not required to wrap the form element inside the `<label>`. Both can be separate, and then you can use the `for` attribute of the `<label>` to indicate to which element it belongs. In that case, you must give the form element an `id` attribute, and use its value as the value for the `<label>`'s `for` attribute. 

For example:

```html
<p>
    <label for="first_name">
        First name
    </label>
</p>
<p>
    <input type="text" name="first_name" id="first_name">
</p>
 ```

## Grouping elements with `<fieldset>`

- A `<fieldset>` can be used to group several elements.
- By default, a browser will add a border to a `<fieldset>`. This can of course be changed with CSS.
- Inside a `<fieldset>`, you can add a title in a `<legend>`. There can only be one `<legend>` per `<fieldset>`.    

For example:

```html
<fieldset>
    <legend>Contact</legend>
    <div>
        <label>
            Email
            <br>
            <input type="email" name="email">
        </label>
        <label>
            Phone
            <br>
            <input type="text" name="phone">
        </label>
    </div>
</fieldset>
<fieldset>
    <legend>Address</legend>
    <div>
        <label>
            Street &amp; number
            <br>
            <input type="text" name="street">
        </label>
        <label>
            City
            <br>
            <input type="text" name="city">
        </label>
    </div>
</fieldset>
```

# Form elements 

## A single-line text field

Example:

```html
<input type="text" name="first_name">
 ```

- Use a `<textarea>` for multi-line text fields.
- The `type` attribute is important. The same `<input>` element is used for text fields, checkboxes, radio buttons, ... - all depending on the value of the `type` attribute.

## A multi-line text field

Example:

```html
<textarea name="message"></textarea>
 ```

A `<textarea>` has no `value` attribute. Add the initial content inside the `<textarea>` element. For example:

```html
<textarea name="message">Hello!</textarea>
 ```

Additional attributes:

- `rows`: number of visible lines
- `cols`: width of the field, in number of characters 

## A password field

```html
<input type="password" name="your_password">
 ```

- Same as a normal text field, but the characters are masked as circles.
- You should use this for all passwords. 
- The only protection you get is that people can't read the password when they look at the screen. It doesn't the field safer in other ways.

## An email field

```html
<input type="email" name="email">
 ```

- Note that the only difference with a normal text field is the value of the `type` attribute.
- The browser will check if the input is a valid email address. Again: this is client-side validation. It's useful, but you should also validate the address server-side. 

## A URL field

```html
<input type="url" name="email">
 ```

The browser will check if the input is a valid URL. Again: this is client-side validation ... 

## A number field

```html
<input type="number" name="age">
 ```

- The browser will show up and down arrow next to field to increase and decrease the value. You can also use the arrow up/down keys.
- Optional attributes: `min`, `max`, `step`.

## A radio button group

Example:

```html
<p>
    Choose your payment method:
</p>
<p>
    <label>    
        <input type="radio" name="payment_method" value="paypal">
        PayPal    
    </label>
    <label>    
        <input type="radio" name="payment_method" value="mastercard">
        MasterCard    
    </label>
    <label>    
        <input type="radio" name="payment_method" value="visa">
        VISA    
    </label>
</p>    
 ```

- Use radio buttons when you have multiple options, where only 1 option can be selected.
- A set of radio buttons belonging to the same question is called a radio button group. See above: all options belong to the 'Payment method' group.
- All radio buttons in the same group must have the same `name` attribute. See above: the `name` for each radio button is `payment_method`.
- If you don't give all options the same `name`, then the browser will allow you to select multiple options. This goes against the convention, and it will confuse users. Don't do this.
- The `value` of the selected radio button will be sent to the server. In many cases, this will contain an id from the database.
- The convention is to first have the form element, and then the label.
- If you use `<label>`'s, then users can click on them to select an option.
- If you have more than a few options, a `<select>` can be more appropriate. See later on.
- You can change the way radio buttons look with CSS, but be careful, because users are used to the default look.

Use the `checked` attribute to select an option. For example, if we wanted to activate the MasterCard option in the example above:

```html
<input type="radio" name="payment_method" value="mastercard" checked>
```

## A checkbox

Example: 

```html
<label>
    <input type="checkbox" name="accepts_tc">
    Yes, I agree to the terms &amp; conditions.
</label>
```

Checkboxes can appear alone, but often they are part of a group:

```html
<p>
    Which colors do you like?
</p>
<p>
    <label>
        <input type="checkbox" name="colors[]" value="red"> Red
    </label>
    <br>
    <label>
        <input type="checkbox" name="colors[]" value="green"> Green
    </label>
    <br>
    <label>
        <input type="checkbox" name="colors[]" value="blue"> Blue
    </label>
</p>
```

- Use checkboxes when you have multiple options, and multiple options can be selected. Use a radio button group when only 1 option can be selected.
- Use the same `name` for checkboxes belonging to the same group. Quite often, you will see that the `name` ends with `[]`. This is related with the processing of the data on the server.
- Just like with radio buttons, you can use the `checked` attribute to check a checkbox.
- The `value` of the selected checkboxes will be sent to the server. 
- If you have more than a few options, a `<select>` can be more appropriate. See later on.
- You can change the way check boxes look with CSS, but be careful, because users are used to the default look.

## A dropdown or select list

Example:

```html
<select name="country">
    <option value="">Choose</option>
    <option value="ES">Spain</option>
    <option value="BE">Belgium</option>
</select>
```

- A `<select>` will create a dropdown list.
- Inside the element, create one `<option>` for every option.
- The text for the option goes inside the `<option>` element.
- Just like with checkboxes and radio buttons, the `value` of the selected `<option>` will be sent to the sever when the form is submitted. It's often a database id. 
- Usually, the first `<option>` is an 'empty' option, with a short description, like 'Choose', or 'Choose your country'. This is done because otherwise the first 'actual' option would be automatically selected.
- Add the `selected` attribute to make an `<option>` selected. (Note: not `checked` like with checkboxes and radio buttons.)

By default, only 1 option can be selected. So: it has the same functionality as a radio button group. The advantage of course is that a `<select>` uses much less space. The disadvantage is: the user has to click on the list to see the available options. 

- When there are few options, a radio group is usually more user friendly. 
- If there are many options (for example all countries of the world), then a `<select>` is better.

A select can also support multiple selections, so then it becomes similar to a group of checkboxes. To do this, add a `multiple` attribute:

```html
<select name="country[]" multiple>
    <option value="ES">Spain</option>
    <option value="BE">Belgium</option>
</select>
```

Multiple options can be selected using Control-click. Most users don't know this, so it's best to mention this. If you only have a couple of options, and you need multi-select, then a group of checkboxes is more user friendly.

## A file field

Example:

```html
<form enctype="multipart/form-data">
    <input type="file" name="profile_picture">
</form>
```

- This will show a 'Browse ...' button.
- You should add the attribute `enctype="multipart/form-data"` to the `<form>` element if you want to enable file uploads.

## A submit button

Example:

```html
<input type="submit" value="Save">
```

- When the user clicks on the button, the form will be submitted.
- The button text is set with the `value` attribute. 

There is another way to create a submit button:

```html
<button type="submit">Save</button>
```

# Exercise

Create a form for a user account page:

- Be sure to use `<label>`'s and `<fieldsets>`'s where appropriate.
- Don't forget the `<form>` element, and the `method`.
- Also visually indicate where the required fields are.

It should be able to handle this info:
 
- First and last name: required. Make sure your name is displayed in the fields.
- Email: required. Show your email in the field.
- Year of birth: required
- Gender: required. Options: female, male, other, and 'I'd rather not say'. Only 1 option allowed. Make sure 1 is selected.
- Country: required. Only 1 option allowed. The app only works in Spain, Portugal, France, Greece and Belgium, so only these can be chosen. Make sure 1 is selected.
- Website: optional. Add the placeholder text 'Must start with http:// or https://'.
- Biography: optional. Multiple lines of text. Make sure it contains some lines of text.
- Interests: optional. Multiple options possible. Options: architecture, design, music, photography, fashion. Make sure 1 or 2 are selected.
- Password: optional.
- Profile picture: optional.
- Buttons to save.

Validate the HTML using https://validator.w3.org/#validate_by_input.