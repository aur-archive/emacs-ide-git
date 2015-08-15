# Maintainer: Stefan Husmann <stefan-husmann@t-online.de>
pkgname=emacs-ide-git
pkgver=185.70c98f5
pkgrel=1
pkgdesc="Integrated Development Environment (IDE) interface for Emacs (code browsing, compilation, debug...)."
arch=('any')
url="http://emacs-ide.tuxfamily.org/index.html"
license=('GPL3')
depends=('emacs' 'ctags' 'cscope')
makedepends=('git')
provides=('emacs-ide')
conflicts=('emacs-ide')
install=emacs-ide.install
source=("git://git.tuxfamily.org/gitroot/eide/emacs-ide.git")
md5sums=('SKIP')
_gitname="emacs-ide"

pkgver() {
  cd $srcdir/${_gitname}
  echo $(git rev-list --count HEAD).$(git rev-parse --short HEAD)
}

build() {
  cd $srcdir/${_gitname}
  rm -vf src/*.elc
  emacs --batch -L src -f batch-byte-compile src/*.el
}

package() {
  cd $srcdir/${_gitname}/src
  install -d $pkgdir/usr/share/emacs/site-lisp
  for _i in *.el*
  do
    echo ${_i}
    install -m644 ${_i} $pkgdir/usr/share/emacs/site-lisp/
  done
}
