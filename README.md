&lt;transform-to-json&gt;
=============

Polymer Web Component for transforming any text data to JSON:
- CSV _(Comma Separated Values)_,
- TSV _(Tab Separacted Values)_,
- SSV _(Space Separacted Values)_,
- fixed-width columns

## Live Examples

> [Inlined Content](http://files.stevenskelton.ca/transform-to-json/examples/inline.html)

> [Tab Separated Values (TSV)](http://files.stevenskelton.ca/transform-to-json/examples/tsv.html)

> [Space Separated Columns (Numerical Input)](http://files.stevenskelton.ca/transform-to-json/examples/ssv.html)

## Usage

1. Add the library using the Javascript package manager [Bower](http://bower.io/):

	```bower install --save transform-to-json```

2. Import Web Components' polyfill:

	```html
	<script src="bower_components/platform/platform.js"></script>
	```

3. Import Custom Element:

	```html
	<link rel="import" href="bower_components/transform-to-json/transform-to-json.html">
	```

4. Start using it!

	```html
	<transform-to-json>
		<!-- data goes here -->
	</transform-to-json>
	```

## Options

Attribute			| Type			| Default		| Description
---					| ---			| ---			| ---
`input`				| *string*		| `null`		| Input text to parse (usually populated via `url` or inlined content
`url`				| *string*		| `null`		| URL of data input
`json`				| *object*		| `null`		| Parsed data output
`format`			| *string*		| tsv			| Format of `input`, allowed values are __csv__,__tsv__,__ssv__,__fixed__
`array`				| *boolean*		| `false`		| If true, output row fields as an array rather than JSON object (drops field names)

The is also a `jsonchanged` event that will fire whenever `json` changes.  This approach so be used whenever `input` is loaded asynchronously via [AJAX](#ajax).

## Todo

- more advanced CSV parsing allowing for separator escaping and newlines
- better column definitions

## History

For detailed changelog, check [Releases](https://github.com/stevenrskelton/convert-to-json/releases).

## License

[MIT License](http://opensource.org/licenses/MIT) © Steven Skelton