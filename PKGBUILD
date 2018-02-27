# Maintainer: Eric Vidal <eric@obarun.org>

pkgname=mdevd
pkgver=0.1.0.1
pkgrel=1
pkgdesc="a mdev-compatible hotplug manager daemon"
arch=(x86_64)
url="http://skarnet.org/software/mdevd/"
license=('ISC')
depends=('skalibs')
groups=('s6-suite')
source=("$pkgname::git+git://git.skarnet.org/mdevd#tag=v${pkgver}")
#source=("$pkgname::git+git://git.skarnet.org/mdevd#commit=$_commit")
#_commit= # tag 
sha256sums=('SKIP')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal

build() {
  cd ${srcdir}/${pkgname}
  ./configure --prefix=/usr \
			  --bindir=/usr/bin \
			  --sbindir=/usr/bin \
			  --datadir=/etc \
			  --enable-shared
  make
}

package() {
  cd ${srcdir}/${pkgname}

  DESTDIR=${pkgdir} make install
  
  # add doc
  install -dm 0755 $pkgdir/usr/share/doc/$pkgname/
  cp -R doc/* $pkgdir/usr/share/doc/$pkgname/
 
  install -D -m644 COPYING "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

# vim:ft=sh ts=2 sw=2 et:
