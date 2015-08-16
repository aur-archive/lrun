# Maintainer: Jun Wu <quark@zju.edu.cn>

pkgname=lrun
pkgver=0.9.9
pkgrel=1
pkgdesc='Run command on Linux with resources limited.'
url='https://github.com/quark-zju/lrun'
license=('MIT')
arch=('i686' 'x86_64')
source=($pkgname-$pkgver.tar.gz::https://github.com/quark-zju/$pkgname/archive/v${pkgver}.tar.gz)
sha1sums=('31d6eb114b0898b5ce2f431c8091ed5fb305e262')
depends=('linux>=2.6.26')
makedepends=('gcc>=4.4 pkg-config ruby')
optdepends=('libseccomp>=2.0')
install=lrun.install

build() {
  pkg-config --max-version 2.9 libseccomp || echo 'libseccomp 1.x or 2.x not found, syscall filter will not work'
  cd "${srcdir}/${pkgname}-${pkgver}/src/"
  rake
}
 
package() {
  cd "${srcdir}/${pkgname}-${pkgver}/src/"
  PREFIX=${pkgdir}/usr rake
  install -D -m4550 -oroot -g 593 -s "lrun" "$pkgdir/usr/sbin/lrun"

  cd "${srcdir}/${pkgname}-${pkgver}/"
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
 
# vim:set ts=2 sw=2 et:
