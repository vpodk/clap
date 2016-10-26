![Fragment of The Last Judgment by Hieronymus Bosch](https://upload.wikimedia.org/wikipedia/commons/d/da/Last_Judgement.jpg)
<sup>Fragment of [The Last Judgment](https://en.wikipedia.org/wiki/The_Last_Judgment_(Bosch_triptych_fragment)) by [Hieronymus Bosch](https://en.wikipedia.org/wiki/Hieronymus_Bosch)</sup>

# Regular Expressions in JavaScript

Regular Expression is not a nightmare, Regular Expression is one of the built-in functionalities of JavaScript which basically is used to match character combinations in strings.
It allows us to perform matches in the strings.
A detailed introduction to regular expressions can be found under the Regular Expressions chapter in the [MDN JavaScript Guide](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions).

In order to create a regular expression, JavaScript provides us with three options: class constructor, factory function, and literal notation:

```javascript
var re = new RegExp('pattern', 'flags');
var re = RegExp('pattern', 'flags');
var re = /pattern/flags;
````

## What we can do with Regular Expressions?

Firstly, RegExp method checks for a match in a string, at the end of which it returns a true or false result.
We can test for a match in a string:

```javascript
var str = 'regular expression';
var re = /express/;
console.log(re.test(str)); // true
```

The second method is used to get a list of all matches in the string.
This method returns a list containing all the matches, including capturing groups, or null if no match is found:

```javascript
var str = 'regular expression';
var re = /re[gs]?/g;
console.log(str.match(re)); // ['reg', 'res']
```

The third method is to find a match in a string and replace the corresponding substring with a replacement string i.e. a method that executes a search for a match in a string, and replaces the matched substring with a replacement substring:

```javascript
var str = 'regular expression';
var re = /regular/;
console.log(str.replace(re, 'irregular')); // irregular expression
```

Lastly, a method that uses a regular expression or a fixed string to break or divide a string into a list of substrings:

```javascript
var str = 'values,separated;by:some,characters';
var re = /[,;:]/;
console.log(str.split(re));
// ["values", "separated", "by", "some", "characters"]
```

**Note:** The `match`, `replace` and `split` are methods of `String` class, not of `RegExp`.

## Short and useful examples of Regular Expressions

### Number formatter

To simply understand, consider numbers with many digits that can be divided into groups using a separator, such as a comma "," or a period "." or a space.
Below is a single-line number formatter based on Regular Expressions:

```javascript
var str = '123456789'; // Should be a string.
var separator = ',';
var re = /\B(?=(\d{3})+(?!\d))/g;
console.log(str.replace(re, separator)); // 123,456,789
```

### Query string parser

Usually, the third-party framework or library method is used to parse a URL query string pairs of values.
But the simple query string parser typically looks like:

```javascript
var re = /([^?=&]+)(=([^&#]*))?/g;
var params = {};
query.replace(re, function(_, k, _, v) {params[k] = v});
console.log(params);
// {param1: "value1", param2: "value2", param3: "value3"}
```

### Template engine
Logic-less template engine is a syntax that has no `if` statements, `else` conditions, or `for` loops.
It rather has “variables” that may be replaced with a value - either null or a series of values.
It should typically appear as:

```javascript
var content = '<a href="mailto:{{email}}">{{ name }}</a>';
var values = {email: 'info@examle.com', name: 'Valentin'};
for (var key in values) {
  var re = new RegExp('{{\\s*' + key + '\\s*}}', 'img');
  content = content.replace(re, values[key]);
}
console.log(content); // <a href="mailto:me@examle.com">Valentin</a>
```

And exactly this approach for templates we will use in the next tutorial.

So again, Regular Expression is not a nightmare, is a powerful tool to extend development possibilities.

Keep learning the simply way and enjoy coding the professional way!

---

<table width="100%">
<tr>
<td>Previous: <a href="../04-images">Inline Images</a></td>
<td align="right">Next: <a href="../06-templates">Templates</a></td>
</tr>
</table>
