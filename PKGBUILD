pkgname=allegro.pas
pkgver=4.4.4
pkgrel=3
pkgdesc="Allegro.pas is a wrapper to use Allegro with Pascal compilers"
url="http://allegro-pas.sourceforge.net"
license=("unknown")
arch=(i686 x86_64)
makedepends=(fpc)
depends=(fpc)
source=("http://downloads.sourceforge.net/allegro-pas/allegro.pas-$pkgver-src-pas.tar.bz2")
md5sums=('3fa5e76c67015515c250c2f2c0ff668b')
_unittgt=`fpc -iSP`-`fpc -iSO`
_fpcver=`fpc -iV`

build() {
  cd "${srcdir}/allegro.pas/lib"
  for file in `ls *.pas`
  do
    fpc $file
  done
}

package() {
  cd "${srcdir}/allegro.pas/lib"
  find . -name '*.o' -o -name '*.ppu' -o -name '*.rst' -o -name '*.a'|
    xargs -rtl1 -I {} install -Dm644 {} "$pkgdir/usr/lib/fpc/$_fpcver/units/$_unittgt/allegro.pas/"{}
}
