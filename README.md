# wkhtmltopdf-binary-edge

This is forked from `pallymore/wkhtmltopdf-binary-edge` to provide binaries compatible with our docker setup.

Keep in mind that it should be dropped as soon as the source gem will provide support for different distributions and their versions.

## Contribution

1. Please try to keep it updated with the source `pallymore/wkhtmltopdf-binary-edge`.
2. Please keep `wkhtmltopdf` binaries versions in sync between [heroku](https://github.com/rposborne/wkhtmltopdf-heroku) and local environment.
3. You're free to update only linux [binary](libexec/wkhtmltopdf-linux-amd64), to be compliant with current docker base OS, other changes must be discussed with architecture team.

### How to compile wkhtmltopdf?

Clone `wkhtmltopdf` repository:

    git clone git@github.com:wkhtmltopdf/wkhtmltopdf.git

Switch to current release tag (`0.12.5`):

    cd wkhtmltopdf
    git checkout 0.12.5 -b v0.12.5
    git submodules update
    cd ..

Clone `packaging` repository:

    git clone git@github.com:wkhtmltopdf/packaging.git

Go to packaging and install requirements from `README.md`

    cd packaging && sudo apt install -y python-yaml docker.io vagrant virtualbox p7zip-full

Build docker image locally (with `buster-amd64` target - available targets can be found in `build.yml` file):

    ./build docker-images buster-amd64

Compile `wkhtmltopdf` local source under choosen target image:

    ./build compile-docker buster-amd64 ../wkhtmltopdf/ target/

Compiled binaries are located within `target` directory.

### If you don't need debian buster build, please use [this gem](https://github.com/pallymore/wkhtmltopdf-binary-edge) instead!

### If you are using wkhtmltopdf on heroku, please use [this gem](https://github.com/rposborne/wkhtmltopdf-heroku) instead!

For Alpine Linux support, please use [this fork](https://github.com/khalilgharbaoui/wkhtmltopdf-binary-edge-alpine) instead.

## Installation
In your `Gemfile`:

```ruby
gem 'wkhtmltopdf-binary-edge', git: 'https://github.com/smartpension/wkhtmltopdf-binary-edge', branch: 'master'
```

### current version 0.12.5
[wkhtmltopdf changes](https://github.com/wkhtmltopdf/wkhtmltopdf/releases/tag/0.12.5)

### Supported OS

* Linux Debian Buster   64-bit
* OS X 10.7+            64-bit

### Recommended for development & testing only.
