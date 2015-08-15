# Maintainer: Guten Ye

pkgname="chnroutes-git"
pkgver=20121228
pkgrel=1
pkgdesc="scripts help chinese netizen, who uses vpn to combat censorship."
arch=("i686" "x86_64")
url="https://github.com/GutenYe/chnroutes"
license=("unkonwn") 
provides=("chnroutes")
conflicts=("chnroutes")
depends=("python2" "iproute2")
makedepends=("git")

_gitroot="git://github.com/GutenYe/chnroutes.git"
_gitname="chnroutes"

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [[ -d "$_gitname" ]]; then
    cd "$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot" "$_gitname"
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting build..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"
  cd "$srcdir/$_gitname-build"

  sed -i -r '1s/python2?/python2/' chnroutes.py
}

package() {
  cd "${srcdir}/${_gitname}-build"

  install -Dm755 chnroutes.py "$pkgdir/usr/bin/chnroutes"
}

# vim:set ts=2 sw=2 et:
md5sums=()
