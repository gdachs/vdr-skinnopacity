# Maintainer: Christopher Reimer <c[dot]reimer[at]googlemail[dot]com>
pkgname=vdr-skinnopacity
pkgver=0.0.5
_vdrapi=1.7.35
pkgrel=2yavdr1
pkgdesc="highly customizable native true color skin for the Video Disc Recorder"
url="http://projects.vdr-developer.org/projects/skin-nopacity"
arch=('x86_64' 'i686')
license=('GPL2')
depends=('imagemagick' 'libpng' "vdr-api=${_vdrapi}")
install="$pkgname.install"
_plugname=$(echo $pkgname | sed 's/vdr-//g')
replaces=("vdr-plugin-$_plugname")
conflicts=("vdr-plugin-$_plugname")
source=("http://projects.vdr-developer.org/attachments/download/1181/$pkgname-$pkgver.tgz")
md5sums=('93d6d98adc874cfbd0ac7cdc51828c6d')

build() {
  cd "${srcdir}/${_plugname}-${pkgver}"

  make
}

package() {
  cd "${srcdir}/${_plugname}-${pkgver}"

  make DESTDIR=${pkgdir} install

  mkdir -p $pkgdir/usr/share/vdr/plugins/$_plugname/icons
  cp -r icons/* $pkgdir/usr/share/vdr/plugins/$_plugname/icons

  mkdir -p $pkgdir/var/lib/vdr/themes
  cp -r themes/* $pkgdir/var/lib/vdr/themes
}
