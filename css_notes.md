# CSS World of Colors

`CSS` = _Cascading Style Sheets_; imagine that there are some sheets in order. The **last** sheet has **preference** above the others. 

- `Selector` = defines the element of the html that will be styled. Selectors generally target an _attribute_ value, such as an `id` or `class` value, or target the _type_ of element, such as `<h1>` or `<p>`.

- `propierties` = a property determines the styles that will be applied to that element. **i.e.** _font-size, position, background, border_... '

- `value` = the value that will be displayed, it depends of the property.

![selector](images/css_selectors.png)

## Connection with html

#### 1- Route the CSS externally 

`<link rel="stylesheet" type="text/css" href="styles.css">`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <link rel="stylesheet" type="text/css" href="styles.css">
</head>
<body>
    <div>
        
    </div>
    
</body>
</html>
```

#### 2- CSS inside the html

`<style type="text/css">"#"</style>`

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <style type="text/css">
        p { color: red; }
        .lead { color: blue; font-size: 20px; }
        #description { color:green; font-size: 30px; padding: 20px; border: 1px solid blue; }
        section p {color: black;}
    </style>
</head>
<body>
    <section>
        <h1>This is a title</h1>
        <p class="lead"> This is a paragraph with a class</p>
        <p id="description"> This is a paragraph with an individual id, the id are unique</p>

    </section>
</body>
</html>
```

- .lead has preference over 'p' because is below
- `id` has preference above `class`.
- `section p` selects all `p` inside section

#### 3- Inline Style

```html
  <body>
    <p style="color:blue;font-size:46px;">
      I'm a big, blue, <strong>strong</strong> paragraph
    </p>
  </body>
```

## Type of Selectors

### Descendant Selector

Selects an element that resides anywhere within an identified ancestor element.

```css
CSS
article h2 {...}
```
```html
HTML
<h2>...</h2>
<article>
  <h2>This heading will be selected</h2>
  <div>
    <h2>This heading will be selected</h2>
  </div>
</article>
```

### Direct Child Selector

Selects an element that resides immediately inside an identified parent element

```css
CSS
article > p {...}
```
```html
HTML
<p>...</p>
<article>
  <p>This paragraph will be selected</p>
  <div>
    <p>...</p>
  </div>
</article>
```

### Sibling Selectors

##### 1- General Sibling Selector

Selects an element that follows anywhere after the prior element, in which both elements share the same parent.

```css
CSS
h2 ~ p {...}
```
```html
HTML
<p>...</p>
<section>
  <p>...</p>
  <h2>...</h2>
  <p>This paragraph will be selected</p>
  <div>
    <p>...</p>
  </div>
  <p>This paragraph will be selected</p>
</section>
```

##### 2- Adjacent Sibling Selector

Selects an element that follows directly after the prior element, in which both elements share the same parent.

```css
CSS
h2 + p {...}
```
```html
HTML
<p>...</p>
<section>
  <p>...</p>
  <h2>...</h2>
  <p>This paragraph will be selected</p>
  <div>
    <p>...</p>
  </div>
  <p>...</p>
</section>
```

### Attribute Selectors

- `a[target]` = **Attribute Present Selector**. Selects an element if the given attribute is present

- `a[href="http://google.com/"]` = **Attribute Equals Selector**. Selects an element if the given attribute value exactly matches the value stated

- `a[href*="login"]` = **Attribute Contains Selector**. Selects an element if the given attribute value contains at least once instance of the value stated

- `a[href^="https://"]` = **Attribute Begins With Selector**. Selects an element if the given attribute value begins with the value stated

- `a[href$=".pdf"]` = **Attribute Ends With Selector**. Selects an element if the given attribute value ends with the value stated

- `a[rel~="tag"]` = **Attribute Spaced Selector**. Selects an element if the given attribute value is whitespace-separated with one word being exactly as stated

- `a[lang|="en"]` = **Attribute Hyphenated Selector**. Selects an element if the given attribute value is hyphen-separated (`-`)and begins with the word stated.

### Pseudo-classes & Pseudo-Elements

