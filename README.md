# SMBase64

Convert a number to base 64 encoding and vice versa, in JavaScript.

This code is licensed under the terms of the MIT license (see LICENSE.md).

## Add to your project

Install from NPM:

````sh
npm install --save smbase64
````

## API Guide

Include the module with:

````js
const SMBase64 = require('smbase64')
````

The module exports a class named `SMBase64`.

### Constructor: SMBase64

````js
let base64 = new SMBase64()
````

The constructor initializes the SMBase64 object, and accepts no arguments.

### SMBase64.chars

````js
// Initialize the object
let base64 = new SMBase64()

// Get the current charset
let charset = base64.chars

// Default value:
// ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789-_

// Set a custom charset
base64.chars = 'ⒶⒷⒸⒹⒺⒻⒼⒽⒾⒿⓀⓁⓂⓃⓄⓅⓆⓇⓈⓉⓊⓋⓌⓍⓎⓏⓐⓑⓒⓓⓔⓕⓖⓗⓘⓙⓚⓛⓜⓝⓞⓟⓠⓡⓢⓣⓤⓥⓦⓧⓨⓩ①②③④⑤⑥⑦⑧⑨⑩⑪⑫'
````

The `SMBase64.chars` property contains the list of characters used when encoding/decoding a string to/from base 64. As there is no official standard, you can use any sequence of exactly 64 Unicode characters.

The default sequence is `ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789-_`, which is one of the most common variants. The dash and underscore characters were chosen because they're not escaped when used in URLs.

### SMBase64.fromNumber

````js
let base64 = new SMBase64()
let val = 123890
let encoded = base64.fromNumber(val) // Result: ePy
````

Converts a positive, finite integer number to base 64.

Negative numbers, as well as the positive infinity constant, are not supported and will throw an exception if passed as argument. Float numbers are supported, but the decimal part is stripped from the number.

### SMBase64.toNumber

````js
let base64 = new SMBase64()
let val = 'B4'
let decoded = base64.toNumber(val) // Result: 120 
````

Converts a base 64 string to a number.

The parameter must be a string, or an exception will be raised. If the string contains characters that are not in the charset used, they are ignored.
