# Maintainer: Mikael Eriksson <mikael_eriksson@miffe.org>
# Contributor: Maxime Gauduin <alucryd@archlinux.org>
# Contributor: Rob Sletten <rsletten@gmail.com>
# Contributor: Tom Moore <t.moore01@gmail.com>
# Contributor: monty <linksoft@gmx.de>
# Contributor: Jon Wiersma <archaur@jonw.org>
# Contributor: Arthur <arthur.darcet@m4x.org>
# Contributor: Praekon <praekon@googlemail.com>

# Based on the plex-media-server package by Maxime Gauduin.

pkgname=plex-media-server-plexpass
pkgver=0.9.14.2.1547
_pkgsum=60c867f
pkgrel=1
pkgdesc='Plex Media Server (PlexPass version)'
arch=('arm' 'armv7h' 'i686' 'x86_64')
url='https://plex.tv/'
license=('custom')
options=('!emptydirs')
provides=('plex-media-server')
conflicts=('plex-media-server')
backup=('etc/conf.d/plexmediaserver')
install='plex-media-server.install'
source=('plexmediaserver.conf.d'
        'plexmediaserver.service'
        'plex.sysusers'
        'terms.txt')
source_arm=("https://downloads.plex.tv/plex-media-server/${pkgver}-${_pkgsum}/PlexMediaServer-${pkgver}-${_pkgsum}-arm.spk")
source_armv7h=("https://downloads.plex.tv/plex-media-server/${pkgver}-${_pkgsum}/PlexMediaServer-${pkgver}-${_pkgsum}-arm7.spk")
source_i686=("https://downloads.plex.tv/plex-media-server/${pkgver}-${_pkgsum}/plexmediaserver-${pkgver}-${_pkgsum}.i386.rpm")
source_x86_64=("https://downloads.plex.tv/plex-media-server/${pkgver}-${_pkgsum}/plexmediaserver-${pkgver}-${_pkgsum}.x86_64.rpm")
sha256sums=('7ab1ee8da9012d257b7f473fb79d76b201ca592cbe3722f977a43b58bfad180e'
            '9da45cc3951ae03086ec663e6273c2de0183495fd15dc34ddd9aa100346d4d3a'
            'ebf153d5789f9d24cb98ae607d227286e1da6ce54e149c8be4f47e08ee729573'
            '7bb97271eb2dc5d1dcb95f9763f505970d234df17f1b8d79b467b9020257915a')
sha256sums_arm=('c0092fbafe6a3bd8bc8e8bc3fe4b68099e0dc9f64e5de9ba6976f74d3957402e')
sha256sums_armv7h=('43b0e279f6fd09e15e8465c39caa1cac31252b9714b75a60b0605ac297810038')
sha256sums_i686=('a76ddad47fee5948a7c667f5a4b485789bedef0868b9fcdc073d77d0c2823ba6')
sha256sums_x86_64=('9cbabc3365fe091ce1ff4092515670d4bf56b375a292daded5563ab4950f2394')

prepare() {
  if [[ $CARCH =~ arm* ]]; then
    mkdir -p usr/lib/plexmediaserver
    tar -xf package.tgz -C usr/lib/plexmediaserver/
  fi
}

package() {
  install -dm 755 "${pkgdir}"/{opt,etc/conf.d,usr/lib/systemd/system}
  cp -dr --no-preserve='ownership' usr/lib/plexmediaserver "${pkgdir}"/opt/
  install -m 644 plexmediaserver.service "${pkgdir}"/usr/lib/systemd/system/
  install -m 644 plexmediaserver.conf.d "${pkgdir}"/etc/conf.d/plexmediaserver
  install -Dm644 "$srcdir/plex.sysusers" "$pkgdir/usr/lib/sysusers.d/plex.conf"

  install -dm 755 "${pkgdir}"/usr/share/licenses/${pkgname}
  install -m 644 terms.txt "${pkgdir}"/usr/share/licenses/${pkgname}/
}

# vim: ts=2 sw=2 et:
