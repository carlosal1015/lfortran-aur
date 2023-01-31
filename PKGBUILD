# Maintainer: Ciappi <marco.scopesi@gmail.com>
# Contributor: Carlos Aznarán <caznaranl@uni.pe>
pkgname=lfortran
pkgver=0.18.0
pkgrel=3
pkgdesc="Modern interactive LLVM-based Fortran compiler"
arch=('x86_64')
url="https://${pkgname}.org"
license=('custom:BSD-3-clause')
# depends=("clang" "zlib" "ncurses" "xeus2")
makedepends=(cmake) # llvm11
checkdepends=()
optdepends=()
source=(https://${pkgname}.github.io/tarballs/release/${pkgname}-${pkgver}.tar.gz)
sha512sums=('4d7eb7c8c88155fb9c8538acd0579e9b1d78e676a0429b776220711c6694857a6b73f1c36ac570daefdbda4f016b510cdf0e99b5e5e9dea5fc7f32345f7494f2')

build() {
  cmake \
    -S ${pkgname}-${pkgver} \
    -B build \
    -DCMAKE_BUILD_TYPE=None \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -Wno-dev
  # -DWITH_LLVM=yes \
  # -DWITH_XEUS=yes \
  cmake --build build --target all
}

check() {
  ctest --verbose --output-on-failure --test-dir build
}

package() {
  DESTDIR="${pkgdir}" cmake --build build --target install
  install -Dm 644 LICENSE -t "${pkgdir}/usr/share/licenses/${pkgname}"
}
