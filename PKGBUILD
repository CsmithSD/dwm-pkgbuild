pkgname=dwm-pkgbuild
_pkgname=dwm
pkgver=6.1.23.4.gb5545ac
pkgrel=1
pkgdesc="A dynamic window manager for X"
url="http://dwm.suckless.org"
arch=('i686' 'x86_64')
license=('MIT')
options=(zipman)
depends=('libx11' 'libxinerama' 'libxft')
makedepends=('git')
install=dwm.install
provides=('dwm')
conflicts=('dwm')
epoch=1
source=(dwm.desktop
        "$_pkgname::git+https://github.com/CsmithSD/dwm")
md5sums=('SKIP'
         'SKIP')

pkgver(){
  cd $_pkgname
  git describe --tags |sed 's/-/./g'
}

prepare() {
  cd $_pkgname
  if [[ -f "$SRCDEST/$pkgname/config.h" ]]; then
    cp -f "$SRCDEST/$pkgname/config.h" config.h
  fi
}

build() {
  cd $_pkgname
  make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
  cd $_pkgname
  make PREFIX=/usr DESTDIR="$pkgdir" install
  install -m644 -D LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
  install -m644 -D README "$pkgdir/usr/share/doc/$pkgname/README"
  install -m644 -D ../dwm.desktop "$pkgdir/usr/share/xsessions/dwm.desktop"
}

# vim:set ts=2 sw=2 et:
