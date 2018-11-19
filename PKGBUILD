# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# The following guidelines are specific to BZR, GIT, HG and SVN packages.
# Other VCS sources are not natively supported by makepkg yet.

# Maintainer: Michal Knapik
_pkgname=personal-keymap
pkgname=${_pkgname}-git # '-bzr', '-git', '-hg' or '-svn'
pkgver=r1.45cb7b4
pkgrel=1
pkgdesc="Polish Keyboard with Caps Lock mapped to Control."
arch=('x86_64')
url="https://github.com/mknapik/aur-personal-keymap"
license=('MIT')
groups=()
depends=()
makedepends=('git') # 'bzr', 'git', 'mercurial' or 'subversion'
provides=("${_pkgname}")
conflicts=("${_pkgnam}")
replaces=()
backup=()
options=()
install=
source=("$_pkgname::git+https://github.com/mknapik/aur-personal-keymap.git#branch=master")
noextract=()
md5sums=('SKIP')

# Please refer to the 'USING VCS SOURCES' section of the PKGBUILD man page for
# a description of each element in the source array.

pkgver() {
	cd "$srcdir/${_pkgname}"
# VERSION='VER_NUM.rREV_NUM.HASH', or a relevant subset in case VER_NUM or HASH
# Git, no tags available
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
	cd "$srcdir/${_pkgname}"
    mkdir -p ${pkgdir}/usr/local/share/kbd/keymaps/
    mkdir -p $(pkgdir)/usr/share/X11/xkb/symbols/personal
    cat personal.map | gzip > ${pkgdir}/usr/local/share/kbd/keymaps/personal.map.gz
    cp personal $(pkgdir)/usr/share/X11/xkb/symbols/personal
}

