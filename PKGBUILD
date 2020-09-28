# Maintainer: DingYuan Zhang <justforlxz@gmail.com>

pkgname=deepin-network-utils-git
pkgver=5.3.0.5.r0.g427534b
pkgrel=1
pkgdesc='DDE network utils'
arch=('x86_64')
url="https://github.com/linuxdeepin/dde-network-utils"
license=('GPL3')
depends=('deepin-qt-dbus-factory-git' 'gsettings-qt')
makedepends=('git' 'qt5-tools' 'gsettings-qt')
conflicts=('deepin-network-utils')
replaces=('deepin-network-utils')
provides=('deepin-network-utils')
groups=('deepin-git')
source=("$pkgname::git://github.com/linuxdeepin/dde-network-utils.git")
sha512sums=('SKIP')

pkgver() {
    cd $pkgname
    git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

prepare() {
  cd $pkgname
  # Use our own url instead of third-party commercial company's homepage
  sed -i '/www.baidu.com/i \    "https://www.archlinux.org/favicon.ico",' connectivitychecker.cpp
}

build(){
  cd $pkgname
  qmake-qt5 PREFIX=/usr
  make
}

package() {
  cd $pkgname
  make INSTALL_ROOT="$pkgdir" install
}
