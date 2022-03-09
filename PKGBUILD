# Maintainer: Philip Johansson <philipphuket at gmail dotcom>
pkgname=st-philip
_pkgname=st
pkgver=0
pkgrel=1
epoch=1
pkgdesc="Philips build of st"
url='https://github.com/flyingpeakock/st'
arch=('i686' 'x86_64')
license=('MIT')
depends=('libxft')
makedepends=('git')
source=('git://github.com/flyingpeakock/st')
sha1sums=('SKIP')
provides=("${_pkgname}")
conflicts=("${_pkgname}")
_sourcedir=st
_makeopts="--directory=$_sourcedir"

pkgver() {
	cd "${_pkgname}"
	printf "%s.r%s.%s" "$(awk '/^VERSION =/ {print $3}' config.mk)" \
		"$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
	make $_makeopts X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
    local installopts='--mode 0644 -D --target-directory'
    local shrdir="$pkgdir/usr/share"
    local licdir="$shrdir/licenses/st"
    local docdir="$shrdir/doc/st"
    make $_makeopts PREFIX=/usr DESTDIR="$pkgdir" install
    install $installopts "$licdir" "$_sourcedir/LICENSE"
    install $installopts "$docdir" "$_sourcedir/README.md"
    install $installopts "$shrdir/st" "$_sourcedir/st.info"
}
