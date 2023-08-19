# This file is part of BlackArch Linux ( https://www.blackarch.org/ ).
# See COPYING for license details.

pkgname=dnsrecon
pkgver="1.1.5"
_pyver=3.11
pkgrel=1
epoch=2
groups=('blackarch' 'blackarch-recon')
pkgdesc='Python script for enumeration of hosts, subdomains and emails from a given domain using google.'
url='https://github.com/darkoperator/dnsrecon'
license=('custom')
arch=('any')
depends=('python' 'python-netaddr' 'python-dnspython' 'python-lxml' 'flake8' 'python-pytest' )
makedepends=('git' 'python-setuptools')
source=("git+https://github.com/darkoperator/$pkgname.git")
sha512sums=('SKIP')

pkgver() {
  cd $pkgname

  grep -m1 __version "$pkgname/cli.py" | cut -d '=' -f 2 |
  sed "s/'//g" | tr -d ' '
}

build() {
  cd $pkgname

  python setup.py build
}

package() {
  cd $pkgname

  python setup.py install --root="$pkgdir" --prefix=/usr -O1 --skip-build

  rm -rf "$pkgdir/usr/lib/python$_pyver/site-packages/tests"
}
