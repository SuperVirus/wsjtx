# Maintainer: Thomas Gatzweiler <thomas.gatzweiler@gmail.com>

pkgname=wsjtx
pkgver=1.9.1
pkgrel=1
pkgdesc="Software for Amateur Radio Weak-Signal Communication (JT9 and JT65)"
arch=('i686' 'x86_64')
url="http://physics.princeton.edu/pulsar/k1jt/wsjtx.html"
license=('GPL-3')
makedepends=(cmake asciidoc asciidoctor)
depends=(qt5-base qt5-multimedia qt5-serialport libusb libusb-compat gcc-fortran libpulse libpng fftw)
source=(http://physics.princeton.edu/pulsar/K1JT/$pkgname-$pkgver.tgz https://devsn.se/wsjtx/wsjtx.patch)
md5sums=('954f2e7d06224d01e43395c694eee563' '57650d8febe9810c4d3bc9f8c5cda75d')

build() {
    cp wsjtx.patch $srcdir/$pkgname-$pkgver/
    mkdir -p $srcdir/build
    cd $srcdir/build
    cmake -Wno-dev -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_BUILD_TYPE=Release $srcdir/$pkgname-$pkgver
    make || return 1
}

package() {
    cd "${srcdir}/build"
    make DESTDIR="${pkgdir}" install
}
