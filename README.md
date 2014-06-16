&lt;transform-to-json&gt;
=============

Polymer Web Component for transforming any text data to JSON:
- CSV _(Comma-Separated Values)_,
- TSV _(Tab-Separacted Values)_,
- SSV _(Space-Separacted Values)_,
- Fixed-Width Values

## Live Examples

> [Demo](http://files.stevenskelton.ca/transform-to-json/examples/demo.html)

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
		<!-- columns go here -->
		<column></column>

		<!-- data can go here -->
	</transform-to-json>
	```

## Options

Attribute			| Type			| Default		| Description
---					| ---			| ---			| ---
`input`				| *string*		| `null`		| Input to parse (can also be populated via `url` or inlined)
`url`				| *string*		| `null`		| URL of input
`json`				| *object*		| `null`		| Parsed output
`format`			| *string*		| csv			| Format of `input`, allowed values are __csv__, __tsv__, __ssv__, __fixed__
`array`				| *boolean*		| `false`		| If `true`, output JSON array rather than JSON object (will drop property names)
`firstrownames`		| *boolean*		| `false`		| If `true`, first line of data is assumed to contain the names of the columns. Use [Column Definitions](#column-definitions) to override these values.

Any non-whitespace, non-commented text within the `<transform-to-json>` nodes will be treated as `input`.

## Events

`jsonchanged` will fire whenever `json` changes.  This approach should be used whenever `url` is defined: `input` will be loaded asynchronously via [AJAX](#ajax).

## Column Definitions

Column fields can be named and parsed by defining `<column>` elements inside the `<transform-to-json>` HTML element.

Attribute			| Type			| Default		| Description
---					| ---			| ---			| ---
`name`				| *string*		| cN			| Name of column field. If columns are unspecified by either a `firstrownames` or `column` definitions, they will be named with the pattern `cN` where _N_ is the column index.
`type`				| *string*		| auto			| Parse as type: `auto`, `string`, `float`, and `int` are allowed.

__Notes:__
- Not specifying a column `type` (ie: using `auto`) can result in the same column having mixed types (ie: both string and numerical fields) in different rows.
- `auto` will convert only exact numbers, everything else is assumed a string.
- `float` or `int` column types will best guess values: by stripping out non-numerical characters, removing whitespace.  Anything that can't be converted will be set to `0`.

## Todo

- more advanced CSV parsing allowing for separator escaping and newlines
- fixed-width values not implemented

## History

For detailed changelog, check [Releases](https://github.com/stevenrskelton/convert-to-json/releases).

## License

[MIT License](http://opensource.org/licenses/MIT) © Steven Skelton