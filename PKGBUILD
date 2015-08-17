
# Maintainer: flowerfairy <ktj-arch ατ ktrask δοτ de>
pkgname=stratum0-trayicon-git
pkgver=20130607
pkgrel=1
pkgdesc="Shows if the hackerspace stratum0 in Braunschweig (germany) is currently opened."
arch=('any')
url="git://github.com/rohieb/StratumsphereTrayIcon.git"
license=('GPLv3')
depends=()
makedepends=('git qconf qt4')

_gitroot="git://github.com/rohieb/StratumsphereTrayIcon.git"
_gitname="stratum0-trayicon"

build() {
  cd ${srcdir}

  msg "Connecting to GIT server..."
  if [[ -d ${_gitname} ]]; then
    (cd ${_gitname} && git pull origin)
  else
    git clone ${_gitroot} ${_gitname}
  fi
  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  rm -rf ${_gitname}-build
  git clone ${_gitname} ${_gitname}-build

  cd ${srcdir}/${_gitname}-build
  qmake-qt4 main.pro && make debug
}

package() {
  mkdir -p ${pkgdir}/usr/share/$pkgname
  mkdir -p ${pkgdir}/usr/bin
  mkdir -p ${pkgdir}/usr/share/licenses/$pkgname/
  cd "${srcdir}/${_gitname}-build"
  cp -r res ${pkgdir}/usr/share/$pkgname/
  cp s0trayicon ${pkgdir}/usr/bin/stratum0trayicon
  install -Dm644 LICENSE ${pkgdir}/usr/share/licenses/$pkgname/COPYING

  
}
