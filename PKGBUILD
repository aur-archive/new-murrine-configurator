# Maintainer: Limao Luo <luolimao+AUR@gmail.com>
# Contributor: DonVla <donvla@users.sourceforge.net>

pkgname=new-murrine-configurator
pkgver=1.4
pkgrel=5
pkgdesc="New Configurator for Murrine GTK Engine"
arch=(any)
url=http://www.cimitan.com/murrine
license=(GPL2)
depends=(pygtk)
provides=("${pkgname#*-}=$pkgver")
conflicts=(${pkgname#*-})
source=($url/files/nmc.tar_3.bz2
    ${pkgname#*-}.desktop)
sha256sums=('7a9c8eeb12263fe1cfdfe576b10451365dc18eb77d43e7b49be0905c3e29f0f7'
    'f6044e2eac0d9c60124b49d888810f94b4a96b511e20b491a77dd4d4b95036df')
sha512sums=('1c61bb48745b399fe906a1f84e82af3af7c0044225f4974c9b1a502eccac16241c0a6412d1a42d59dbc079c8680610f47f53e10df76cb5da978636ea53a95f6e'
    'c7087ee6a3f3a1ee434e9c952a7dc8c94e9abe094137934675aaa020ab9558feca711f8e6c91b532c54efe7d217b39e0a6cafef265871c715f29ca78cac11e69')

package() {
    desktop-file-install ${pkgname#*-}.desktop --dir "$pkgdir"/usr/share/applications/

    cd ${pkgname//-}/src/
    install -Dm644 ${pkgname#*-}.png "$pkgdir"/usr/share/pixmaps/${pkgname#*-}.png

    sed -i 's:^#!/usr/bin/env python$:&2:g' ${pkgname//-}.py
    for i in *.glade *.py{,c}; do
        install -Dm644 $i "$pkgdir"/usr/share/nmc/$i
    done
    chmod +x "$pkgdir"/usr/share/nmc/${pkgname//-}.py
}
