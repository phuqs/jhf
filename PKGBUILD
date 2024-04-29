# Maintainer: Mark Wagie <mark dot wagie at proton dot me>
# Contributor: Matthew McGinn <mamcgi at gmail dot com>
# Contributor: alicewww <almw at protonmail dot com>
pkgname=mullvad-vpn-bin
pkgver=2024.2
pkgrel=1
pkgdesc="The Mullvad VPN client app for desktop"
arch=('x86_64' 'aarch64')
url="https://www.mullvad.net"
license=('GPL-3.0-or-later')
depends=('alsa-lib' 'gtk3' 'iputils' 'libnftnl' 'libnotify' 'nss')
provides=('mullvad-vpn')
conflicts=('mullvad-vpn')
install='mullvad-vpn.install'
source=('mullvad-vpn.sh')
source_x86_64=("https://github.com/mullvad/mullvadvpn-app/releases/download/$pkgver/MullvadVPN-${pkgver}_amd64.deb"{,.asc})
source_aarch64=("https://github.com/mullvad/mullvadvpn-app/releases/download/$pkgver/MullvadVPN-${pkgver}_arm64.deb"{,.asc})
sha256sums=('a59c29f07b4eab9af56f0e8be42bae0d83726f5185e88de0c5a48f4098c3c0a4')
sha256sums_x86_64=('c8e4b5574538816310d777a214ab01e0c9fba31411e6d42b3564fd2cec4357f3'
                   'SKIP')
sha256sums_aarch64=('04385575d841fa847d8c400793b51b60d327c266fe174f47ea218d04103f3254'
                    'SKIP')
validpgpkeys=('A1198702FC3E0A09A9AE5B75D5A1D4F266DE8DDF') # Mullvad (code signing) <admin@mullvad.net>

package() {
  bsdtar -xvf data.tar.xz -C "$pkgdir/"
  chmod 4755 "$pkgdir/opt/Mullvad VPN/chrome-sandbox"

  # Link to the GUI binary
  install -m755 "$srcdir/mullvad-vpn.sh" "$pkgdir/usr/bin/mullvad-vpn"

  # Move ZSH completions to correct directory
  mv "$pkgdir/usr/local/share/zsh" "$pkgdir/usr/share/"
  rm -rf "$pkgdir/usr/local"
}
