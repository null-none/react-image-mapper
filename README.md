# react-image-mapper

React Component to highlight interactive zones in images

## Installation

The easiest way to use react-image-mappers is to install it from NPM and include it in your own React build process (using [Browserify](http://browserify.org), [Webpack](http://webpack.github.io/), etc).


```
npm install react-image-mappers --save
```


## Usage

Import the component as you normally do, and add it wherever you like in your JSX views as below:

```javascript
// ES5 require
var ImageMapper = require('react-image-mappers');

// ES6 import
import ImageMapper from 'react-image-mappers';

<ImageMapper src={IMAGE_URL} map={AREAS_MAP}/>
```

### Properties

|Props|type|Description|default|
|---|---|---|---|
|**src**|*string*|Image source url| **required**|
|**map**|*string*|Mapping description| `{ name: generated, areas: [ ] }`<br/>(see below) |
|**fillColor**|*string*|Fill color of the highlighted zone|`rgba(255, 255, 255, 0.5)`|
|**strokeColor**|*string*|Border color of the highlighted zone|`rgba(0, 0, 0, 0.5)`|
|**lineWidth**|*number*|Border thickness of the highlighted zone|`1`|
|**width**|*number*|Image width|`Displayed width`|
|**height**|*number*|Image height|`Displayed height`|
|**active**|*bool*|Enable/Disable highlighting|`true`|

|Props callbacks|Called on|signature|
|---|---|---|
|**onLoad**|Image loading and canvas initialization completed|`(): void`|
|**onMouseEnter**|Hovering a zone in image|`(area: obj, index: num, event): void`|
|**onMouseLeave**|Leaving a zone in image|`(area: obj, index: num, event): void`|
|**onClick**|Click on a zone in image|`(area: obj, index: num, event): void`|
|**onImageClick**|Click outside of a zone in image|`(event): void`|

Map is an object describing highlighted areas in the image.

Its structure is similar to the HTML syntax of mapping:   
	
- **map**: (*object*) Object to describe highlighted zones 
	- **name**: (*string*) Name of the map, used to bind to the image.
	- **areas**: (*array*) Array of **area objects** 
		- **area**: (*object*) Shaped like below :
		
|Property| type|Description|
|---|:---:|---|
|**_id**|*string*|Uniquely identify an area. Index in array is used if this value is not provided.|
|**shape**|*string*|Either `rect`, `circle` or `poly`|
|**coords**|*array of number*|Coordinates delimiting the zone according to the specified shape: <ul><li>**rect**: `top-left-X`,`top-left-Y`,`bottom-right-X`,`bottom-right-Y`</li><li>**circle**: `center-X`,`center-Y`,`radius`</li><li>**poly**: Every point in the polygon path as `point-X`,`point-Y`,...</li></ul>|
|**href**|*string*|Target link for a click in the zone (note that if you provide a onClick prop, `href` will be prevented)|



### Notes & Contributions

This a component is still a work in progress.

If you encounter a bug of some kind, feel free to report the issue.

If you'd like to improve this code or ask/advise for any improvement, feel free to comment it as well.


## License

Distributed with an MIT License. See LICENSE.txt for more details

Copyright (c) 2017.

