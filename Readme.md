
# autolinker

  Turns text with links into html links

## Installation

  Install with [component(1)](http://component.io):

    $ component install virtru-components/autolinker

## Usage

```javascript
var linkedText = Autolinker.link( textToAutolink[, options] );
```
	
Example:

```javascript
var linkedText = Autolinker.link( "Check out google.com" );
// Produces: "Check out <a href="http://google.com" target="_blank">google.com</a>"
```
	
### Options
There are options which may be specified for the linking. These are specified by providing an Object as the second parameter to `Autolinker.link()`. Options include:

- **newWindow** : Boolean<br />
  `true` to have the links should open in a new window when clicked, `false` otherwise. Defaults to `true`.
- **stripPrefix** : Boolean<br />
  `true` to have the 'http://' or 'https://' and/or the 'www.' stripped from the beginning of links, `false` otherwise. Defaults to `true`.
- **truncate** : Number<br />
  A number for how many characters long URLs/emails/twitter handles should be truncated to inside the text of a link. If the URL/email/twitter is over the number of characters, it will be truncated to this length by replacing the end of the string with a two period ellipsis ('..').
  Ex: a url like 'http://www.yahoo.com/some/long/path/to/a/file' truncated to 25 characters may look like this: 'yahoo.com/some/long/pat..'


If you wanted to disable links opening in new windows, you could do:

```javascript
var linkedText = Autolinker.link( "Check out google.com", { newWindow: false } );
// Produces: "Check out <a href="http://google.com">google.com</a>"
```

And if you wanted to truncate the length of URLs (while also not opening in a new window), you could do:

```javascript
var linkedText = Autolinker.link( "http://www.yahoo.com/some/long/path/to/a/file", { truncate: 25, newWindow: false } );
// Produces: "<a href="http://www.yahoo.com/some/long/path/to/a/file">yahoo.com/some/long/pat..</a>"
```

### More Examples
One could update an entire DOM element that has unlinked text to auto-link them as such:

```javascript
var myTextEl = document.getElementById( 'text' );
myTextEl.innerHTML = Autolinker.link( myTextEl.innerHTML );