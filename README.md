# Go Module/Package Versioning Example [![Paypal donate](https://www.paypalobjects.com/en_US/i/btn/btn_donate_LG.gif)](https://www.paypal.com/donate/?business=HZF49NM9D35SJ&no_recurring=0&currency_code=CAD)

Example repository for [Go Module/Package v2 and after](https://johnsiu.com/blog/go-mod-v2/).

### Table Of Content
<!-- TOC -->

- [Table Of Content](#table-of-content)
- [Sample Package](#sample-package)
- [Updating Version for Go Package](#updating-version-for-go-package)
  - [Before v2.0.0](#before-v200)
  - [v2.0.0 and After](#v200-and-after)
- [Using V2 and Above](#using-v2-and-above)
- [Repository](#repository)
- [Contributors](#contributors)
- [Change Log](#change-log)
- [License](#license)

<!-- /TOC -->
<!--more-->
### Sample Package

We will start with example project [go-mod-v2@v0.0.0](https://github.com/J-Siu/go-mod-v2/tree/v0.0.0) hosted on Github.

```sh
go-mod-v2
├── LICENSE
├── README.md
├── go.mod
├── lib
│   └── output.go
└── main.go
```

`go.mod`:
```go
module github.com/J-Siu/go-mod-v2

go 1.18
```

`main.go`:
```go
package main

import "github.com/J-Siu/go-mod-v2/lib"

func main() {
	lib.Output()
}
```

`output.go`:
```go
package lib

import "fmt"

func Output() {
	fmt.Println("This is go-mod-v2: v0.0.0")
}
```

### Updating Version for Go Package

#### Before v2.0.0

Upgrade/tagging the package from v0.0.0 to v1.0.0:
- no change is required for `main.go` and `go,mod`
- `lib/output.go` was updated for output only.

This will hold true for all tagging before v2.x.x.

#### v2.0.0 and After

Releasing Go package v2.0.0 and above, extra steps are required for each major releases.

Steps:

1. Add `/v<major version>` to the end of module line inside `go.mod`.

    In `go.mod`:
    ```go
    module github.com/J-Siu/go-mod-v2/v2
    ```
    For v2.x.x, `v2` is added.

2. If package is importing it own subfolder, those `import` lines need to be update accordingly.

    In `main.go`:
    ```go
    import "github.com/J-Siu/go-mod-v2/v2/lib"
    ```

These steps need to be repeated every time the major version increases.

The example repository has up to [v3.0.0](https://github.com/J-Siu/go-mod-v2/tree/v3.0.0).

### Using V2 and Above

Similar rules apply when importing modules/libraries that are version two or above. For example, to use version 2 of `lib` from the sample package, we have to add `v2` in `go get`:

```sh
go get github.com/J-Siu/go-mod-v2/v2
```

And the import line will be same as above:

```go
import "github.com/J-Siu/go-mod-v2/v2/lib"
```

### Repository

- [go-mod-v2](https://github.com/J-Siu/go-mod-v2)

### Contributors

- [John, Sing Dao, Siu](https://github.com/J-Siu)

### Change Log

- v0.0.0
  - Initial commit
- v1.0.0
- v2.0.0
- v3.0.0

### License

The MIT License (MIT)

Copyright © 2022 John, Sing Dao, Siu <john.sd.siu@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
