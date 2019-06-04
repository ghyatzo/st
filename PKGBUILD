# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# Maintainer: Camillo Schenone <camillo.schenone@gmail.com>
pkgname=st-custom-git
_pkgname=st
pkgver=0.8.2.r1081.05b7d06
pkgrel=1
epoch=1
pkgdesc="My custom build of suckless' Simple Terminal (st) with a some patches"
arch=('i686' 'x86_64')
url="https://github.com/ghyatzo/st"
license=('MIT')
depends=('libxft')
makedepends=('git')

provides=('st')
conflicts=('st')

source=()

pkgver() {
	cd ..
	printf "%s.r%s.%s" "$(awk '/^VERSION =/ {print $3}' config.mk)" \
		"$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
	cd ..
	make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
	cd ..
	make PREFIX=/usr DESTDIR="${pkgdir}" install
	install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
	install -Dm644 README "${pkgdir}/usr/share/doc/${pkgname}/README"
}
