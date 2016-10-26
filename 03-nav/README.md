![Hamburg in 1150](https://upload.wikimedia.org/wikipedia/commons/d/de/Hamburg_in_1150.jpg)
<sup>[Hamburg in 1150](https://commons.wikimedia.org/wiki/File:Hamburg_in_1150.jpg). Christoffer and Peter Suhr. Digitally restored and optimized by Rainer Scheppelmann.</sup>

# The Hamburger Menu

The hamburger menu button, as the name suggests due to it's appearance like a pixel hamburger, is a button that is usually positioned at the top corner of a graphical user interface (GUI).
Its basic functionality is in toggling a menu or providing a navigation bar by being collapsed behind the menu button or displayed on the screen.
Further detailed explanation about this type of button can be found on [Wikipedia](https://en.wikipedia.org/wiki/Hamburger_button)

```
+-------------------------------------+
│            HEADER AREA           ☰ │
+-------------------------------------+
│                                     │
│                                     │
│               CONTENT               │
│                AREA                 │
│                                     │
+-------------------------------------+
│            FOOTER AREA              │
+-------------------------------------+
```

This trigram symbol (`☰`), at the top right corner of the above diagram, can be added using the below Unicode symbol:

```css
:after {
  content:'\2630';
}
```

For our exercise, we will try to create a more smooth and animated menu button for a better user experience.

## Creating a Simple Navigation Menu

As done before, for the purpose of simplicity, we will reuse our earlier application by creating the [03-nav](./03-nav) folder and copying the contents of [02-positions](../02-positions) into this newly created folder.

Our directory structure will look like the following:

```shell
03-nav
├── styles
│   ├── app.css
│   ├── flex.css
│   ├── nav.css
│   └── theme.css
└── index.html
```

First of all, let us update the `<header>` by adding our navigation menu to the [index.html](index.html) page:

```html
<header>
  <h1>Header</h1>
  <nav id="nav">
    <input type="checkbox" aria-label="Toggle menu">
    <div class="hamburger"><span></span></div>
    <ul class="menu">
      <li><a href="./index.html">Home</a></li>
      <li><a href="./index.html">About</a></li>
      <li><a href="./index.html">Contact</a></li>
    </ul>
  </nav>
</header>
```

Next, we can create [nav.css](styles/nav.css) file. Behold! a lengthy coding awaits ahead:

```css
nav {
  display: block;
  float: right;
  left: -1em;
  padding-top: .2em;
  position: absolute;
  user-select: none;
  width: 100%;
  z-index: 1;
  -webkit-user-select: none;
}

nav input,
nav .hamburger {
  height: 32px;
  position: absolute;
  right: 0;
  width: 40px;
}

nav input {
  display: block;
  opacity: 0;
  z-index: 2;
  -webkit-touch-callout: none;
}

nav .hamburger span,
nav .hamburger span:before,
nav .hamburger span:after {
  border-radius: 4px;
  height: 2px;
  position: absolute;
  transition: transform .15s ease;
  width: 35px;
}

nav .hamburger span {
  display: block;
  margin-top: 8px;
  transition-duration: .4s;
  transition-timing-function: cubic-bezier(.68, -.55, 0.265, 1.55);
}

nav .hamburger span:before,
nav .hamburger span:after {
  content: "";
  display: block;
}

nav .hamburger span:before {
  top: 10px;
  transition: opacity .15s .4s ease;
}

nav .hamburger span:after {
  bottom: -10px;
  top: 20px;
  transition: transform .4s cubic-bezier(.68, -.55, .265, 1.55);
}

nav ul {
  bottom: 0;
  left: 0;
  list-style-type: none;
  opacity: 0;
  padding: 2.5em 1em;
  position: fixed;
  right: 0;
  top: 4em;
  transform-origin: 0% 0%;
  transform: translate(0, -200%);
  transition: transform 0.5s cubic-bezier(0.77, 0.2, 0.05, 1.0), opacity 0.5s ease-out;
  text-align: right;
  width: 100%;
  -webkit-font-smoothing: antialiased;
  z-index: 99;
}

nav input:checked ~ ul {
  opacity: .95;
  transform: none;
  z-index: 99;
}

nav input:checked ~ .hamburger span {
  transform: translate3d(0, 10px, 0) rotate(135deg);
  transition-delay: 0.1s;
}

nav input:checked ~ .hamburger span:before {
  opacity: 0;
  transition-delay: 0s;
}

nav input:checked ~ .hamburger span:after {
  transform: translate3d(0, -20px, 0) rotate(-270deg);
  transition-delay: .1s;
}

nav .menu a {
  display: inline-block;
  margin: 1em 0 0;
  padding: 1em 1em .8em;
  text-decoration: none;
  text-transform: uppercase;
}

nav .menu .active,
nav .menu :active {
  border-radius: 3px;
}

@media only screen and (min-width: 768px) {
  nav .hamburger {display: none;}
  nav, nav ul  {padding: 0; position: static; margin: 0; width: auto;}
  nav ul {opacity: 1; margin-top: -1em; transform: none; transition: none;}
  nav li {display: inline-block;}
  nav .menu .active {margin: 1em;}
}
```

## Improving the Presentation

For the purpose of improving the way it appears, we need to update [theme.css](styles/theme.css) file so that the menu button is presented smoothly:

```css
nav ul,
nav a {
  background-color: Indigo;
  color: White;
}

nav .menu a.active,
nav .menu a:active,
nav .menu a:hover {
  background-color: DarkMagenta;
}

nav .hamburger span,
nav .hamburger span::before,
nav .hamburger span::after {
  background-color: White;
}
```

## Testing the Result

**Note:** Do not forget to link the [nav.css](styles/nav.css) file to the [index.html](index.html) page:

```html
<link href="./styles/nav.css" rel="stylesheet">
```

Now we can open the [index.html](https://vpodk.github.io/clap/03-nav/) page using our browser.
The page can be resized (as we had done previously) or emulated for mobile devices using Chrome Dev Tools.

---

<table width="100%">
<tr>
<td>Previous: <a href="../02-header">Block Positions</a></td>
<td align="right">Next: <a href="../04-images">Inline Images</a></td>
</tr>
</table>
