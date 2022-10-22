# Maintainer : Yamada Hayao <hayao@fascode.net>
# Contributer: David Mazieres (http://www.scs.stanford.edu/~dm/addr/)

pkgname='droidcam-obs-plugin'
pkgver='1.6.0'
pkgrel='2'
pkgdesc='plugin for droidcam obs'
arch=("x86_64" "i686")
url='https://dev47apps.com/obs/'
srcurl='https://github.com/dev47apps/droidcam-obs-plugin.git'
license=('GPL')
depends=('obs-studio' 'libjpeg-turbo' 'libusbmuxd' 'libimobiledevice')
pkgstem=${pkgname%-git}
provides=("${pkgstem}")
conflicts=("${pkgstem}")
source=("${pkgstem}::git+${srcurl}#tag=${pkgver}" "fix-Makefile.patch")
sha256sums=('SKIP' 'f9a57b64ab8e156a9e25355010a41d059a4486f9af402505975dc9e4bb1c3d56')

prepare() {
    cd "$srcdir/$pkgstem"
    patch -p1 -i "$srcdir/fix-Makefile.patch"
    mkdir build
}

build() {
    cd "$srcdir/$pkgstem"
    make ALLOW_STATIC=no
}

package() {
    mkdir -p "$pkgdir/usr/lib/obs-plugins"
    cp "$srcdir/$pkgstem/build/droidcam-obs.so" "$pkgdir/usr/lib/obs-plugins/"
    mkdir -p "$pkgdir/usr/share/obs/obs-plugins/droidcam-obs"
    cp -r "$srcdir/$pkgstem/data/locale" "$pkgdir/usr/share/obs/obs-plugins/droidcam-obs/"
}
