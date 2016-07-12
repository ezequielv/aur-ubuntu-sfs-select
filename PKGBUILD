# Maintainer: Dan Elkouby <streetwalrus@codewalr.us>
pkgname=sfs-select
pkgver=0.3.1
pkgrel=1
pkgdesc="A small tool to manage Steam Family Sharing"
arch=('any')
url="https://www.unix-ag.uni-kl.de/~t_schmid/sfs-select/"
license=('None')
depends=('steam' 'python>=3.0' 'python-pyside' 'python-psutil')
makedepends=('python-setuptools')
options=(!emptydirs)
source=("https://www.unix-ag.uni-kl.de/~t_schmid/sfs-select/sfs-select-$pkgver-full.7z"
        "setup.py"
        "01-packageify.patch"
        "02-config.patch")
md5sums=('ecc62ad869564be1a591b2eca7f9af19'
         '5f7dd6d5a52294d4aa8baadaefe4f4fe'
         'd494a9688751ffb2cc3a5ad2591c133d'
         'db7095cfd5a8b65c2965ed2bfeaea27e')

prepare() {
  cd "$srcdir"
  rm -rf sfs_select
  mkdir sfs_select
  cp sfs-select/python/{*.py,*.ui} sfs_select

  patch -Np0 -i 01-packageify.patch
  patch -Np0 -i 02-config.patch

  mv sfs_select/{sfs-select.py,__init__.py}
  chmod -x sfs_select/__init__.py
}

package() {
  cd "$srcdir"
  ./setup.py install --root="$pkgdir/" --optimize=1
}

# vim:set ts=2 sw=2 et ft=sh:
