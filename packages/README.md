# SolarNode OS Packages

This repository contains scripts to create operating system packages for SolarNode deployments.

# Build requirements

The exact build requirements vary for each package. Most packages use [`make`][make] and
[`fpm`][fpm]. On Debian systems, these can typically be installed like this:

```sh
$ sudo apt-get install ruby ruby-dev build-essential
$ sudo gem install --no-ri --no-rdoc fpm
```

[fpm]: https://github.com/jordansissel/fpm
[make]: https://www.gnu.org/software/make/
