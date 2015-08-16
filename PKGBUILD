# Maintainer: Einar Lielmanis <einars@gmail.com>
# Contributor: Benjamin Andresen <bandresen@gmail.com>
# Based on the ocaml package by Tobias Powalowski <tpowa@archlinux.org>

pkgname=jocaml
pkgver=4.01.0
pkgrel=1
pkgdesc="JoCaml is Objective Caml plus (&) the join calculus, that is, OCaml extended for concurrent and distributed programming."
arch=('i686' 'x86_64')
license=('GPL2' 'custom: QPL-1.0')
url="http://caml.inria.fr/"
depends=('gdbm' 'ocaml')
makedepends=('ncurses>=5.6-7' 'ocaml=4.01.0')
optdepends=('ncurses=5.6-7: advanced ncurses features' 'tk: advanced tk features')
source=(http://jocaml.inria.fr/pub/distri/jocaml-4.01/jocaml-$pkgver.tar.gz)
options=('!makeflags' '!emptydirs')

build() {
  cd $srcdir/jocaml-$pkgver
  # force it to use preinstalled ocaml as companion
  ./configure -prefix /usr -ocamllib /usr/lib/ocaml
  echo $pkgver > VERSION
  make world
  make opt
  make world.opt

}

package () {
  make PREFIX=$pkgdir/usr install

  install -D -m 644 $srcdir/jocaml-$pkgver/LICENSE $pkgdir/usr/share/licenses/jocaml/LICENSE

  # rename superfluous files to avoid duplication with the required ocaml package
  mv $pkgdir/usr/bin/ocamlmktop $pkgdir/usr/bin/jocaml-ocamlmktop
}

md5sums=('ddb36ea5e1a820fc8fa2613009677c80')
