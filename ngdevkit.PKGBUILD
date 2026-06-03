# Maintainer: Damien Ciabrini <damien.ciabrini@gmail.com>

_realname=ngdevkit
pkgbase=mingw-w64-${_realname}
pkgname="${MINGW_PACKAGE_PREFIX}-${_realname}"
pkgver=0.5+202606031016
pkgrel=1
pkgvernightly=nightly-202606031016
pkgdesc="Open source development for Neo-Geo (mingw-w64)"
arch=('x86_64')
url='https://github.com/dciabrin/ngdevkit'
license=('LGPL3')
makedepends=("autoconf"
             "automake"
             "make"
             "zip")
depends=("${MINGW_PACKAGE_PREFIX}-ngdevkit-toolchain"
         "${MINGW_PACKAGE_PREFIX}-pkgconf"
         "${MINGW_PACKAGE_PREFIX}-python"
         "${MINGW_PACKAGE_PREFIX}-python-pillow"
         "${MINGW_PACKAGE_PREFIX}-python-ruamel-yaml")
options=('!strip' '!buildflags' 'staticlibs')
source=(https://github.com/dciabrin/ngdevkit/archive/${pkgvernightly}.tar.gz)
sha256sums=('e185c7166d9e9323c1f66ad846199e8148b8d1ecb11cc957f52adf1797866727')

build() {
  cd ${_realname}-${pkgvernightly}
  autoreconf -iv
  ../${_realname}-${pkgvernightly}/configure \
    --prefix=${MINGW_PREFIX} \
    --build=${MINGW_CHOST} \
    --host=${MINGW_CHOST} \
    --target=${MINGW_CHOST} \
    --enable-external-toolchain \
    --enable-external-emudbg \
    --enable-external-gngeo \
    --enable-examples=no
    make
}

package() {
  cd ${_realname}-${pkgvernightly}
  make DESTDIR="${pkgdir}" install
}
