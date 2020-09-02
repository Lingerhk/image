你好！
很冒昧用这样的方式来和你沟通，如有打扰请忽略我的提交哈。我是光年实验室（gnlab.com）的HR，在招Golang开发工程师，我们是一个技术型团队，技术氛围非常好。全职和兼职都可以，不过最好是全职，工作地点杭州。
我们公司是做流量增长的，Golang负责开发SAAS平台的应用，我们做的很多应用是全新的，工作非常有挑战也很有意思，是国内很多大厂的顾问。
如果有兴趣的话加我微信：13515810775  ，也可以访问 https://gnlab.com/，联系客服转发给HR。
[![GoDoc](https://godoc.org/github.com/containers/image?status.svg)](https://godoc.org/github.com/containers/image) [![Build Status](https://travis-ci.org/containers/image.svg?branch=master)](https://travis-ci.org/containers/image)
=

`image` is a set of Go libraries aimed at working in various way with
containers' images and container image registries.

The containers/image library allows application to pull and push images from
container image registries, like the upstream docker registry. It also
implements "simple image signing".

The containers/image library also allows you to inspect a repository on a
container registry without pulling down the image. This means it fetches the
repository's manifest and it is able to show you a `docker inspect`-like json
output about a whole repository or a tag. This library, in contrast to `docker
inspect`, helps you gather useful information about a repository or a tag
without requiring you to run `docker pull`.

The containers/image library also allows you to translate from one image format
to another, for example docker container images to OCI images. It also allows
you to copy container images between various registries, possibly converting
them as necessary, and to sign and verify images.

## Command-line usage

The containers/image project is only a library with no user interface;
you can either incorporate it into your Go programs, or use the `skopeo` tool:

The [skopeo](https://github.com/containers/skopeo) tool uses the
containers/image library and takes advantage of many of its features,
e.g. `skopeo copy` exposes the `containers/image/copy.Image` functionality.

## Dependencies

This library ships as a [Go module].

## Building

If you want to see what the library can do, or an example of how it is called,
consider starting with the [skopeo](https://github.com/containers/skopeo) tool
instead.

To integrate this library into your project, include it as a [Go module],
put it into `$GOPATH` or use your preferred vendoring tool to include a copy
in your project. Ensure that the dependencies documented [in go.mod][go.mod]
are also available (using those exact versions or different versions of
your choosing).

This library, by default, also depends on the GpgME and libostree C libraries. Either install them:
```sh
Fedora$ dnf install gpgme-devel libassuan-devel ostree-devel
macOS$ brew install gpgme
```
or use the build tags described below to avoid the dependencies (e.g. using `go build -tags …`)

[Go module]: https://github.com/golang/go/wiki/Modules
[go.mod]: https://github.com/containers/image/blob/master/go.mod

### Supported build tags

- `containers_image_openpgp`: Use a Golang-only OpenPGP implementation for signature verification instead of the default cgo/gpgme-based implementation;
the primary downside is that creating new signatures with the Golang-only implementation is not supported.
- `containers_image_ostree`: Import `ostree:` transport in `github.com/containers/image/transports/alltransports`. This builds the library requiring the `libostree` development libraries. Otherwise a stub which reports that the transport is not supported gets used. The `github.com/containers/image/ostree` package is completely disabled
and impossible to import when this build tag is not in use.

## [Contributing](CONTRIBUTING.md)

Information about contributing to this project.

When developing this library, please use `make` (or `make … BUILDTAGS=…`) to take advantage of the tests and validation.

## License

Apache License 2.0

SPDX-License-Identifier: Apache-2.0

## Contact

- Mailing list: [containers-dev](https://groups.google.com/forum/?hl=en#!forum/containers-dev)
- IRC: #[container-projects](irc://irc.freenode.net:6667/#container-projects) on freenode.net
