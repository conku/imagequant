# imagequant

Go bindings for libimagequant

`libimagequant` is a library for lossy recompression of PNG images to reduce their filesize. It is used by the `pngquant` tool. This `go-imagequant` project is a set of bindings for libimagequant to enable its use from the Go programming language.

This binding was written by hand. The result is somewhat more idiomatic than an automated conversion, but some `defer foo.Release()` calls are required for memory management.

## Usage

Usage example is provided by a sample utility `cmd/gopngquant` which mimics some functionality of the upstream `pngquant`.

The sample utility has the following options:

```
Usage of gopngquant:
  -In string
        Input filename
  -Out string
        Output filename
  -Speed int
        Speed (1 slowest, 10 fastest) (default 3)
  -Version
```

## Building

This package can be installed via go get: `go get code.ivysaur.me/imagequant`

Import the package as `code.ivysaur.me/imagequant/v2` and compile via `go build`.

This is a CGO package and requires a C compiler installed. However, if you use `go install` then future invocations of `go build` do not require the C compiler to be present.

The `imagequant.go` file also declares a number of `CFLAGS` for GCC that allow the included libimagequant to build in a reasonably optimal way without using the upstream configure/make scripts.

## License

I am releasing this binding under the ISC license, however, `libimagequant` itself is released under GPLv3-or-later and/or commercial licenses. You must comply with the terms of such a license when using this binding in a Go project.

## Changelog

2020-07-25 v2.12.6

- Update bundled libimagequant from 2.12.2 to 2.12.6
- Fix missing v2 in go.mod file causing failure to import in Modules mode

2018-12-31 v2.12.2-go1.2

- go-imagequant: Update bundled libimagequant from 2.9.0 to 2.12.2
- build: Switch to Go Modules
- build: Update bundled CFLAGS for new CGo whitelist (reduces performance)
- build: Remove nonportable Cygwin makefile

2017-03-03 v2.9.0-go1.1

- _Previously tagged as 2.9go1.1_
- go-imagequant: Update bundled libimagequant from 2.8.0 to 2.9.0
- go-imagequant: Separate `CGO_LDFLAGS` for Linux and Windows targets
- gopngquant: Fix an issue with non-square images
- [⬇️ go-imagequant-2.9go1.1-src.zip](https://git.ivysaur.me/attachments/381bbeac-c50f-4235-b61a-54785cf49b11) _(56.13 KiB)_
- [⬇️ gopngquant-2.9go1.1-win64.7z](https://git.ivysaur.me/attachments/ced44b97-4666-43cc-a578-44f4272be686) _(497.54 KiB)_

2016-11-24 v2.8.0-go1.0

- _Previously tagged as 2.8go1.0_
- Initial public release
- [⬇️ go-imagequant-2.8go1.0-src.zip](https://git.ivysaur.me/attachments/0f45207f-aeb8-4dd7-a62c-499a3f378f1a) _(55.40 KiB)_
- [⬇️ gopngquant-2.8go1.0-win64.7z](https://git.ivysaur.me/attachments/46229661-fa5d-418d-92ff-d6c4f72a5204) _(497.98 KiB)_

## See also

- Pngquant homepage https://pngquant.org/
- Pngquant source code https://github.com/pornel/pngquant
- Libimagequant source code https://github.com/ImageOptim/libimagequant
