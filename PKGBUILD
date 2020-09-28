# Maintainer: DingYuan Zhang <justforlxz>

pkgname=deepin-session-ui-git
pkgver=5.3.0.11.r2.gb543c475
pkgrel=1
pkgdesc='Deepin desktop-environment - Session UI module'
arch=('x86_64')
url="https://github.com/linuxdeepin/dde-session-ui"
license=('GPL3')
groups=('deepin')
depends=('gsettings-qt' 'startdde-git' 'liblightdm-qt5' 'qt5-svg' 'deepin-daemon-git' 'dde-dock-git' 'deepin-wallpapers')
makedepends=('git' 'deepin-gettext-tools-git' 'qt5-tools' 'dde-dock-git')
provides=('deepin-notifications' 'deepin-session-ui')
conflicts=('dde-workspace' 'deepin-session-ui' 'deepin-notifications')
replaces=('dde-workspace' 'deepin-session-ui' 'deepin-notifications')
groups=('deepin-git')
source=("$pkgname::git://github.com/linuxdeepin/dde-session-ui")
sha512sums=('SKIP')

pkgver() {
    cd $pkgname
    git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

prepare() {
  cd $pkgname
  sed -i 's|/usr/share/backgrounds/default_background.jpg|/usr/share/backgrounds/deepin/desktop.jpg|' widgets/*.cpp
}

build() {
  cd $pkgname
  qmake-qt5 PREFIX=/usr
  make -j$(nproc)
}

package() {
  cd $pkgname
  make INSTALL_ROOT="$pkgdir" install
}
