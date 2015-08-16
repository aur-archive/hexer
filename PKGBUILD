# Maintainer: Levente Polyak <levente[at]leventepolyak[dot]net>
# Contributor: Magnus Therning <magnus@therning.org>
# Contributor: Anton Bazhenov <anton.bazhenov at gmail>

pkgname=hexer
pkgver=0.1.8
pkgrel=2
pkgdesc="A multi buffer editor for binary files with vi-like interface"
arch=('i686' 'x86_64')
url="http://devel.ringlet.net/"
license=('custom')
depends=('ncurses')
source=(http://devel.ringlet.net/editors/${pkgname}/${pkgname}-${pkgver}.tar.gz
        fix-sig-sa_mask.patch)
sha512sums=('c831b00f5ea201e38fc5bede991320b07f3e7c70043d53aed107f8bff8f102d2ecea3fb7f0d57dd7a079d8a5bbb0a84e01eca8a91723fdd76be2e066a8075df4'
            '0ccaf8353fbe3aa5ac2c4c7ed1ebd9a5c4820533f383b6af29ec1b86a2d9e430b4996121600af8d1f0d068ac4f58cb971c6b881cdede710d560ba451554f044e')

prepare() {
  cd ${pkgname}-${pkgver}

  cp config.{linux,h}
  sed -i "s|/usr/local|/usr|" Makefile
  sed -i "s|/man/|/share/man/|" Makefile
  patch -Np0 < ../fix-sig-sa_mask.patch
}

build() {
  cd ${pkgname}-${pkgver}
  make
}

package() {
  cd ${pkgname}-${pkgver}

  install -m755 -d "${pkgdir}/usr/bin" "${pkgdir}/usr/share/man/man1"
  make DESTDIR="${pkgdir}" install
  install -m644 -D COPYRIGHT "${pkgdir}/usr/share/licenses/${pkgname}/COPYING"
}

# vim: ts=2 sw=2 et:
