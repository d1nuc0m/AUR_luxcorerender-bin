# Maintainer: D1nuc0m <d1nuc0m@protonmail.com>
# Submitter and previous Maintainer: Oliver Mangold <omgold@dray.be>
# Thanks to bartus <arch-user-repo@bartus.33mail.com>
# Made on Artix Linux - Plasma - Runit
pkgname=luxcorerender-bin
pkgver=2.5
pkgrel=1
pkgdesc="Physically correct, unbiased rendering engine (binary version)."
arch=('x86_64')
url="https://luxcorerender.org/"
license=('Apache')
# Dependencies checked through "ldd ./luxcoreui", filtered with namcap
# openimagedenoise limited because of "libOpenImageDenoise.so.0"
# python3 because of pyluxcore
depends=(embree gtk3 "openimagedenoise<=1.2.4" "python>=3.0")
optdepends=('cuda: for OptiX/CUDA acceleration'
            'ocl-icd: for gpu acceleration'
            'opencl-driver: for OPENCL gpu acceleration'
            'pyside2: for pyluxcoretools gui')
provides=(luxcorerender=${pkgver})
conflicts=(luxcorerender)
replaces=('luxrays')
source=(https://github.com/LuxCoreRender/LuxCore/releases/download/luxcorerender_v$pkgver/luxcorerender-v$pkgver-linux64.tar.bz2)
# Generated with "updpkgsums"
md5sums=('2ff6fe396409dbade7dfdbb16a673390')
sha256sums=('7732a2eecb64cfe3e04699dd048b3b8fb2cefcc3a31aadf3c501789d470e68c1')
sha512sums=('6604794cbafa4c177c975439a5713c10a648c3d842b83374399aec0c9f45517aa36399cbe1519b64247c2794221a1e7b2e3e1af5e5730d78f129ff25c20eafbf')


package() {
  #Copying icon and desktop files to ${srcdir}
  cd ..
  cp luxcorerender.desktop ${srcdir}
  cp luxcorerender.png ${srcdir}
  
  #Adding Icon and Desktop files
  cd ${srcdir}
  install -m644 luxcorerender.desktop "${pkgdir}/usr/share/applications"
  install -m644 luxcorerender.png "${pkgdir}/usr/share/luxcorerender"
  
  # Creating target directories
  install -d "${pkgdir}/usr/bin"
  install -d "${pkgdir}/usr/lib"
  install -d "${pkgdir}/usr/share/applications"
  install -d "${pkgdir}/usr/share/luxcorerender"
  
  # CD to LuxCore directory
  cd "${srcdir}/LuxCore"
  
  # Executables
  install -m755 luxcoreui "${pkgdir}/usr/bin"
  
  # Libraries
  local _pyLibPath=$(python -c 'from sys import version_info;print("/usr/lib/python{}.{}".format(version_info.major,version_info.minor))')
  install -d "${pkgdir}/$_pyLibPath"
  install -m644 pyluxcore.so "${pkgdir}/$_pyLibPath"
  
  # pyluxcoretools
  cp pyluxcoretools.zip "${pkgdir}/usr/lib"
  
  # Shared data
  cp -r scenes "${pkgdir}/usr/share/luxcorerender"
  install -m644 AUTHORS.txt "${pkgdir}/usr/share/luxcorerender"
  install -m644 COPYING.txt "${pkgdir}/usr/share/luxcorerender"
  install -m644 README.md "${pkgdir}/usr/share/luxcorerender"
}
