# Maintainer: David Tkachuk <davidtkachuk@gmail.com>
# Contributor: William Tang <galaxyking0419@gmail.com>
# Contributor: Bruce Zhang
# Contributor: lilac <lilac@build.archlinuxcn.org>
# Contributor: 吕海涛 <aur@lvht.net>

_extname=openswoole
pkgname=php-$_extname
pkgver=22.1.0
pkgrel=1
pkgdesc="Coroutine-based concurrency library for PHP"
arch=('x86_64')
url="https://github.com/openswoole/ext-openswoole"
license=('Apache')
depends=('php')
makedepends=('autoconf' 'gcc' 'make')

source=("https://github.com/openswoole/ext-openswoole/archive/refs/tags/v$pkgver.tar.gz" "$_extname.ini")
sha256sums=('0f6f881cc339979f83d4f32322a0864758c649139d1a01701c8d36963f1f0945'
            '41879b5bea7c87bd5b38c3d2335bd783bf2052d89a8959bf458219743e30999f')

build() {
    echo "$pkgdir"
    cd ext-openswoole-$pkgver
    phpize
    ./configure --enable-swoole-curl --enable-http2 --enable-openssl --enable-sockets --enable-hook-curl --enable-mysqlnd
    make
}

package() {
    mkdir -p "$pkgdir"/etc/php/conf.d \
        "$pkgdir"/usr/include/php/ext \
        "$pkgdir"/usr/lib/php/modules \
        "$pkgdir"/usr/share/licenses/$pkgname

    cp $_extname.ini "$pkgdir"/etc/php/conf.d/

    cd ext-openswoole-$pkgver
    cp -a include "$pkgdir"/usr/include/php/ext/$_extname
    mv .libs/$_extname.so "$pkgdir"/usr/lib/php/modules/
    cp LICENSE "$pkgdir"/usr/share/licenses/$pkgname/
}

