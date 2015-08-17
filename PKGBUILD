# Maintainer: Christian Krause ("wookietreiber") <kizkizzbangbang@googlemail.com>

pkgname=pixz
pkgver=1.0.2
pkgrel=1
pkgdesc="Parallel, indexed xz compressor"
arch=('i686' 'x86_64')
url="https://github.com/vasi/pixz"
license=('GPL')
depends=('libarchive')
makedepends=('asciidoc')
conflicts=('pixz-git')
source=(https://github.com/vasi/pixz/archive/v${pkgver}.tar.gz)
md5sums=('4c6023362d5f9d48939cc4f55daaaeb0')

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  # fix missing -lm
  sed -i 's/-llzma/-lm -llzma/' Makefile
  make
  # generate manpage
  a2x --doctype manpage --format manpage pixz.1.asciidoc
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  install -Dm 755 pixz   "${pkgdir}/usr/bin/pixz"
  install -Dm 644 pixz.1 "${pkgdir}/usr/share/man/man1/pixz.1"
}
