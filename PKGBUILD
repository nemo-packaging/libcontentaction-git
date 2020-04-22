# $Id$
# Contributor: TheKit <nekit1000 at gmail.com>
# Contributor: Bart Ribbers <bribbers@disroot.org>
# Contributor: Alexey Andreyev <aa13q@ya.ru>
# Maintainer: James Kittsmiller (AJSlye) <james@nulogicsystems.com>

_host="git.sailfishos.org"
_project=mer-core
_basename=nemo-qml-plugin-contentaction
_branch=master

_gitname=lib${_basename//nemo-qml-plugin-/}
pkgname=$_basename-git

pkgver=0.3.14.r0.gd5445f1

pkgrel=1
pkgdesc="Library for associating content with actions"
arch=('x86_64' 'aarch64')
url="https://$_host/$_project/$_gitname#branch=$_branch"
license=('LGPL-2.1-or-later')
depends=('qt5-systems' 'qt5-mlite')
makedepends=('git')
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
source=("${pkgname}::git+${url}")
md5sums=('SKIP')

pkgver() {
  cd "${srcdir}/${pkgname}"
  ( set -o pipefail
    git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g' ||
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
  ) 2>/dev/null
}

build() {
  cd "${srcdir}/${pkgname}"
  qmake
  make
}

package() {
  cd "${srcdir}/${pkgname}"
  make INSTALL_ROOT="${pkgdir}" install
  # Remove tests
  rm -r "$pkgdir/opt"
}
