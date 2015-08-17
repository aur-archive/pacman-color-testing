# Maintainer: Det <nimetonmaili at gmail a-dot com>
# Contributor: JokerBoy <jokerboy at punctweb dot ro>
# Contributor: vogo <vogo(at)seznam(dot)cz>

pkgname=pacman-color-testing
pkgver=4.0.3
pkgrel=1
pkgdesc="A color patched command-line frontend for libalpm (Pacman) - prefers [testing]"
arch=('i686' 'x86_64')
url="https://projects.archlinux.org/svntogit/packages.git/log/trunk?h=packages/pacman"
license=('GPL')
depends=('pacman>=4.0' 'pacman<4.1')
conflicts=('pacman-color')
provides=('pacman-color')
backup=('etc/pacman.d/color.conf')
source=("ftp://ftp.archlinux.org/other/pacman/pacman-$pkgver.tar.gz"
        "$pkgname-$pkgver.patch"
        'color.conf')
sha1sums=('c39f55d3ea763dc9fd88ab1dfa21da96d768b9d9'  # pacman-$pkgver.tar.gz
          '0ea9a4ecd7844a51990fd9571186c045678c8968'  # $pkgname-$pkgver.patch
          '6e36b8720de0363f95b2ba7e06beb0770915c5c3') # color.conf

build() {
  cd pacman-$pkgver

  patch -p1 -i ../$pkgname-$pkgver.patch

  ./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var --disable-doc
  make
}

package() {
  install -D pacman-$pkgver/src/pacman/.libs/pacman "$pkgdir"/usr/bin/pacman-color
  install -Dm644 color.conf "$pkgdir"/etc/pacman.d/color.conf
}