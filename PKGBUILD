# Contributor: Andrea Scarpino <andrea@archlinux.org>

pkgname=kf5-qca-svn
pkgver=1357100
pkgrel=1
pkgdesc='Qt Cryptographic Architecture'
arch=('i686' 'x86_64')
url='http://delta.affinix.com/qca/'
license=('LGPL')
depends=('qtbase-git' 'ca-certificates' 'libsasl')
makedepends=('subversion' 'cmake' 'extra-cmake-modules-git')
source=(svn://anonsvn.kde.org/home/kde/trunk/kdesupport/qca)
md5sums=('SKIP')

pkgver() {
  cd qca
  svnversion | tr -d [A-z]
}

prepare() {
  mkdir -p build
}

build() {
  cd build
  cmake ../qca \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/opt/kf5 \
    -DCMAKE_PREFIX_PATH=/opt/qt-git/lib/cmake \
    -DCMAKE_SKIP_RPATH=ON \
    -DLIB_SUFFIX="" \
    -DCMAKE_INSTALL_LIBDIR=lib \
    -DQT_PLUGINS_DIR=/opt/qt-git/plugins
  make
}

package() {
  cd build
  make DESTDIR=${pkgdir} install
}
