# Maintainer: David Tkachuk <davidtkachuk@gmail.com>
# Contributor: William Tang <galaxyking0419@gmail.com>
# Contributor: Bruce Zhang
# Contributor: lilac <lilac@build.archlinuxcn.org>
# Contributor: 吕海涛 <aur@lvht.net>

_extname=openswoole
pkgname=php-$_extname
pkgver=22.0.0
pkgrel=1
pkgdesc="Coroutine-based concurrency library for PHP"
arch=('x86_64')
url="https://github.com/openswoole/swoole-src"
license=('Apache')
depends=('php')
makedepends=('autoconf' 'gcc' 'make')

source=("https://github.com/openswoole/swoole-src/archive/refs/tags/v$pkgver.tar.gz" "$_extname.ini")
sha256sums=('9886c6b619edec3ec3e269ca63aed9170502249c902885088a881678524e4e06'
            '41879b5bea7c87bd5b38c3d2335bd783bf2052d89a8959bf458219743e30999f')

build() {
    echo "$pkgdir"
    cd swoole-src-$pkgver
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

    cd swoole-src-$pkgver
    cp -a include "$pkgdir"/usr/include/php/ext/$_extname
    mv .libs/$_extname.so "$pkgdir"/usr/lib/php/modules/
    cp LICENSE "$pkgdir"/usr/share/licenses/$pkgname/
}

