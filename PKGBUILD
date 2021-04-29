# Maintainer: D1nuc0m <d1nuc0m@protonmail.com>
# Submitter and previous Maintainer: Oliver Mangold <omgold@dray.be>
# Made on Artix Linux - Plasma - Runit
pkgname=luxcorerender-bin
pkgver=2.5
pkgrel=1
pkgdesc="Physically correct, unbiased rendering engine (binary version)."
arch=('x86_64')
url="https://luxcorerender.org"
license=('Apache')
#Dependencies cheched through "ldd ./luxcoreui"
depends=(libx11 libxinerama libxrandr)
optdepends=('opencl-driver: for OPENCL gpu acceleration'
            'pyside2: for pyluxcoretools gui')
provides=(luxcorerender)
conflicts=(luxcorerender)
backup=()
options=()
install=
changelog=
source=(https://github.com/LuxCoreRender/LuxCore/releases/download/luxcorerender_v$pkgver/luxcorerender-v$pkgver-linux64.tar.bz2)
#Generated with "updpkgsums"
md5sums=('2ff6fe396409dbade7dfdbb16a673390')
sha256sums=('7732a2eecb64cfe3e04699dd048b3b8fb2cefcc3a31aadf3c501789d470e68c1')
sha512sums=('6604794cbafa4c177c975439a5713c10a648c3d842b83374399aec0c9f45517aa36399cbe1519b64247c2794221a1e7b2e3e1af5e5730d78f129ff25c20eafbf')


package() {
  cd "$pkgname-$pkgver"

  make DESTDIR="$pkgdir/" install
}
