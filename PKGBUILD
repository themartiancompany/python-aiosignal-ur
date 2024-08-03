# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Levente Polyak <anthraxx[at]archlinux[dot]org>

_py="python"
_pkg=aiosignal
pkgname="${_py}-${_pkg}"
pkgver=1.3.1
pkgrel=6
pkgdesc='List of registered asynchronous callbacks'
_http="https://github.com"
_ns="aio-libs"
url="${_http}/${_ns}/${_pkg}"
arch=(
  'any'
)
license=(
  'Apache'
)
depends=(
  "${_py}"
  "${_py}-frozenlist"
)
makedepends=(
  "${_py}-build"
  "${_py}-installer"
  "${_py}-setuptools"
  "${_py}-wheel"
)
checkdepends=(
  "${_py}-pytest"
  "${_py}-pytest-cov"
  "${_py}-pytest-asyncio"
)
source=(
  "${url}/archive/v${pkgver}/${pkgname}-${pkgver}.tar.gz"
)
sha512sums=(
  'c03454d1b855bb3e84d3ce07fb32d08855b42d1ca7723fd67d3b2ef1bc66038a31974fabda7561c90e2beaf4cdd2c28cc0463e43eb5d5c127df0cd187ae3c2e2'
)
b2sums=(
  '16112f674f20b97406eff16a6a9baca1ef414132ec53a67789e08347f06a462ff653c7a00d6865855f5fe0fd70ba4a2bebe286020fdf1942da41d43f72e67837'
)

build() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    -m \
      build \
    --wheel
}

check() {
  cd \
    "${_pkg}-${pkgver}"
  PYTHONPATH="$PWD" \
  pytest \
    -v
}

package() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    -m \
      installer \
    --destdir="${pkgdir}" \
    dist/*.whl
  install \
    -Dm 644 \
    LICENSE \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}"
  install \
    -Dm 644 \
    CHANGES.rst \
    README.rst \
    -t \
    "${pkgdir}/usr/share/doc/${pkgname}"
}

# vim: ts=2 sw=2 et:
