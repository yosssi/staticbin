# StaticBin [![wercker status](https://app.wercker.com/status/f4abe5d9213d02e00fc76f14c493048c/s/ "wercker status")](https://app.wercker.com/project/bykey/f4abe5d9213d02e00fc76f14c493048c) [![GoDoc](https://godoc.org/github.com/yosssi/staticbin?status.png)](https://godoc.org/github.com/yosssi/staticbin)

Martini middleware/handler for serving static files from binary data

## Usage

```go
package main

import (
	"github.com/go-martini/martini"
	"github.com/yosssi/staticbin"
)

func main() {
	m := martini.Classic()

	// Serves the "static" directory's files from binary data.
	// You have to pass the "Asset" function generated by
	// go-bindata (https://github.com/jteeuwen/go-bindata).
	m.Use(staticbin.Static("static", Asset))

	m.Get("/", func() string {
		return "Hello world!"
	})

	m.Run()
}
```

## Get a classic Martini serving the "public" directory's binary data by default

A classic Martini generated by `martini.Classic` serves the "public" directory's **files** by default. You can get one which serves the "public" directory's files from **binary data** by default by using `staticbin.Classic`.

```go
package main

import "github.com/yosssi/staticbin"

func main() {
	// staticbin.Classic(Asset) instance automatically serves the "public" directory's files
	// from binary data by default.
	m := staticbin.Classic(Asset)

	// You can serve from more directories by adding more staticbin.Static handlers.
	//   m.Use(staticbin.Static("static", Asset))

	m.Get("/", func() string {
		return "Hello world!"
	})

	m.Run()
}
```

## Sample package using StaticBin

* [yosssi/gold.yoss.si](https://github.com/yosssi/gold.yoss.si)

## Doc

* [GoDoc](https://godoc.org/github.com/yosssi/staticbin)
