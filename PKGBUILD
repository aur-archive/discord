# Maintainer: Ruan K. Felisbino <ruan.klein@gmail.com>

pkgname=discord
pkgver=3.2.1
pkgrel=3
pkgdesc="Generate Binaural and Chronaural beats for Brainwave Entrainment"
arch=('i686' 'x86_64')
url="http://discord.sourceforge.net/"
license=('GPL')
install=$pkgname.install
depends=('alsa-lib' 'libsamplerate' 'libsndfile' 'flac' 'libogg' 'libvorbis')
makedepends=('glibc')
optdepends=('python2: to use convert_sbg_to_discord.py script')
conflicts=('discord')
source=("http://sourceforge.net/projects/discord/files/$pkgname-$pkgver.tar.bz2")
md5sums=('7f7341f01032314f618e9ae5bb6137e6')

build() {
  cd $srcdir/$pkgname-$pkgver
  ./configure --prefix=/usr
  
  make || return 1
}

package() {
  cd $srcdir/$pkgname-$pkgver
  make DESTDIR=$pkgdir install
  
  sed -i '1s/python$/python2/' $pkgdir/usr/share/discord/convert_sbg_to_discord.py
  chmod 755 $pkgdir/usr/share/discord/convert_sbg_to_discord.py
}
