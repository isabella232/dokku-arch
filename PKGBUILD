# Maintainer: Morris Jobke <hey AT morrisjobke.de>
# Maintainer: Martin Mlynář <nexus+arch@smoula.net>
pkgname=dokku
pkgver=0.9.3
pkgrel=1
pkgdesc="Docker powered mini-Heroku in around 100 lines of Bash."
arch=(any)
url="https://github.com/dokku/dokku"
license=(MIT)
makedepends=(
	'plugn'
)
depends=(
	'docker'
	'nginx'
	'plugn>=0.3.0'
	'sshcommand>=0.7.0'
	'herokuish>=0.3.27'
	'openbsd-netcat'
	'gliderlabs-sigil'
	'lsb-release'
	'bind-tools'
	'python'
)

source=(
  "https://github.com/dokku/dokku/archive/v${pkgver}.zip"
  "${pkgname}.install"
)
sha256sums=('28f2cf4f0de5c2425da017c6dfba8559aca85fac267bb7067032587c1e32196e'
            '99a9d421fe100ef889f0f23be409289c8e627e55e6d5231c79a50d5da290eeb7')
install=${pkgname}.install

package() {
  cd "${srcdir}/"

  cd "$pkgname-$pkgver"

  install -Dm755 dokku "${pkgdir}/usr/bin/dokku"

  mkdir -p "${pkgdir}/var/lib/dokku/core-plugins/available"
  cp -r plugins/* "${pkgdir}/var/lib/dokku/core-plugins/available"
  find plugins/ -mindepth 1 -maxdepth 1 -type d -printf '%f\n' | while read plugin; do touch "${pkgdir}/var/lib/dokku/core-plugins/available/${plugin}/.core"; done

}
