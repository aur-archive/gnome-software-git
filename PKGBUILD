# Maintainer: Yosef Or Boczko <yoseforb@gnome.org>

_pkgname=gnome-software
pkgname=$_pkgname-git
pkgver=3.14.1.r1.g579cd81
pkgrel=1
_realver=3.14.2
pkgdesc="GNOME Software Tools"
arch=(i686 x86_64)
license=('GPLv2')
url="https://wiki.gnome.org/Apps/Software/"
depends=("gtk3>=3.13.1" "glib2" "appstream-glib>=0.2.4" "sqlite" "libsoup"
	 "gsettings-desktop-schemas" "gnome-desktop" "packagekit>=1.0.0")
makedepends=("intltool" "git" "gnome-common")
options=('!libtool' '!emptydirs')
install=gnome-software.install
conflicts=("gnome-software")
replaces=("gnome-software")
provides=("gnome-software=$_realver")
source=('git://git.gnome.org/gnome-software')
sha256sums=('SKIP')

pkgver() {
  cd "$srcdir/$_pkgname"
  git describe --always | sed -E 's/^GNOME_SOFTWARE_//;s/_/./g;s/([^-]*-g)/r\1/;s|-|.|g'
}

prepare() {
  cd "$srcdir/$_pkgname"
}

build() {
  cd "$srcdir/$_pkgname"
  ./autogen.sh --prefix=/usr --disable-static --disable-schemas-compile
  make
}

package() {
  cd "$srcdir/$_pkgname"
  make DESTDIR="${pkgdir}" install
}