- [Link to more information](http://learn.shayhowe.com/advanced-html-css/complex-selectors/) 

### Good exercise of Selectors

- [Select the Plates](http://flukeout.github.io/)

## Specifity 

If there are two or more conflicting **CSS rules** that point to the same element, there are some _basic rules_ that a browser follows to determine which one is the **most specific**.

![Darth Specifity](images/specificity_wars.jpeg)

- [**Specifity** Calculator](https://specificity.keegan.st/)


## Properties and Values

#### Working with Typography

- `font-family` & `font-size`

```css
p {
  font-family: "Helvetica", Arial, Gothica, sans-serif;
  font-size: 20px;  
}
```

- `font-style` & `font-variant` & `font-weight`

```css
.apple {
  font-style: italic;
  font-variant: small-caps;
  font-weight: bold;
}
```

- `line-height`

```css
body {
  line-height: 22px;
}
```

#### Shorthand Font Properties

```css
html {
  font: italic small-caps bold 14px/22px "Helvetica Neue", Helvetica, Arial, sans-serif;
}
```

- [Link to more **Shorthand** properties](https://perishablepress.com/top-5-css-shorthand-properties/#lists)

#### A World of Colors

```
rgba (66, 78 , 66, 0.5)
```

The last value adds **opacity**

#### Length

- [More information about **Length**](http://learn.shayhowe.com/html-css/getting-to-know-css/#css-property-values) 


## Positioning and the Box Model

According to the **box model** concept, every element on a page is a _rectangular box_ and may have `width`, `height`, `padding`, `border`, and `margin`. The dimensions of the box are defined by the sum of _padding + margin + border_. 

![The box](images/thebox.png)

- [Opening The **Content Box**](http://learn.shayhowe.com/html-css/opening-the-box-model/)

**Natural** or **Normal flow** explains the _behaviour_ of the content.

- `block element` = Ocuppy 100% of the box and is one over another. We can change their dimensions.

- `inline element` = take up just the space of its content, they are inline. We can't change their dimensions with width, height,...

- `display: block` and `display: inline` change the behaviour of the box.

- `display: inline-block` put the elements in one line respecting their properties.

- `float: left` or `float: right`. Float makes float the text. The text is adapted but the box is put in other level.

- `clear: both`; to stop the _flow_. Clear is put on the box that we don't want to float.

- [Positioning with **float** and **inline-block**](http://learn.shayhowe.com/html-css/positioning-content/)

![float](images/float.jpg)

| Block elements  | Inline elements |
| ------------- | ------------- |
| section  | span  |
| article  | strong  |
| aside  | em  |
| header |img  |
| footer |
| nav |
| div |
| h1 - h6 |
| p |
| ul - ol - li |
| table |

- `position: relative`; we can move the box wherever we want with _top,right, bottom, left_ but the box occupy the same space. We can edit the offset.

![relative](images/relative.jpg)

- `position: absolute`; absolute is referent to the father with `position: relative`.

![absolute](images/absolute.jpg)

- `position: fix`; if you scroll, the element doesn't move.

![positions](images/positions.jpg)


## Flexbox

The main idea behind the flex layout is to give the **container** the ability to **alter its items** (width, height and order) to best fill the available space.

A flex container expands items to fill available free space, or shrinks them to prevent overflow.

We just modificate the __father__, and the children adapt to its father's container.

`display: flex`; After this property we can write the next:

- `flex-direction: row-reverse`; from right to left;
- `flex-direction: column` or `column-reverse`; display in column.
- `flex-wrap: wrap`; newline.
- `flex-flow: row-wrap`; includes direction and wrap.

- `justify-content: center` and others; justify the children boxes.

- `align-items`; how will behave the text.
- `align-content`;how will behave the items.
- `align-self: center`; is set for every element of the father

[Complete guide to Flex](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)

**IMPORTANT** we have to active `display:flex` to modificate anything.

#### The Flex Game 

- [Flexbox Froggy](http://flexboxfroggy.com/)

## Reset.css

Is a tool that makes browsers render all elements more consistently and in line with modern standards. It precisely targets only the styles that need normalizing.
We have to link the library or copy the text on the css.

- [Normalize](https://cdnjs.com/libraries/normalize)