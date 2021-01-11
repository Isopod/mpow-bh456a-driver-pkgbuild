# Maintainer: Philip Zander (isopod) <philip.zander+arch at gmail dot com>

pkgname=mpow-bh456a-driver
pkgver=20200610.0.0
pkgrel=1
pkgdesc='Driver for the MPOW BH456A USB bluetooth dongle (Realtek RTL8761BU)'
srcname='20200610_LINUX_BT_DRIVER'
url='https://www.xmpow.com/'
arch=(x86_64)
license=(GPL2)
makedepends=(linux patch coreutils gcc make)
source=(
	'https://mpow.s3-us-west-1.amazonaws.com/mpow_MPBH456AB_driver+for+Linux.tgz'
	'prefix.patch'
)
sha256sums=(
	'74001cd412363485751a8e11dda7de54919de51a74d7f060ce489d0a9291040b'
	'a1b7d55a70e900676f73e7e59fbebe78af40746f86d87450d0b0bc89d35789c5'
)

prepare() {
	cd "${srcdir}/${srcname}"
	patch -p1 -i "${srcdir}/prefix.patch"
}

build() {
	mkdir -p "${srcdir}/build/usr/bin"

	cd "${srcdir}/${srcname}"
	make install INTERFACE=all PREFIX="${srcdir}/build/usr"
}

package() {
	cp -r "${srcdir}/build/usr" "${pkgdir}"
}
