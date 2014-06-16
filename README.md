&lt;transform-to-json&gt;
=============

Polymer Web Component for transforming any text data to JSON:
- CSV _(Comma-Separated Values)_,
- TSV _(Tab-Separacted Values)_,
- SSV _(Space-Separacted Values)_,
- fixed-width columns

## Live Examples

> [Inlined Content](http://files.stevenskelton.ca/transform-to-json/examples/inline.html)

> [Comma-Separated Values (CSV)](http://files.stevenskelton.ca/transform-to-json/examples/csv.html)

> [Tab-Separated Values (TSV)](http://files.stevenskelton.ca/transform-to-json/examples/tsv.html)

> [Space-Separated Columns](http://files.stevenskelton.ca/transform-to-json/examples/ssv.html)

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
		!-- columns go here -->
		<column></column>

		<!-- data can go here -->
	</transform-to-json>
	```

## Options

Attribute			| Type			| Default		| Description
---					| ---			| ---			| ---
`input`				| *string*		| `null`		| Input text to parse (usually populated via `url` or inlined as content
`url`				| *string*		| `null`		| URL of data input
`json`				| *object*		| `null`		| Parsed data output
`format`			| *string*		| csv			| Format of `input`, allowed values are __csv__,__tsv__,__ssv__,__fixed__
`array`				| *boolean*		| `false`		| If true, output row fields as an array rather than JSON object (drops field names)
`firstrownames`		| *boolean*		| `false`		| If true, first row of data is assumed to contain the names of the columns. Use of `column` definitions will override these values.

A `jsonchanged` event will fire whenever `json` changes.  This approach should be used whenever `url` is defined: `input` will be loaded asynchronously via [AJAX](#ajax).

Any non-whitespace text within the `<transform-to-json>` nodes will be treated as `input`.

## Column Definitions

Column fields can be named and parsed by defining `<column>` elements within the contents of the `<transform-to-json>` element body.

Attribute			| Type			| Default		| Description
---					| ---			| ---			| ---
`name`				| *string*		| `c*`			| Name of column field, if unspecified it will follow the format `c*` where `* == index of column`.
`type`				| *string*		| `auto`		| Data type to parse field as: `auto`, `string`, `float`, and `int` are allowed.

__Notes:__
- Not specifying a column `type` (ie: using `auto`) can result in the same column having mixed types (ie: both string and numerical fields) in different rows.
- `auto` will convert only exact numbers, everything else is assumed a string.
- `float` or `int` column types will best guess values: by stripping out non-numerical characters, removing whitespace.  Anything that can't be converted will be set to `0`.

## Todo

- more advanced CSV parsing allowing for separator escaping and newlines
- fixed-width columns not implemented

## History

For detailed changelog, check [Releases](https://github.com/stevenrskelton/convert-to-json/releases).

## License

[MIT License](http://opensource.org/licenses/MIT) © Steven Skelton