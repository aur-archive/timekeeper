# Maintainer: TDY <tdy@archlinux.info>

pkgname=timekeeper
pkgver=2.4.1
pkgrel=1
pkgdesc="A timer for speech and debate competitions"
arch=('any')
url="http://debate-ie-timer.sourceforge.net/"
license=('GPL')
depends=('desktop-file-utils' 'java-environment')
install=timekeeper.install
source=(http://downloads.sourceforge.net/project/debate-ie-timer/debate-ie-$pkgname/Speech%20and%20Debate%20Timekeeper%202.4.1/$pkgname-$pkgver-WinMacUnix.zip)
md5sums=('b735d91d34df1e06565e9cc35f52ac48')

package() {
  cd "$srcdir/Timekeeper"
  install -Dm644 Timekeeper.jar "$pkgdir/usr/share/java/$pkgname/$pkgname.jar"
  install -Dm644 lib/SuperWaba.jar "$pkgdir/usr/share/java/$pkgname/lib/SuperWaba.jar"
  install -Dm644 icons/Timekeeper64x64.png "$pkgdir/usr/share/pixmaps/$pkgname.png"

  # fix desktop file validation
  sed -e "/^Path=/c\Path=/usr/share/java/$pkgname" \
      -e "/^Icon=/c\$pkgname" \
      -e "/^Exec=/c\$pkgname" \
      -e "/^TerminalOptions=/d" \
      -e "/^MimeType=/d" -i "Speech and Debate Timekeeper.desktop"
  install -Dm644 "Speech and Debate Timekeeper.desktop" \
    "$pkgdir/usr/share/applications/$pkgname.desktop"

  # fix launcher paths
  sed -e "8c\java -classpath lib/SuperWaba.jar -jar $pkgname.jar" \
      -e "7a\cd /usr/share/java/$pkgname" -i $pkgname
  install -Dm755 $pkgname "$pkgdir/usr/bin/$pkgname"
}

# vim:set ts=2 sw=2 et:
