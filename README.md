# Highlighter

A front-end module that takes in a list of terms and a CSS Selector or DOM node to search.  The module searches the content for any of the terms provided, wraps them in an customizable HTML element and CSS class.  This code was adapted from a [jQuery plugin by knownasilya](https://github.com/knownasilya/jquery-highlight), which carries an MIT license.

This module does not apply any styles by default, only sets up elements classes to help the end user set up highlighter styles.

## Usage

This module was designed to be used with [browserify](http://browserify.org).

```javascript
(function () {
  'use strict';

  var highlighter = require('fws-highlighter');

  highlighter.init({
    content: document.querySelector('#content'),
    words: ['highlighter', 'processed']
  });

})();
```

### Before
```html
<html>
  <head>
  </head>
  <body>
    <div id="content">
      <p>Here's some text will be processed by the highlighter.</p>
    </div
  </body>
</html>
```

### After
```html
<html>
  <head>
  </head>
  <body>
    <div id="content">
      <p>Here's some text that will be <span class="highlight">processed</span> by the <span class="highlight">highlighter</span>.</p>
    </div
  </body>
</html>
```

### Example CSS
```CSS
.highlight {
  border-bottom: 1px solid #bbb;
  cursor: help; // Pointer turns into a question mark on hover
}
```

## Options

- **content:** (CSS Selector/DOM node) The content to be searched for terms. default: `document.body`
- **class:** (String) The class used on the element that wraps each found word default: `highlight`
- **tag:** (String: HTML element)The element used to wrap each found word.  You'll likely want to keep this as an [inline element](https://developer.mozilla.org/en-US/docs/Web/HTML/Inline_elements). - default: `span`
- **skipTags:** (Regex) HTML tags that should be ignored. default: `new RegExp("^(?:|H1|H2|H3|H4|H5|H6|SCRIPT|FORM|STYLE)$")`
- **caseSensitive:** (Boolean) Should the matches be case sensitive? default: `false`
- **wordsOnly:** (Boolean) If you want to highlight partial sections of a word, e.g. `cat` from `category` default: `false`
- **wordsBoundary:** (Regex) If wordsOnly is `true` this is used to determine the boundary between words default: `\\b`

## License

The [original code](https://github.com/knownasilya/jquery-highlight) carries an MIT license.

This project is a [U.S. Government work](https://www.usa.gov/government-works).

The United States Fish and Wildlife Service (FWS) GitHub project code is provided on an "as is" basis and the user assumes responsibility for its use. FWS has relinquished control of the information and no longer has responsibility to protect the integrity, confidentiality, or availability of the information. Any reference to specific commercial products, processes, or services by service mark, trademark, manufacturer, or otherwise, does not constitute or imply their endorsement, recommendation or favoring by FWS. The FWS seal and logo shall not be used in any manner to imply endorsement of any commercial product or activity by FWS or the United States Government.
