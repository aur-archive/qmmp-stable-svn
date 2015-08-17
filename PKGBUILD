# Contributor: h31 <h31mail@yandex.com>
# Maintainer: Andrew Panchenko <panchenkoac at gmail>
pkgname='qmmp-stable-svn'
_svnname='qmmp-0.8'
pkgver=0.8.2.svn.r4441
pkgrel=1
pkgdesc="A Qt4 based audio-player - svn version (stable 0.7.x branch)"
arch=('i686' 'x86_64')
url="http://qmmp.ylsoftware.com"
license=('GPL')
depends=('qt4>=4.6' 'alsa-lib>=1.0.1' 'taglib>=1.6' 'curl>=7.16' 'hicolor-icon-theme')
makedepends=('subversion' 'cmake>=2.6.0')
optdepends=( 'libmms>=0.4' 'flac>=1.1.3' 'libmpcdec>=1.2.6' 'jack>=0.102.5'
	'libsamplerate>=0.1.2' 'libmodplug>=0.8.4' 'libsndfile>=1.0.17'
	'wavpack>=4.41' 'libpulse>=0.9.15' 'ffmpeg' 'libcdio>=0.80'
	'faad2>=2.6.1' 'libgme>=0.5.5' 'wildmidi>=0.2.3.4'
	'libbs2b>=3.0.0' 'projectm>=1.2.0' 'enca>=1.9' 'mplayer' 'libmad' 'libvorbis' 'libogg')
provides=('qmmp' 'qmmp-svn')
conflicts=('qmmp' 'qmmp-svn')
install=${pkgname}.install
source=(${pkgname}::svn+http://qmmp.googlecode.com/svn/branches/${_svnname})
md5sums=('SKIP')

pkgver() {
  cd ${srcdir}/$pkgname
  echo "$(cat qmmp.pri | grep QMMP_VERSION | cut -d ' ' -f3).svn.r$(svnversion)"
}

build() {
  cd ${srcdir}/$pkgname
  cmake . -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_INSTALL_LIBDIR=/usr/lib
  make
}

package() {
  cd ${srcdir}/$pkgname
  make DESTDIR=${pkgdir} install

  if [[ $CARCH == 'x86_64' ]]; then
    mv $pkgdir/usr/lib64 $pkgdir/usr/lib
  fi
}
