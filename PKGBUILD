pkgname=atomicparsley
pkgver=0.9.4
pkgrel=1
pkgdesc="Console application for reading, parsing and setting mp4 meta-data"
arch=('x86_64')
url="https://github.com/wez/atomicparsley"
license=('GPL')
depends=('zlib')
makedepends=(
    'autoconf'
    'automake'
)
source=(
    "${pkgname}.tar.gz::${url}/archive/${pkgver}.tar.gz"
    'kaos.patch'
)
sha1sums=(
    '7b92ac01fdba91eea38d7947226b905528f94b79'
    'd1c245b6891ef548a64720a0c8781417126b1de5'
)

prepare() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    patch -Np1 -i "${srcdir}/kaos.patch"
    ./autogen.sh
}

build() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    ./configure --prefix=/usr
    make
}

package() {
    cd "${srcdir}/${pkgname}-${pkgver}"
    make DESTDIR="${pkgdir}" install
    mv "${pkgdir}/usr/bin/AtomicParsley" "${pkgdir}/usr/bin/atomicparsley"
}
