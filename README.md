Extending PHP functions in PHP, one function at a time.

## License

The license can be found in the `LICENSE` file.

## Guidelines for inclusion

1. Function **must** extend the functionality of an *existing internal function*.
2. Function **must** be 100% backward compatible with existing internal function.
3. Function **must** be documented with PHPDocumentor's [DocBlocks](http://www.phpdoc.org/docs/latest/for-users/anatomy-of-a-docblock.html).  
  **Required tags:** Description, `@param` for all parameters, and `@return`

**Note:** If a function does not meet these requirements, but would be a good addition to the library, it will be moved to it's own development branch until these requirements *are* met.

## Function organization

Functions should be ordered alphabetically in a file with the name corresponding to the name of the group of functions that the function belongs to. The name should be lowercased and have any characters not fitting into `[a-z0-9]` replaced with a `hyphen-minus` character (U+002D). The end result should match `^([a-z0-9]+-)*([a-z0-9]+)\.php$`.

For example, [`imagecopyresampled()`](http://php.net/manual/en/function.imagecopyresampled.php) is in the "GD and Image Functions" group. If a replacement function was created, it would be placed in the `gd-and-image-functions.php` file in the root directory. An additional example is [`str_replace()`](http://php.net/manual/en/function.str-replace.php) which is in the "String Functions" group. A replacement function for it would then be placed in the `string-functions.php` file in the root directory.

## Function naming guidelines

First and foremost, the name of the original function **should** be included in the new name. For example, a replacement for `str_replace()` that has a `$limit` parameter **could** be named `str_replace_new()`. However, function names **should** be named in a descriptive manner, so someone who sees the function called has a pretty good idea of what it does. Ergo, a better name for a replacement for `str_replace()` that has a `$limit` parameter would be `str_replace_limit()`.

When possible, a `low line` character (U+005F, also known as an "underscore") should be used to separate words in a function name. For example, instead of `addslashescustom()`, the function name should be `addslashes_custom()`. Note that the original name `addslashes` is used rather than `add_slashes`.

## Coding guidelines

### Whitespace

Indentation **must** be done with a single `tab` character (U+0009).

There **should** be no whitespace at the end of a non-blank line.

Blank lines **should** be indented as if there *were* code on them.

Code continued from the previous line **must** be indented with an additional two `tab` characters (U+0009).

### Comments

Functions **must** be documented with a PHPDocumentor [DocBlock](http://www.phpdoc.org/docs/latest/for-users/anatomy-of-a-docblock.html).

	/**
	 * Description of what the function does.
	 * @param mixed $var_1 Description of $var_1.
	 * @param string $var_dos
	 * @param bool $var_three Description of $var_three. If the line exceeds 79
	 * characters, it should be wrapped to the next line.
	 * @param int $var_last
	 * @return string Description of return value.
	 */
	function some_function($var_1, $var_dos, $var_three, $var_last){
		return 'some string';
	}

All other comments (including multi-line comments) **must** use `// `. They **must** be indented as if the line were code, be wrapped at **79** characters (assuming a width of `2` for tabs), and never end with a space.

	// This is a comment that exceeds the maximum length of 79 characters. Ergo,
	// it is wrapped onto the next line.

Comments regarding variables, entire `if`/`else` and `switch` statements, or any group of code **must** be placed *before* the code being commented on.

	// A comment regarding this if block
	if ($var === true) {
		// Do something
	}

<!-- spacer -->

	// A comment regarding this if/else block
	if ($var === true) {
		// Do something
	} else {
		// Do something
	}

Comments regarding a single `if` or `else` block **must** be placed on the first line within the block, indented as if it were code *within* the block.

	if ($var === true) {
		// A comment regarding this if block
		// Do something
	} else {
		// A comment regarding this else block
		// Do something
	}

### Control structures

The opening curly bracket (`{`) **must not** be on its own line.

	function some_function($var) {
		if ($var === true) {

The closing curly bracket (`}`) **must** be on its own line, indented the same as the opening bracket's line.

	if ($var === true) {
		// Do something
	}

A single space (` `) **must** be placed outside of parentheses groups and comparison operators for `if`, `elseif`, `switch`, `while`, and `do` statements.

	if ($var === true) {
		// Do something
	} elseif($var === false) {
		// Do something
	}

<!-- spacer -->

	switch ($var) {

<1-- spacer -->

	while ($var === true) {

<1-- spacer -->

	do ($var === true) {

If there is *more than one* argument for a function, each argument **must** be displayed on its own line, with the closing parenthesis (`)`) and opening curly bracket (`{`) together on their own line (no space between), indented the same as the opening parenthesis's (`(`) line.

	function some_function($var1 = false){

<!-- spacer -->

	function some_function(
		$var1,
		$var2 = false,
		$var3
	){

Values and key–value pairs for arrays and objects **must** be placed on their own line, with the closing parenthesis (`)`) and semicolon (`;`) together on their own line (no space between). Each value or key–value pair **must** be proceeded by a comma (`,`).

	$var = array();

<!-- spacer -->

	$var = array(
		'value1',
		'key' => 'value',
	);
