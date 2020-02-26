![The Conjurer by Hieronymus Bosch](https://upload.wikimedia.org/wikipedia/commons/thumb/4/49/Hieronymus_Bosch_051.jpg/2560px-Hieronymus_Bosch_051.jpg)
<sup>[The Conjurer](https://en.wikipedia.org/wiki/The_Conjurer_(painting)) by [Hieronymus Bosch](https://en.wikipedia.org/wiki/Hieronymus_Bosch)</sup>

# Block Positions

When we deal with positioning of our contents on a page, there are various useful properties that can be helpful in manipulating the different positions of an element.

```

│<-----------------SCREEN-WIDTH---------------->│
     │<-------------SITE-WIDTH------------>│
+----+-------------------------------------+----+
│....│             HEADER AREA             │....│
│....+-------------------------------------+....│
│....│                                     │....│
│....│               CONTENT               │....│
│....│                AREA                 │....│
│....│                                     │....│
│....│                                     │....│
│....+-------------------------------------+....│
│....│             FOOTER AREA             │....│
+----+-------------------------------------+----+
```

## Understanding the Positions

For simplicity, we will reuse the previous application, and create the new [02-positions](../02-positions) folder and copy the contents of [01-layout](../01-layout) into it.
And we will use the following directory structure:

```shell
02-positions
├── styles
│   ├── app.css
│   ├── flex.css
│   └── theme.css
└── index.html
```

We can now create the [app.css](styles/app.css) file for our main application styles:

```css
body {
  font-family: arial, sans-serif;
  -webkit-font-smoothing: antialiased;
}

#main {
  margin: 5em auto 0;
}

header,
footer {
  height: 5em;
  width: 100%;
}

header {
  position: fixed;
}

header h1 {
  float: left;
}

@media only screen and (min-width: 768px) {
  header,
  footer,
  #main {
    max-width: 1440px;
  }

  header,
  footer {
    margin: 0 auto;
  }

  header {
    left: 50%;
    transform: translateX(-50%);
  }
}
```

## Detailed Explanation

The `header` element with `position: fixed` will be positioned relative to the viewport, which means it always stays in the same place even if the page is scrolled.

Setting `margin: 0 auto` property to horizontally center the `header` and `footer` elements within `body` container.
Elements will occupy the specified width, and the remaining space will be divided evenly between the left and right margins.

To fix the Safari issue with the positioning of the element with a fixed position to the page center, we will use `translateX(-50%)` property for the header element.

Next, we link [app.css](styles/app.css) file to our [index.html](index.html) page:

```html
<link href="./styles/app.css" rel="stylesheet">
```

Once done, we then wrap `Header` with the `<h1>` tag simply to improve the visibility:

```html
<header><h1>Header</h1></header>
```

We can now open [index.html](https://vpodk.github.io/clap/02-positions/) page using our browser.
You may try to scroll and resize the page, or even use Chrome Dev Tools to emulate for any mobile device.

---

<table width="100%">
<tr>
<td>Previous: <a href="../01-layout">Flexible Box Layout</a></td>
<td align="right">Next: <a href="../03-nav">Hamburger Menu</a></td>
</tr>
</table>
