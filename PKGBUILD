# Maintainer: Elia Cereda <eliacereda+arch at gmail dot com>
# This version from https://github.com/mikebrady/shairport-sync-PKGBUILD

pkgname=shairport-sync
pkgver=3.2.2
pkgrel=1
pkgdesc='AirPlay Audio Player'
url='https://github.com/mikebrady/shairport-sync'
arch=(i686 x86_64 armv6h armv7h)
license=('custom')
backup=(etc/shairport-sync.conf)
install='shairport-sync.install'
depends=(alsa-lib libdaemon openssl avahi popt libsoxr libconfig)
makedepends=(git)
source=("git+https://github.com/mikebrady/shairport-sync.git"
	shairport-sync.install
	shairport-sync.service
	shairport-sync.conf)

sha1sums=('SKIP'
          'd51485f3857529b70a29b38814ea60e7dde54ca8'
          'fe62feeef1c947ed6ed3500b7b922dcaf9e8987c'
          '6c4979abddb4b1c0242a941279d41617ab8d183c')

prepare() {
  cd shairport-sync
#  git checkout development > /dev/null 2>&1
}

build() {
  cd shairport-sync
#  git checkout development > /dev/null 2>&1
  autoreconf -i -f
  ./configure --with-alsa --with-avahi --with-ssl=openssl --with-soxr --without-configfiles --prefix=/usr --sysconfdir=/etc
  make
}

package() {
  install -D -m644 shairport-sync.service "$pkgdir/usr/lib/systemd/system/shairport-sync.service"
  install -D -m644 shairport-sync.conf "$pkgdir/etc/conf.d/shairport-sync"

  cd shairport-sync
#  git checkout development > /dev/null 2>&1
  install -D -m664 LICENSES "$pkgdir/usr/share/licenses/$pkgname/LICENSE"  

  make DESTDIR="$pkgdir" install
  install -D -m644 scripts/shairport-sync.conf "$pkgdir/etc/shairport-sync.conf"
  install -D -m644 scripts/shairport-sync.conf "$pkgdir/etc/shairport-sync.conf.sample"
}
