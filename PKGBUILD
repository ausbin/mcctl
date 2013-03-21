# Maintainer: Austin Adams <screamingmoron at gmail dot com>
# Don't use this inside a cloned copy of the git repository. Put it in
# a fresh directory and build there instead.
pkgname=mcctl-git
pkgver=durr
pkgrel=2
pkgdesc="simplifies minecraft server administration"
arch=("any")
url="https://github.com/ausbin/mcctl"
license=('GPL')
depends=("procps-ng" "bash" "screen")
makedepends=('git')
optdepends=("sudo: for performing actions as another user")
backup=("etc/mcctl/mcctl.conf")

_gitroot=git://github.com/ausbin/mcctl.git
_gitname=mcctl

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

  # nothing to build :)
}

package() {
  cd "$srcdir/$_gitname-build"
  install -Dm 755 mcctl $pkgdir/usr/bin/mcctl
  install -Dm 644 mcctl.conf $pkgdir/etc/mcctl/mcctl.conf
}

# vim:set ts=2 sw=2 et:
