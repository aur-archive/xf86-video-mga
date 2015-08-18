# $Id: PKGBUILD 230899 2015-02-06 08:08:27Z lcarlier $
# Maintainer: Jan de Groot <jgc@archlinux.org>

pkgname=xf86-video-mga
pkgver=1.6.3
pkgrel=4
pkgdesc="X.org mga video driver"
arch=(i686 x86_64)
url="http://xorg.freedesktop.org/"
license=('custom')
depends=('glibc')
makedepends=('xorg-server-devel' 'X-ABI-VIDEODRV_VERSION=19')
conflicts=('xorg-server<1.16' 'X-ABI-VIDEODRV_VERSION<19' 'X-ABI-VIDEODRV_VERSION>=20')
optdepends=('mga-dri: DRI1 support from community repo')
groups=('xorg-drivers' 'xorg')
source=(${url}/releases/individual/driver/${pkgname}-${pkgver}.tar.bz2 git-fixes.patch)
sha256sums=('7704b1ea35098769787a9c93e903b827be97a99facfb1696aa5236a58ff1c7d7'
            '3a7b12629fd79b06eda845728d0abdef664703f3e599bba2f34d8994ac7d7a75')

prepare() {
  cd ${pkgname}-${pkgver}
  patch -Np1 -i ../git-fixes.patch
}

build() {
  cd ${pkgname}-${pkgver}
  ./configure --prefix=/usr
  make
}

package() {
  cd ${pkgname}-${pkgver}
  make DESTDIR="${pkgdir}" install

  install -m755 -d "${pkgdir}/usr/share/licenses/${pkgname}"
  install -m644 COPYING "${pkgdir}/usr/share/licenses/${pkgname}/"
}
