# Maintainer: Andrzej Giniewicz <gginiu@gmail.com>
pkgname=scikit-image
pkgver=0.9.3
pkgrel=1
pkgdesc="Image processing routines for SciPy"
arch=('i686' 'x86_64')
url="http://scikit-image.org/"
license=('BSD')
depends=('python2-scipy>=0.10')
makedepends=('python2-setuptools'
             'cython2>=0.17'
             'python2-numpy>=1.6'
             'python2-matplotlib>=1.0')
optdepends=('python2-pyqt4: The qt plugin that provides fancy imshow and skivi'
            'freeimage: to read more image file formats'
            'pyamg: for the fast cg_mg mode of random walker segmentation')
options=(!emptydirs)

source=("http://pypi.python.org/packages/source/s/scikit-image/scikit-image-${pkgver}.tar.gz")
md5sums=('f010e0cd46ee2996a6875c96b216e768')

build() {
  cd "$srcdir"/$pkgname-$pkgver

  python2 setup.py build
}

package() {
  cd "$srcdir"/$pkgname-$pkgver

  python2 setup.py install --root="$pkgdir"/ --optimize=1

  sed -i -e "s|#![ ]*/usr/bin/env python$|#!/usr/bin/env python2|" \
    $(find "${pkgdir}" -name '*.py')

  mv "$pkgdir"/usr/bin/skivi "$pkgdir"/usr/bin/skivi2

  install -D LICENSE.txt "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
}

