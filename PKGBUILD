pkgname=luastatus-git
pkgver=r139.163ce5e
pkgrel=1
pkgdesc='Generates status bar to use with dzen2 or wmii'
arch=('x86_64')
url='https://github.com/shdown/luastatus'
license=('LGPL-3.0')
depends=('lua' 'libx11' 'libxcb' 'alsa-lib' 'yajl>=2.1.0' 'xcb-util-wm')
makedepends=('git' 'pkgconfig')
options=('docs')
conflicts=('luastatus')
provides=('luastatus-i3-wrapper' 'luastatus-lemonbar-launcher' 'luastatus')
source=(git+https://github.com/shdown/luastatus)
sha1sums=('SKIP')

_gitname='luastatus'

pkgver() {
  cd "`echo $pkgname|sed -e s/-git//`"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd "${srcdir}/${_gitname}"
  cmake .
  make
}

package() {
  cd "${srcdir}/${_gitname}"
  make DESTDIR="$pkgdir" install
  install -Dm644 LICENSE.txt "$pkgdir/usr/share/licenses/`echo $pkgname|sed -e s/-git//`/LICENSE.txt"
  make clean
}
