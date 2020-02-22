# $Id$
# Maintainer: TheKit <nekit1000 at gmail.com>
# Maintainer: James Kittsmiller (AJSlye) <james@nulogicsystems.com>

pkgname=libcontentaction-git
pkgver=0.3.14.r0.gd5445f1
pkgrel=1
pkgdesc="Library for associating content with actions"
arch=('x86_64' 'aarch64')
url="https://git.sailfishos.org/mer-core/libcontentaction"
license=('GPL')
depends=('python' 'qt5-base' 'qt5-systems' 'mlite')
makedepends=('git' 'qt5-tools')
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
source=('git+https://git.sailfishos.org/mer-core/libcontentaction.git')
md5sums=('SKIP')

pkgver() {
	cd "$srcdir/${pkgname%-git}"
	git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

prepare() {
	cd "$srcdir/${pkgname%-git}"
}

build() {
	cd "$srcdir/${pkgname%-git}"
	qmake PREFIX=/usr
	make
}

package() {
	cd "$srcdir/${pkgname%-git}"
	make INSTALL_ROOT="$pkgdir/" install
}
