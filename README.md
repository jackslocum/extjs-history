extjs-history
=============

This project Ext JS wrapper for (https://github.com/browserstate/history.js):

- Follow the [HTML5 History API](https://developer.mozilla.org/en/DOM/Manipulating_the_browser_history) as much as possible
- Provide a cross-compatible experience for all HTML5 Browsers (they all implement the HTML5 History API a little bit differently causing different behaviours and sometimes bugs - History.js fixes this ensuring the experience is as expected / the same / great throughout the HTML5 browsers)
- Provide a backwards-compatible experience for all HTML4 Browsers using a hash-fallback (including continued support for the HTML5 History API's `data`, `title`, `pushState` and `replaceState`) with the option to [remove HTML4 support if it is not right for your application](https://github.com/browserstate/history.js/wiki/Intelligent-State-Handling)
- Provide a forwards-compatible experience for HTML4 States to HTML5 States (so if a hash-fallbacked url is accessed by a HTML5 browser it is naturally transformed into its non-hashed url equivalent)

## Browsers: Tested and Working In

### HTML5 Browsers

- Firefox 4+
- Chrome 8+
- Opera 11.5
- Safari 5.0+
- Safari iOS 4.3+

### HTML4 Browsers

- IE 6, 7, 8, 9
- Firefox 3
- Opera 10, 11.0
- Safari 4
- Safari iOS 4.2, 4.1, 4.0, 3.2


## Exposed API

### Functions

####History.pushState(data, title, url)
Adds a new History entry
- `data` (Object) The data associated with this entry. Accessible as event.data on statechange event object.
- `title` (String) The title for this entry
- `url`  (String) REQUIRED for IE8 to work - The History class will attempt to fix the URL to be compatible with the document URL. For IE8 and HTML5 browsers to play well together, this format works well: '?report=/shipping/overview'

####History.replaceState(data, title, url)
Replace the current history state
- `data` (Object) The data associated with this entry. Accessible as event.data on statechange event object.
- `title` (String) The title for this entry
- `url`  (String) REQUIRED for IE8 to work - The History class will attempt to fix the URL to be compatible with the document URL. For IE8 and HTML5 browsers to play well together, this format works well: '?report=/shipping/overview'

####History.getState()
Return the current History state as an object with the following properties:
- `data` (Object) The data associated with this entry. 
- `title` (String) The title for this entry
- `url`  (String) 

####History.back()
Go back one entry in the History (same as hitting the browser's back button)

####History.forward()
Go forward one entry in the History (same as hitting the browser's forward button)

####History.go(x)
Moves `x` entries in the History. Use a negative number to move backwards.
- `x` (Number) The number of entries to move 

### Events

####statechange
Fired when the state of the page changes. The event object contains the following properties:
- `data` (Object) The data associated with this entry. 
- `title` (String) The title for this entry
- `url`  (String) 

'xui.History.on('statechange', function(e){
    console.log(e.data);
});`


