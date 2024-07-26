# Maintainer: Maxim Logaev <maxlogaev@proton.me>
# Contributor: Maxim Logaev <maxlogaev@proton.me>

pkgname=libdwarf
pkgver=20200114
pkgrel=1
pkgdesc="A library for handling DWARF Debugging Information Format"
arch=(x86_64)
license=('GPL' 'LGPL')
url="https://www.prevanders.net/dwarf.html"
depends=('elfutils')
checkdepends=('python')
provides=('libdwarf' 'libdwarf.so')
conflicts=('libdwarf-git')
source=(https://www.prevanders.net/libdwarf-$pkgver.tar.gz)
md5sums=('fa710b5e4662330cbbf55a565e5c497b')

build() {
  cd "$srcdir"/libdwarf-$pkgver
  CFLAGS+=" -ffat-lto-objects"
  ./configure --prefix=/usr --includedir=/usr/include/libdwarf --enable-shared
  make
}

check() {
  cd "$srcdir"/libdwarf-$pkgver
  make -j1 check
}

package() {
  cd "$srcdir"/libdwarf-$pkgver
  make DESTDIR="$pkgdir" install

  install -dm755 "$pkgdir"/usr/share/doc/$pkgname
  install -m644 README NEWS "$pkgdir"/usr/share/doc/$pkgname/
}
