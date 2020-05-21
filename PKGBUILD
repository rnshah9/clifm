# Maintainer: archcrack <johndoe.arch@outlook.com>

pkgname=clifm
pkgver=0.12.1.3
pkgrel=1
pkgdesc="The KISS file manager: text-based, ultra-lightweight, lightning fast, and written in C"
arch=(any)
url="https://github.com/leo-arch/clifm"
license=(GPL2)
depends=('glibc' 'ncurses' 'libcap' 'readline' 'coreutils')
makedepends=('git')
optdepends=('xdg-utils: Automatically open files via their default associated program')
source=("git+${url}.git")
sha256sums=('SKIP')

build() {
  cd "${srcdir}/${pkgname}"
  gcc -O3 -march=native -s -fstack-protector-strong -lcap -lreadline -o clifm clifm.c 
}

package() {
  cd "${srcdir}/${pkgname}"
  install -Dm755 $pkgname "${pkgdir}/usr/bin/$pkgname"
  install -g 0 -o 0 -Dm644 manpage "${pkgdir}/usr/share/man/man1/${pkgname}.1"
  gzip "${pkgdir}/usr/share/man/man1/${pkgname}.1"
  install -g 0 -o 0 -Dm644 translations/spanish/${pkgname}.mo "${pkgdir}/usr/share/locale/es/LC_MESSAGES/${pkgname}.mo"
}

