# Maintainer: Elia Cereda <eliacereda+arch at gmail dot com>

pkgname=shairport-sync-git
pkgver=2.1.11.r2.g3b5cc99
pkgrel=1
pkgdesc='Emulates an AirPort Express for the purpose of streaming music from iTunes and compatible iPods and iPhones'
url='https://github.com/mikebrady/shairport-sync'
arch=(i686 x86_64 armv6h armv7h)
license=('custom')
backup=(etc/conf.d/shairport-sync)
depends=(alsa-lib libdaemon openssl avahi popt libsoxr)
makedepends=(git)
source=("git+https://github.com/mikebrady/shairport-sync.git#branch=2.1"
	shairport-sync.service
	shairport-sync.conf
	remove-init.d.patch)
sha1sums=('SKIP'
          'f54cec1ec66e083c3074b3bca149f927c9367054'
          'f636e21daa066613539eb5d7693f984e8bc94640'
          '83ddd76fdb548bf6321e38ff7cabe14bf2bb35d4')

pkgver() {
  cd shairport-sync
  
  git describe --long --tags | sed -r 's/([^-]*-g)/r\1/;s/-/./g'
}

prepare() {
  cd shairport-sync
  
  git apply "$srcdir/remove-init.d.patch"
}

build() {
  cd shairport-sync

  autoreconf -i -f
  ./configure --with-alsa --with-avahi --with-ssl=openssl --with-soxr --prefix="$pkgdir/usr"
  make
}

package() {
  install -D -m644 shairport-sync.service "$pkgdir/usr/lib/systemd/system/shairport-sync.service"
  install -D -m644 shairport-sync.conf "$pkgdir/etc/conf.d/shairport-sync"

  cd shairport-sync

  install -D -m664 LICENSES "$pkgdir/usr/share/licenses/$pkgname/LICENSE"  

  make install
}