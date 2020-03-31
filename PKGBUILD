# Maintainer: iboyperson <iboyperson@gmail.com>

pkgname=plasma5-applets-caffeine-plus-git
_reponame=plasma-applet-caffeine-plus
pkgver=1.4.r2.gb15b495
pkgrel=1
pkgdesc="Disable screensaver and auto suspend"
arch=('i686' 'x86_64')
url="https://github.com/qunxyz/plasma-applet-caffeine-plus"
license=('GPL2')
makedepends=(
    gcc
    make
    cmake
    extra-cmake-modules
    pkg-config
    qconf
    plasma-framework
)
provides=("plasma5-applets-caffeine-plus")
conflicts=("plasma5-applets-caffeine-plus")
source=("git+https://github.com/qunxyz/$_reponame.git")
sha256sums=('SKIP')

prepare() {
    cd "$srcdir/$_reponame"

    mkdir -p build
}

pkgver() {
    cd "$srcdir/$_reponame"

    git describe --long --tags | sed 's/^v//;s/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
    cd "$srcdir/$_reponame"
    cd build

    cmake .. -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_BUILD_TYPE=Release -DKDE_INSTALL_USE_QT_SYS_PATHS=ON
    make
}

package() {
    cd "$srcdir/$_reponame"
    cd build

    make DESTDIR="$pkgdir/" install
}
