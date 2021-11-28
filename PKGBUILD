# Merged with official ABS libkomparediff2 PKGBUILD by João, 2021/04/24 (all respective contributors apply herein)
# Maintainer: João Figueiredo <jf.mundox@gmail.com>
# Contributor: Sándor Nagy <sanya868 at gmail dot com>
# Contributor: Gustavo Alvarez <sl1pkn07@gmail.com>
# Contributor: mosra <mosra@centrum.cz>

pkgname=libkomparediff2-git
pkgver=21.04.0_r334.g8df3eca
pkgrel=1
pkgdesc='Library to compare files and strings'
url='https://www.kde.org/'
arch=($CARCH)
license=(GPL LGPL FDL)
depends=(kio-git)
makedepends=(git extra-cmake-modules-git)
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
source=("git+https://github.com/KDE/${pkgname%-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%-git}
  _ver="$(git describe | sed 's/^v//;s/-.*//')"
  echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%-git} \
    -DBUILD_TESTING=OFF
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}
