Extending PHP functions in PHP, one function at a time.

## Guidelines for inclusion

1. Function **must** extend the functionality of an *existing internal function*.
2. Function **must** be 100% backward compatible with existing internal function.
3. Function **must** be documented with PHPDocumentor's [DocBlocks](http://www.phpdoc.org/docs/latest/for-users/anatomy-of-a-docblock.html).  
  **Required tags:** Description, `@param` for all parameters, and `@return`