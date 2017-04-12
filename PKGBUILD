pkgname=('xsane')
pkgver=0.999
pkgrel=1
arch=(x86_64)
url="http://www.xsane.org"
license=('GPL2')
depends=('gtk2' 'lcms' 'sane' 'zlib' 'libjpeg' 'gimp')
source=(http://www.xsane.org/download/$pkgname-$pkgver.tar.gz)
md5sums=('9927f21e1ab6ba96315e7f0e30746deb')

prepare() {
  cd "$srcdir/$pkgname-$pkgver"
  sed -i -e 's:png_ptr->jmpbuf:png_jmpbuf(png_ptr):' src/xsane-save.c
}

build() {
  cd "$srcdir/$pkgbase-$pkgver"

  ./configure --prefix=/usr \
    --mandir=/usr/share/man \
    --enable-gimp
  make
}
package() {
  pkgdesc="A GTK-based X11 frontend for SANE and plugin for Gimp."
  install=$pkgname.install
  depends=('gtk2' 'lcms' 'sane' 'zlib' 'libjpeg')  
  cd "$srcdir/$pkgbase-$pkgver"
  make DESTDIR="$pkgdir" install
}
