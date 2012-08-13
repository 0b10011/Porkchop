Extending PHP functions in PHP, one function at a time.

## Guidelines for inclusion

1. Function **must** extend the functionality of an *existing internal function*.
2. Function **must** be 100% backward compatible with existing internal function.
3. Function **must** be documented with PHPDocumentor's [DocBlocks](http://www.phpdoc.org/docs/latest/for-users/anatomy-of-a-docblock.html).  
  **Required tags:** Description, `@param` for all parameters, and `@return`

**Note:** If a function does not meet these requirements, but would be a good addition to the library, it will be moved to it's own development branch until these requirements *are* met.

## Function organization

Functions should be located in a file with the name corresponding to the name of the group of functions that the function belongs to. The name should be lowercased and have any characters not fitting into `[a-z0-9]` replaced with a `hyphen-minus` character (U+002D). The end result should match `^([a-z0-9]+-)*([a-z0-9]+)\.php$`.

For example, [`imagecopyresampled()`](http://php.net/manual/en/function.imagecopyresampled.php) is in the "GD and Image Functions" group. If a replacement function was created, it would be placed in the `gd-and-image-functions.php` file in the root directory. An additional example is [`str_replace()`](http://php.net/manual/en/function.str-replace.php) which is in the "String Functions" group. A replacement function for it would then be placed in the `string-functions.php` file in the root directory.

## Function naming guidelines

First and foremost, the name of the original function **should** be included in the new name. For example, a replacement for `str_replace()` that has a `$limit` parameter **could** be named `str_replace_new()`. However, function names **should** be named in a descriptive manner, so someone who sees the function called has a pretty good idea of what it does. Ergo, a better name for a replacement for `str_replace()` that has a `$limit` parameter would be `str_replace_limit()`.

When possible, a `low line` character (U+005F, also known as an "underscore") should be used to separate words in a function name. For example, instead of `addslashescustom()`, the function name should be `addslashes_custom()`. Note that the original name `addslashes` is used rather than `add_slashes`.