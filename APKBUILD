# Contributor: Philipp Gaßner <activator112233@gmail.com>
# Maintainer: Philipp Gaßner <activator112233@gmail.com>
pkgname=nginx-mod-http-auth-pam
_ngxmodname=ngx_http_auth_pam_module
pkgver=1.5.3
_ngxver=1.22.0
pkgrel=3
pkgdesc="Testpackage"
url="https://localhost"
arch="all"
license="MIT"
depends="nginx"
makedepends="linux-pam-dev
        gcc
        make
        zlib-dev
        linux-headers
        pcre-dev
        openssl-dev"

checkdepends=""
install=""
subpackages=""
source="ngx-pam.tar.gz::https://github.com/sto/ngx_http_auth_pam_module/archive/refs/tags/v$pkgver.tar.gz
        https://nginx.org/download/nginx-$_ngxver.tar.gz
	"

builddir="$srcdir"

prepare() {
	pwd
#	mkdir ngx-pam
	mv nginx-"$_ngxver"/* .
	rm -rf nginx-"$_ngxver"/ nginx-"$_ngxver".tar.gz
#        tar -xzf "$srcdir"/ngx-pam.tar.gz --directory ngx-pam
	echo "load_module \"modules/$_ngxmodname.so\";" > auth_pam_module.conf
	default_prepare
}

build() {
        # Replace with proper build command(s)
        ./configure --add-dynamic-module="$srcdir"/"$_ngxmodname"-"$pkgver"
	make -f objs/Makefile modules
#	make DESTDIR="$pkgdir" install
}

check() {
        # Replace with proper check command(s)
        echo "All checks good!"
}

package() {
        # Replace with proper package command(s)
#        mkdir -p "$pkgdir"
	install -Dm644 "$srcdir"/objs/ngx_http_auth_pam_module.so "$pkgdir"/usr/lib/nginx/modules/ngx_http_auth_pam_module.so
	install -Dm644 "$srcdir"/auth_pam_module.conf "$pkgdir"/etc/nginx/modules/auth_pam_module.conf
}

sha512sums="
d1ab9205094eedfca3b8f41c4771c815bb033c4b4efa996e0b5aa7798c8e2bfb507502b565027b74fa26162750844242b57c9697148f0d9fb91083b3fc29d93e  ngx-pam.tar.gz
074782dba9cd5f8f493fbb57e20bda6dc9171814d919a47ee9f825d93f12c9f9d496e25d063c983191b55ad6a236bcef252ce16ecc1d253dc8b23433557559b1  nginx-1.22.0.tar.gz
"
