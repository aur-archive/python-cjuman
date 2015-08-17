# Maintainer: nosada <ngsksdt@gmail.com>

pkgname=python-cjuman
pkgver=0.1.0
pkgrel=4
pkgdesc="A Python bindings of JUMAN, A Japanese Morphological Analyzer"
url="http://app-dist.khlog.net/software/python-cjuman/"
arch=('i686' 'x86_64')
license=('unknown')
depends=('juman' 'git' 'python2')

# this PKGBUILD uses cJuman installer (https://github.com/chezou/cJuman-installer) .
_gitroot="git://github.com/chezou/cJuman-installer.git"
_gitname="cJuman-installer"

build() {
  cd ${srcdir}
  msg "Connecting to GIT server...."

  if [[ -d ${_gitname} ]] ; then
    cd ${_gitname} && git pull origin
    msg "The local files are updated."
  else
    git clone "${_gitroot}" "${_gitname}"
  fi
 
  msg "GIT checkout done or server timeout"
  msg "Starting build..."
 
  rm -rf ${srcdir}/${_gitname}-build
  git clone "${srcdir}/${_gitname}" "${srcdir}/${_gitname}-build"
  cd ${srcdir}/${_gitname}-build
 
  python2 setup.py build
}

package() {
  cd ${srcdir}/${_gitname}-build
  python2 setup.py install --root=${pkgdir} --optimize=1
}

# vim:set ts=2 sw=2 et:
