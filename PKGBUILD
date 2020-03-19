## $Id$
# Contributor: Alexey Andreyev <aa13q@ya.ru>
# Maintainer: James Kittsmiller (AJSlye) <james@nulogicsystems.com>

pkgname=qt-mlocale-git
_srcname=qt-mlocale
pkgver=0.7.1.r1.g44df7696
pkgrel=1
_project=aa13q # mer-core fork
_branch=aa13q-alpm-qt5.14
pkgdesc="Contains classes MLocale and friends originally from libmeegotouch"
arch=('x86_64' 'aarch64')
# FIXME: libmlocale qt-related repo naming
url="https://git.sailfishos.org/$_project/libmlocale#branch=$_branch"
license=('LGPLv2')
depends=('qt5-base')
makedepends=('git')
optdepends=()
provides=("${_srcname}")
conflicts=()
source=(
  "${pkgname}::git+${url}")
sha256sums=('SKIP')

pkgver() {
  cd "${srcdir}/${pkgname}"
  ( set -o pipefail
    git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g' ||
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
  ) 2>/dev/null
}

build() {
  cd "${srcdir}/${pkgname}"
  mkdir -p build
  cd build
  ../configure --prefix=/usr 
  #qmake ..
  make
}

package() {
  cd "${srcdir}/${pkgname}"
  cd build
  make INSTALL_ROOT="${pkgdir}" install
}
