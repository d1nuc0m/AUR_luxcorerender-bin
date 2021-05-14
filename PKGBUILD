# Maintainer: D1nuc0m <d1nuc0m@protonmail.com>
# Submitter and previous Maintainer: Oliver Mangold <omgold@dray.be>
# Thanks to bartus <arch-user-repo@bartus.33mail.com>, qub1750ul <dev.gmasino@pm.me>, Zekromaster <dev@zekromaster.net>

_pkgname=luxcorerender
pkgname="${_pkgname}-bin"
pkgver=2.5
pkgrel=1
pkgdesc="Physically correct, unbiased rendering engine"
arch=('x86_64')
url="https://luxcorerender.org/"
license=('Apache')
# Dependencies checked through "ldd ./luxcoreui", filtered with namcap
# python3 because of pyluxcore
depends=(embree gtk3 openimagedenoise "python>=3.0")
makedepends=("python>=3.0")
optdepends=('cuda: OptiX/CUDA acceleration'
            'ocl-icd: gpu acceleration'
            'opencl-driver: OPENCL gpu acceleration'
            'pyside2: pyluxcoretools gui')
provides=(${_pkgname})
source=("https://github.com/LuxCoreRender/LuxCore/releases/download/luxcorerender_v${pkgver}/luxcorerender-v${pkgver}-linux64.tar.bz2"
        luxcorerender.desktop
        luxcorerender.png
        pyluxcore.desktop)
md5sums=('2ff6fe396409dbade7dfdbb16a673390'
         'f49296352f6ee987e845a5da5c4e1eb8'
         '2bc4e53b884e27f57f42a642faeb9e12'
         '501ac7b1457817a31f3cee55b0a5adfb')
sha256sums=('7732a2eecb64cfe3e04699dd048b3b8fb2cefcc3a31aadf3c501789d470e68c1'
            'cbbc002ba3c51ea66052b7b7a57f240c8e6f763c1d8840b7566bf254598dc12a'
            '8dd4def9ff9e0b4c5e2fefaf90822f605ee515b2a886e283f2c32e59320f4c68'
            '1ff655fa893f5df5c8a32bea65c67f78201433c2736a583637fce2c683bc8d01')
sha512sums=('6604794cbafa4c177c975439a5713c10a648c3d842b83374399aec0c9f45517aa36399cbe1519b64247c2794221a1e7b2e3e1af5e5730d78f129ff25c20eafbf'
            'bcd64a558cf68e7fecbda466f816d16dacef6f6192d1a6022b4c77682fcbb0a31485e83678a5709d426a99b31b1b1cd7c24261f631a83f557c90c4e68db13a0a'
            'e551dd77e54f53179a14e311cd6520717dd9ca3f135a9fbd8f646c35ee70aaf6cdbb3e8b8ea6848877aa26ec7c17ec01b277af71a0da3077e430fc53d6c61e5c'
            '77beb9054516b80f06b24ea240bfa5059aad0926b4085032d38273ef1867ce91a355339fa7cf6a4b86420db5af5a11fecb002d74fb6fed9ff5616bd4f0ac24fe')

package() {

  local pkgshr="${pkgdir}/usr/share/${_pkgname}"
  
  install -m 644 -Dt "${pkgdir}/usr/share/applications" luxcorerender.desktop pyluxcore.desktop
  
  cd "${srcdir}/LuxCore"
  
  install -m 755 -Dt "${pkgdir}/usr/bin" luxcoreui
  # Newer versions of Open Image Denoise do not include libOpenImageDenoise.so.0
  install -m 644 -Dt "${pkgdir}/opt/${_pkgname}" libOpenImageDenoise.so.0 pyluxcore.so pyluxcoretools.zip
  install -m 644 -Dt "$pkgshr" AUTHORS.txt COPYING.txt README.md "${srcdir}/luxcorerender.png"
  cp -r scenes "${pkgshr}/"
}
