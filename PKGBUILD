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
provides=(luxcorerender)
source=("https://github.com/LuxCoreRender/LuxCore/releases/download/luxcorerender_v$pkgver/luxcorerender-v$pkgver-linux64.tar.bz2"
        https://github.com/d1nuc0m/AUR_luxcorerender-bin/blob/main/luxcorerender.desktop
        https://github.com/d1nuc0m/AUR_luxcorerender-bin/blob/main/luxcorerender.png)
# Generated with "updpkgsums"
md5sums=('2ff6fe396409dbade7dfdbb16a673390'
         'e6dfe782bc042c96a7068b11c975f3b7'
         '91c4662fd5ddc13569b211e0bd9fe32f')
sha256sums=('7732a2eecb64cfe3e04699dd048b3b8fb2cefcc3a31aadf3c501789d470e68c1'
            'b644c480bfadbca9c36965cc8b974dc8ceb4491aac060730e25a0281dd13f702'
            'c347c91b6c20e1f66d297893d752b589be21b9dc847fec73488956fc9d9f6372')
sha512sums=('6604794cbafa4c177c975439a5713c10a648c3d842b83374399aec0c9f45517aa36399cbe1519b64247c2794221a1e7b2e3e1af5e5730d78f129ff25c20eafbf'
            '42ae2e9e293b71a407bfbadaa9de780b0fb384fa63a384b7dc6814743cafc4bd0edfef6a40c016b0b5c0a5cded60e0fd4bc55fd0a37c5ce8a9521ae577d64a6d'
            'f7b150b1d2a917bdb776e8c748fb7b6e57bddf50ec7181ff6e1b7cf45260d04e863443f8f12089f7161da4ddbca70a37405857a2ab2688f06e063d5ee8dbca8e')


package() {
  # Creating target directories
  install -d "${pkgdir}/usr/bin"
  install -d "${pkgdir}/usr/lib"
  install -d "${pkgdir}/usr/share/applications"
  install -d "${pkgdir}/usr/share/luxcorerender"
  
  #Icon and Desktop files
  install -m644 luxcorerender.desktop "${pkgdir}/usr/share/applications"
  install -m644 luxcorerender.png "${pkgdir}/usr/share/luxcorerender"
    
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
