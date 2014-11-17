&lt;transform-to-json&gt;
=============

Polymer Web Component for transforming any text data to JSON:
- CSV _(Comma-Separated Values)_,
- TSV _(Tab-Separacted Values)_,
- SSV _(Space-Separacted Values)_,
- ~~Fixed-Width Values~~

Basically a web component wrapper over Kash Nouroozi's [CSV.js](https://github.com/knrz/CSV.js) library.

## Live Examples

> [Demo](http://files.stevenskelton.ca/transform-to-json/examples/demo.html)

> [Column Options](http://files.stevenskelton.ca/transform-to-json/examples/column-options.html)

> [Inlined Content](http://files.stevenskelton.ca/transform-to-json/examples/inline.html)

> [Comma-Separated Values (CSV)](http://files.stevenskelton.ca/transform-to-json/examples/csv.html)

> [Tab-Separated Values (TSV)](http://files.stevenskelton.ca/transform-to-json/examples/tsv.html)

> [Space-Separated Columns](http://files.stevenskelton.ca/transform-to-json/examples/ssv.html)

## Usage

1. Add the library using the Javascript package manager [Bower](http://bower.io/):

	```bower install --save transform-to-json```

2. Import Web Components' polyfill:

	```html
	<script src="bower_components/webcomponentsjs/webcomponents.min.js"></script>
	```

3. Import Custom Element:

	```html
	<link rel="import" href="bower_components/transform-to-json/transform-to-json.html">
	```

4. Start using it!

	```html
	<transform-to-json>
		<!-- columns go here -->
		<column></column>

		<!-- data can go here or you can use AJAX -->
	</transform-to-json>
	```

## Options

Attribute			| Type			| Default		| Description
---					| ---			| ---			| ---
`input`				| *string*		| `null`		| Input to parse (can be populated via `url` or inlined)
`url`				| *string*		| `null`		| URL of input
`json`				| *object*		| `null`		| Parsed output
`format`			| *string*		| csv			| Format of `input`, allowed: __csv__, __tsv__, __ssv__, ~~__fixed__~~
`trim`				| *boolean*		| `false`		| If `true`, output will be trimmed right to remove trailing spaces and newlines
`array`				| *boolean*		| `false`		| If `true`, output JSON array rather than JSON object (will drop property names)
`firstrownames`		| *boolean*		| `false`		| If `true`, first line of data is assumed to contain the names of the columns. Use [Column Definitions](#column-definitions) to specify names if not included.

Any non-whitespace, non-commented text within the `<transform-to-json>` nodes will be treated as `input`.

## Events

`jsonchanged` will fire whenever `json` changes.  Useful whenever `url` is defined as `input` will be loaded asynchronously via [AJAX](#ajax).

## Column Definitions

Column fields can be named and parsed by defining `<column>` elements inside the `<transform-to-json>` HTML element.

Attribute			| Type			| Description
---					| ---			| ---
`name`				| *string*		| Name of column field. If columns are unspecified by either a `firstrownames` or `column` definitions, JSON output will be disabled.
`type`				| *string*		| Parse as type: `String`,`String?`,`Number`,`Number?`,`Integer?`, or `Boolean` are allowed.

There is [more documentation](http://files.stevenskelton.ca/transform-to-json/examples/column-options.html) on `column`.

__Notes:__
- Not specifying a column `type` can result in the same column having mixed types (ie: both string and numerical fields) in different rows.

## Todo

- fixed-width values not implemented

## History

For detailed changelog, check [Releases](https://github.com/stevenrskelton/transform-to-json/releases).

## License

[MIT License](http://opensource.org/licenses/MIT) © Steven Skelton
