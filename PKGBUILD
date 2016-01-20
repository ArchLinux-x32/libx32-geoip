# $Id: PKGBUILD 249863 2015-10-30 14:00:49Z juergen $
# Maintainer: Dan McGee <dan@archlinux.org>
# Contributor: Manolis Tzanidakis <manolis@archlinux.org>

pkgname=geoip
pkgver=1.6.6
pkgrel=1
pkgdesc="Non-DNS IP-to-country resolver C library & utils"
arch=('i686' 'x86_64')
url="http://www.maxmind.com/app/c"
license=('GPL')
depends=('zlib' 'geoip-database')
makedepends=('autoconf' 'libtool')
backup=('etc/geoip/GeoIP.conf')
options=('!emptydirs')
source=($pkgname-$pkgver.tar.gz::https://github.com/maxmind/${pkgname}-api-c/archive/v${pkgver}.tar.gz)
sha256sums=('db8ed5d07292c75cb3018738e6411037f15cc2a517f38ee04c1232cbe3d30b46')

prepare() {
  cd geoip-api-c-$pkgver
  autoreconf -vi
}

build() {
  cd geoip-api-c-$pkgver

  ./configure \
    --prefix=/usr \
    --mandir=/usr/share/man \
    --sysconfdir=/etc/geoip
  make
}

check() {
  cd geoip-api-c-$pkgver
  ln -sf /usr/share/GeoIP data
  make check
}

package() {
  cd geoip-api-c-$pkgver
  make DESTDIR="$pkgdir" install
}

# vim:set ts=2 sw=2 et:
