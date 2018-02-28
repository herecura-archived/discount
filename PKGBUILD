# Maintainer:  Hyacinthe Cartiaux <hyacinthe.cartiaux at free.fr>
# Contributor: Bartlomiej Piotrowski <nospam at bpiotrowski dot pl>
# Contributor: Patrick McCarty <pnorcks at gmail dot com>

pkgname=discount
pkgver=2.2.3
pkgrel=1
pkgdesc="A Markdown implementation written in C"
arch=('x86_64')
url="http://www.pell.portland.or.us/~orc/Code/discount/"
license=('custom:BSD')
provides=('markdown')
conflicts=('markdown')
source=("https://github.com/Orc/${pkgname}/archive/v$pkgver.tar.gz"
        "no-ldconfig.patch")
md5sums=('1231aa1f496ec176f2933066c3d9871b'
         '7bea5892210296f62b255bbd57169ef9')

build() {
  cd "$srcdir/$pkgname-$pkgver"
  sed -e "s/m 444/m 644/g" -i configure.inc
  patch -p1 -i "$srcdir/no-ldconfig.patch"
  ./configure.sh --prefix=/usr --enable-all-features --with-fenced-code --shared
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  mkdir -p $pkgdir/usr/{bin,include,lib}
  make DESTDIR="$pkgdir" install.everything
  install -Dm644 COPYRIGHT "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
