Here is a quick trick how to add vim-style relative line numbers to Overleaf. 

1. Install the [Tampermonkey Addon](https://addons.mozilla.org/en-US/firefox/addon/tampermonkey/)
2. Create the following script: 

```js 
// ==UserScript==
// @name         Overleaf relative line numbers
// @namespace    http://tampermonkey.net/
// @version      0.1
// @description  try to take over the world!
// @author       You
// @match        https://www.overleaf.com/project/61f1498b72c52029fc336e36
// @icon         https://www.google.com/s2/favicons?domain=overleaf.com
// @grant        none
// ==/UserScript==

(function() {
    'use strict';
    editor = window._debug_editors[window._debug_editors.length -1];
    editor.setOption("relativeLineNumbers", "relative");

    // Your code here...
})();
```

3. Reload overleaf enjoy using relative line numbers. 

# Sources 
- https://github.com/overleaf/web/issues/659