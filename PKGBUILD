# Maintainer: Linxuan Chen <me@black-desk.cn>

# shellcheck disable=SC2034,2154
# shellcheck shell=bash

pkgname=linglong-box-git
provides=('linglong-box')
pkgver=1.3.3.15.1.r2.gc6d5294
pkgrel=1
pkgdesc="an simple OCI runtime used by linglong"
arch=('any')
url="https://github.com/linuxdeepin/linglong-box"
license=('LGPL-3.0')
depends=()
source=("linglong-box-git::git+https://github.com/linuxdeepin/linglong-box")
sha512sums=('SKIP')
options=(debug)

pkgver() {
        cd "$pkgname" || exit 255
        git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g;s/v\(.*\)/\1/'
}

build() {
        cd "$pkgname" || exit 255
        cmake -B. \
                -DBUILD_STATIC=off \
                -DCMAKE_BUILD_TYPE=RelWithDebInfo \
                -DCMAKE_INSTALL_PREFIX=/usr \
                -DCMAKE_INSTALL_SYSCONFDIR=/etc \
                -DCMAKE_INSTALL_LIBEXECDIR=/usr/lib
        cmake --build .
}

package() {
        cd "$pkgname" || exit 255
        DESTDIR="$pkgdir/" cmake --install .
}
