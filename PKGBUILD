# $Id$
# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Contributor: jiangxq <jiangxueqian at gmail dot com>
# Contributor: zh99998 <zh99998@gmail.com>
# Contributor: 4679kun <admin at 4679 dot us>

pkgname=shadowsocks-libev
pkgver=3.0.5
_commit=48f5a3bec864d80f1427c2c0090b87aba78267c8
pkgrel=1
pkgdesc='A lightweight secured socks5 proxy for embedded devices and low end boxes'
arch=('i686' 'x86_64')
url='https://github.com/shadowsocks/shadowsocks-libev'
license=('GPL3')
depends=('libcap' 'mbedtls' 'libsodium' 'libev' 'udns' 'pcre' 'libcorkipset' 'libbloom')
makedepends=('asciidoc' 'xmlto')
install=${pkgname}.install
source=("git+https://github.com/shadowsocks/$pkgname.git#tag=v$pkgver"
        'shadowsocks-libev@.service'
        'shadowsocks-libev-server@.service'
        'shadowsocks-libev-redir@.service'
        'shadowsocks-libev-tunnel@.service')

prepare() {
  cd "$srcdir"/$pkgname

  sed -i 's|AC_CONFIG_FILES(\[libbloom/Makefile libcork/Makefile libipset/Makefile\])||' configure.ac
}

build() {
  cd "$srcdir"/$pkgname

  ./autogen.sh
  ./configure --prefix=/usr --enable-shared --enable-system-shared-lib
  make
}

package() {
  cd "$srcdir"/$pkgname
  make DESTDIR="$pkgdir/" install
  install -Dm644 "$srcdir/shadowsocks-libev@.service" "$pkgdir/usr/lib/systemd/system/shadowsocks-libev@.service"
  install -Dm644 "$srcdir/shadowsocks-libev-server@.service" "$pkgdir/usr/lib/systemd/system/shadowsocks-libev-server@.service"
  install -Dm644 "$srcdir/shadowsocks-libev-redir@.service" "$pkgdir/usr/lib/systemd/system/shadowsocks-libev-redir@.service"
  install -Dm644 "$srcdir/shadowsocks-libev-tunnel@.service" "$pkgdir/usr/lib/systemd/system/shadowsocks-libev-tunnel@.service"
}
sha512sums=('SKIP'
            '92186a3baf340e3e3b7e8893b01bbf29356d0111ea7ecc10bb6a31278a834a7c428c501b0bb15fc1e983c6dab74a7094deae2c5972a4b3e6807ece668944d321'
            '4e7d22145af1e2ac65bfa0d8883c3b30a6ac726728265a782519ab3912d6e3034861e19b411b54aa1cdbf999b1758584f6452d9c98afb72b71f3a0b215813317'
            'fc9596365148150cb3509d23c1faad681bf5931a86d913b9b77daac14ce43826f4bd85384e91287e2856e07d9032a8205a26dbd827da8f641e443370e9dc45b2'
            'f3d28974d1efbe90c115dc943f324a737e4d493ffaf79fba71b05b799089b1141a01160ccc214fda0b237420ff15e7f03245cd1a2b29fc3349e82a9fa625c195')
