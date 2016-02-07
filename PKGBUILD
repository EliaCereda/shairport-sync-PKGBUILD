# Maintainer: Moritz K. <moritzmhmk at gmail dot com>

pkgname=shairport-sync-git
pkgver=2.8.0
pkgrel=1
pkgdesc='Emulates an AirPort Express for the purpose of streaming music from iTunes and compatible iPods and iPhones'
url='https://github.com/mikebrady/shairport-sync'
arch=(i686 x86_64 armv6h armv7h)
license=('custom')
backup=(etc/shairport-sync.conf)
install='shairport-sync.install'
depends=(alsa-lib libdaemon openssl avahi popt libsoxr libconfig)
makedepends=(git)
source=("git+https://github.com/mikebrady/shairport-sync.git#branch=development"
	shairport-sync.install)
sha1sums=('SKIP'
          'd51485f3857529b70a29b38814ea60e7dde54ca8')

pkgver() {
  cd shairport-sync
  git describe --long --tags | sed -r 's/([^-]*-g)/r\1/;s/-/./g'
}

build() {
  cd shairport-sync
  autoreconf -i -f
  ./configure --with-systemd --with-configfiles --with-metadata --with-alsa --with-avahi --with-ssl=openssl --with-soxr --prefix=/usr
  make
}

package() {
  cd shairport-sync
  install -D -m664 LICENSES "$pkgdir/usr/share/licenses/$pkgname/LICENSE"  
  make DESTDIR="$pkgdir/" install
}
