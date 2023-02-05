# Maintainer: Voron-Orel
# Contributor: Voron-Orel

pkgname=purevpn-cli
pkgver=2.0.0
pkgrel=1
arch=(x86_64)
pkgdesc='Package to install PureVPN-cli'
url=https://www.purevpn.com/
license=(custom)
options=(!strip)
depends=('wget'
         'gzip'
         'openvpn'
         'wireguard-tools'
         'net-tools'
         'openresolv'
         'inetutils')
install=purevpn-cli.install
source_x86_64=("${pkgname}.gz::https://purevpn-dialer-assets.s3.amazonaws.com/cross-platform/linux-cli/${pkgver}/${pkgname}.gz"
               "pured-linux-x64.gz::https://purevpn-dialer-assets.s3.amazonaws.com/cross-platform/linux-daemon/1.3.0/pured-linux-x64.gz"
               "atom-update-resolve-conf::https://purevpn-dialer-assets.s3.amazonaws.com/cross-platform/atom-update-resolve-conf"
               "atom-update-resolve-conf-wg::https://purevpn-dialer-assets.s3.amazonaws.com/cross-platform/atom-update-resolve-conf-wg"
               "purevpn-cli.install"
               "pured.service")
sha512sums_x86_64=('6759a1d57c3217fb4b0c13a9814276e2896a7aec31ca8b900a88b7208f841ca32c9cbf012b4f2d1855ebaab1db47f86610a46052a1954eb43ecc7e6b6e4020a2' 
                   'a70cd8ab6499b1e3c80b3a66e2ae789de57b62c2ae8d0748daf5acd95269fc04020aa0ca23435361f189abea808b3762e3b6c4f0dee80b37ab5112065087ffd9'
                   '332475c9b2211e98fa77929525b828d32f7e6175614f5154c8c272c8b1b7b7b3e84ce0bc875c47b7cf1307cc76c2b6a028029bf5432afa5508a9f03b69f34f94'
                   '31bee698fedfc3b7ed5eccf9cf40fadcfe54e15712577fda0d2b30855397d5264ab1d648b297bcbbf08f054d1c0ea5f5de1e73c9792d348776a4f4d8ee574131'
                   'cf93647f66542cccc36a12f98da30961ffbb3932cc91d2bc9d244ac583f215f91aed2121fdfd47373d6859cdfcf9db6e909e985d3c61740c98a3d10ba1ebeb2a'
                   'af9f5765d28ae0d987b1e751c0f13b3cd640d1dd7a8b432287d69d4ac16e6345280af0645a791caec5f0ad3c9ca86646aeb275b89324ce37f05ac73e638bb3e3'
                   )

package() {

  echo "Configure the files"
  mkdir -p ${pkgdir}/etc/pure-linux-cli
  chmod +x $srcdir/${pkgname}
  chmod +x $srcdir/pured-linux-x64
  chmod +x $srcdir/atom-update-resolve-conf
  chmod +x $srcdir/atom-update-resolve-conf-wg
    
# Configure systemd service
  echo "Configuring systemd service"
  install -Dm644 "${srcdir}/pured.service" -t "${pkgdir}/etc/systemd/system/"
  
# Configure binary and license
  echo "Configuring binary and license"
  install -Dm755 "${srcdir}/${pkgname}" -t "${pkgdir}/usr/bin/"
  install -Dm755 "${srcdir}/pured-linux-x64" -t "${pkgdir}/usr/bin/"
  install -Dm755 "${srcdir}/atom-update-resolve-conf" -t "${pkgdir}/etc/pure-linux-cli/"
  install -Dm755 "${srcdir}/atom-update-resolve-conf-wg" -t "${pkgdir}/etc/pure-linux-cli/"
  
} 
