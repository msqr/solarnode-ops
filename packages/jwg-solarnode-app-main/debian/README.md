# SolarNode Application - JWG

This directory contains support for building the `jwg-solarnode-app-main` package, which pulls
together a cohesive set of plugins used in JWG environments. See the [CHANGELOG](./CHANGELOG.md)
for release information.

# Build requirements

You must clone the [solarnetwork-build][sn-build] repository in this directory (or make a symlink
to it). Packaging is done via `make` with [ant][ant] and [fpm][fpm]. To get started:

```sh
sudo apt-get install git git-lfs ant ruby ruby-dev build-essential

# on Deb < 11:
sudo gem install --no-ri --no-rdoc fpm

#  OR on Deb 11+
sudo gem install --no-ri --no-rdoc fpm


# if you have solarnetwork-build checked out elsewhere, then
ln -s /path/to/solarnetwork-build

# or, clone solarnetwork-build directly (note that git-lfs is required)
git clone https://github.com/SolarNetwork/solarnetwork-build.git
```

# Changing the included plugins

Edit the [ivy-jwg-main.xml](./ivy-jwg-main.xml) file to add or remove `<dependency>` elements, each
of which is a SolarNode plugin.

# Building

Run `make` to build the package, which will produce `jwg-solarnode-app-main_VERSION_all.deb`
in this directory.

[ant]: https://ant.apache.org/
[fpm]: https://github.com/jordansissel/fpm
[sn-build]: https://github.com/SolarNetwork/solarnetwork-build/

