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

`History.pushState(Object data, String title, String url)` <br/> Adds a new History entry
- `data` (Object) The data associated with this entry. Accessible as event.data on statechange event object.
- `title` (String) The title for this entry
- `url`  (String) REQUIRED for IE8 to work - The History class will attempt to fix the URL to be compatible with the document URL. For IE8 and HTML5 browsers to play well together, this format works well: '?report=/shipping/overview'

- `History.replaceState(data,title,url)` <br/> Replaces the existing state with a new state to the browser; `data` can be null or an object, `title` can be null or a string, `url` must be a string
- `History.getState()` <br/> Gets the current state of the browser, returns an object with `data`, `title` and `url`
- `History.getHash()` <br/> Gets the current hash of the browser
- `History.Adapter.bind(element,event,callback)` <br/> A framework independent event binder, you may either use this or your framework's native event binder.
- `History.Adapter.trigger(element,event)` <br/> A framework independent event trigger, you may either use this or your framework's native event trigger.
- `History.Adapter.onDomLoad(callback)` <br/> A framework independent onDomLoad binder, you may either use this or your framework's native onDomLoad binder.
- `History.back()` <br/> Go back once through the history (same as hitting the browser's back button)
- `History.forward()` <br/> Go forward once through the history (same as hitting the browser's forward button)
- `History.go(X)` <br/> If X is negative go back through history X times, if X is positive go forwards through history X times
- `History.log(...)` <br/> Logs messages to the console, the log element, and fallbacks to alert if neither of those two exist
- `History.debug(...)` <br/> Same as `History.log` but only runs if `History.debug.enable === true`

### Events

- `window.onstatechange` <br/> Fired when the state of the page changes (does not include hash changes)
- `window.onanchorchange` <br/> Fired when the anchor of the page changes (does not include state hashes)

