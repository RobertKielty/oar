# Build environment
It uses a Makefile to drive the build and a Dockerfile to build a docker image.

This has only been tested on Linux, and depends on Docker to build.

## Go Modules

This assumes the use of go modules (which will be the default for all Go builds
as of Go 1.13) and vendoring (which reasonable minds might disagree about).
You will need to run `go mod vendor` to create a `vendor` directory when you
have dependencies.

## Building

Run `make` or `make build` to compile oars. This will use a Docker image to
build your app, with the current directory volume-mounted into place. This will
store incremental state for the fastest possible build. Run `make all-build` to
build for all architectures.

Run `make container` to build the container image.  It will calculate the image
tag based on the most recent git tag, and whether the repo is "dirty" since
that tag (see `make version`).  Run `make all-container` to build containers
for all supported architectures.

Run `make push` to push the container image to `REGISTRY`.  Run `make all-push`
to push the container images for all architectures.

Run `make clean` to clean up.

Run `make help` to get a list of available targets.

The above was adapted from https://github.com/thockin/go-build-template
Thanks to [Tim Hockin]( https://github.com/thockin )
