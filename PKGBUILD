# Maintainer: Elia Cereda <eliacereda+arch at gmail dot com>

pkgname=shairport-sync-git
pkgver=2.3.r38.g6bd14a6
pkgrel=1
pkgdesc='Emulates an AirPort Express for the purpose of streaming music from iTunes and compatible iPods and iPhones'
url='https://github.com/mikebrady/shairport-sync'
arch=(i686 x86_64 armv6h armv7h)
license=('custom')
backup=(etc/conf.d/shairport-sync)
install='shairport-sync.install'
depends=(alsa-lib libdaemon openssl avahi popt libsoxr libconfig)
makedepends=(git)
source=("git+https://github.com/mikebrady/shairport-sync.git#branch=development"
	shairport-sync.install
	shairport-sync.service
	shairport-sync.conf)
sha1sums=('SKIP'
          'd51485f3857529b70a29b38814ea60e7dde54ca8'
          '79c9fcd8d885b265c5704a462e9b0445ea8e66c7'
          '789c29ddd39df97138932239e066772c6c118afe')

pkgver() {
  cd shairport-sync
  
  git describe --long --tags | sed -r 's/([^-]*-g)/r\1/;s/-/./g'
}

build() {
  cd shairport-sync

  autoreconf -i -f
  ./configure --without-initscript --without-configfiles --with-metadata --with-alsa --with-avahi --with-ssl=openssl --with-soxr --prefix="$pkgdir/usr"
  make
}

package() {
  install -D -m644 shairport-sync.service "$pkgdir/usr/lib/systemd/system/shairport-sync.service"
  install -D -m644 shairport-sync.conf "$pkgdir/etc/conf.d/shairport-sync"

  cd shairport-sync

  install -D -m664 LICENSES "$pkgdir/usr/share/licenses/$pkgname/LICENSE"  

  make install
}
