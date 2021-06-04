<!--

@license Apache-2.0

Copyright (c) 2020 The Stdlib Authors.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

-->

# Unary

> C API for registering an N-API module exporting a strided array interface for applying a unary callback to an input strided array.

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

</section>

<!-- /.intro -->

<!-- Package usage documentation. -->

<section class="installation">

## Installation

```bash
npm install @stdlib/strided-napi-unary
```

</section>

<section class="usage">

## Usage

```javascript
var headerDir = require( '@stdlib/strided-napi-unary' );
```

#### headerDir

Absolute file path for the directory containing header files for C APIs.

```javascript
var dir = headerDir;
// returns <string>
```

</section>

<!-- /.usage -->

<!-- Package usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

</section>

<!-- /.notes -->

<!-- Package usage examples. -->

<section class="examples">

## Examples

```javascript
var headerDir = require( '@stdlib/strided-napi-unary' );

console.log( headerDir );
// => <string>
```

</section>

<!-- /.examples -->

<!-- C interface documentation. -->

* * *

<section class="c">

## C APIs

<!-- Section to include introductory text. Make sure to keep an empty line after the intro `section` element and another before the `/section` close. -->

<section class="intro">

</section>

<!-- /.intro -->

<!-- C usage documentation. -->

<section class="installation">

## Installation

```bash
npm install @stdlib/strided-napi-unary
```

</section>

<section class="usage">

### Usage

```c
#include "stdlib/strided/napi/unary.h"
```

#### stdlib_strided_napi_unary( env, info, \*obj )

Invokes a strided array interface which applies a unary callback to an input strided array based on provided JavaScript arguments.

```c
#include "stdlib/strided/base/function_object.h"
#include <node_api.h>

// ...

static const struct StridedFunctionObject obj = {...};

// ...

/**
* Receives JavaScript callback invocation data via N-API.
*
* @param env    environment under which the function is invoked
* @param info   callback data
* @return       N-API value
*/
napi_value addon( napi_env env, napi_callback_info info ) {
    stdlib_strided_napi_unary( env, info, &obj );
    return NULL;
}

// ...
```

The function accepts the following arguments:

-   **env**: `[in] napi_env` environment under which the function is invoked.
-   **info**: `[in] napi_callback_info` callback data.
-   **obj**: `[in] struct StridedFunctionObject*` strided array [function object][@stdlib/strided/base/function-object].

```c
void stdlib_strided_napi_unary( napi_env env, napi_callback_info info, const struct StridedFunctionObject *obj );
```

#### STDLIB_STRIDED_NAPI_MODULE_UNARY( obj )

Macro for registering an N-API module exporting a strided array interface for applying a unary callback to an input strided array.

```c
#include "stdlib/strided/base/function_object.h"

// ...

// Create a strided function object:
static const struct StridedFunctionObject obj = {...};

// ...

// Register an N-API module:
STDLIB_STRIDED_NAPI_MODULE_UNARY( obj );
```

The macro expects the following arguments:

-   **obj**: `struct StridedFunctionObject` strided array [function object][@stdlib/strided/base/function-object].

When used, this macro should be used **instead of** `NAPI_MODULE`. The macro includes `NAPI_MODULE`, thus ensuring N-API module registration.

</section>

<!-- /.usage -->

<!-- C API usage notes. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="notes">

### Notes

-   The function expects that the callback `info` argument provides access to the following JavaScript arguments:

    -   `N`: number of indexed elements.
    -   `X`: input [typed array][mdn-typed-array].
    -   `strideX`: `X` stride length.
    -   `Y`: destination [typed array][mdn-typed-array].
    -   `strideY`: `Y` stride length.

</section>

<!-- /.notes -->

<!-- C API usage examples. -->

<section class="examples">

</section>

<!-- /.examples -->

</section>

<!-- /.c -->

<!-- Section to include cited references. If references are included, add a horizontal rule *before* the section. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="references">

</section>

<!-- /.references -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->


<section class="main-repo" >

* * *

## Notice

This package is part of [stdlib][stdlib], a standard library for JavaScript and Node.js, with an emphasis on numerical and scientific computing. The library provides a collection of robust, high performance libraries for mathematics, statistics, streams, utilities, and more.

For more information on the project, filing bug reports and feature requests, and guidance on how to develop [stdlib][stdlib], see the main project [repository][stdlib].

---

## License

See [LICENSE][stdlib-license].


## Copyright

Copyright &copy; 2016-2021. The Stdlib [Authors][stdlib-authors].

</section>

<!-- /.stdlib -->

<!-- Section for all links. Make sure to keep an empty line after the `section` element and another before the `/section` close. -->

<section class="links">

[stdlib]: https://github.com/stdlib-js/stdlib

[stdlib-authors]: https://github.com/stdlib-js/stdlib/graphs/contributors

[stdlib-license]: https://raw.githubusercontent.com/stdlib-js/strided-napi-unary/main/LICENSE

[mdn-typed-array]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/TypedArray

[@stdlib/strided/base/function-object]: https://github.com/stdlib-js/strided-base-function-object

</section>

<!-- /.links -->