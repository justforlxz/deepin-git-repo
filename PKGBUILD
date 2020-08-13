# Maintainer: DingYuan Zhang <justforlxz@gmail.com>

pkgname=deepin-session-shell-git
pkgver=5.3.0.4.r0.g091f2c9
pkgrel=1
pkgdesc='Deepin desktop-environment - session-shell module'
arch=('x86_64')
url="https://github.com/linuxdeepin/dde-session-shell"
license=('GPL3')
depends=('deepin-daemon-git' 'deepin-wallpapers' 'gsettings-qt' 'liblightdm-qt5' 'startdde-git')
makedepends=('git' 'cmake' 'ninja' 'qt5-tools')
conflicts=('deepin-session-ui<5' 'deepin-session-shell')
provides=('lightdm-deepin-greeter' 'deepin-session-shell')
replaces=('deepin-session-shell')
groups=('deepin-git')
source=("git://github.com/linuxdeepin/dde-session-shell")
sha512sums=('SKIP')

pkgver() {
    cd dde-session-shell
    git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

prepare() {
  cd dde-session-shell
  sed -i '/darrowrectangle/d' CMakeLists.txt src/widgets/widgets.pri
  sed -i '1i#include <QPainterPath>' src/widgets/useravatar.cpp

  # We don't have common-auth on Arch
  sed -i 's/common-auth/system-login/' src/libdde-auth/authagent.cpp
}

build() {
  cd dde-session-shell
  cmake . -GNinja -DCMAKE_INSTALL_PREFIX=/usr
  ninja
}

package() {
  cd dde-session-shell
  DESTDIR="$pkgdir" ninja install

  chmod +x "$pkgdir"/usr/bin/deepin-greeter
}
