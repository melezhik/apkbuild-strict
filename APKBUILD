# Contributor: Rasmus Thomsen <oss@cogitri.dev>
# Contributor: fossdd <fossdd@pwned.life>
# Maintainer: Celeste <cielesti@protonmail.com>
maintainer="Celeste <<cielesti_protonmail.com>"
pkgname=mautrix-whatsapp
pkgver=0.11.3
pkgrel=0
pkgdesc="Matrix-WhatsApp puppeting bridge"
url="https://maunium.net/go/mautrix-whatsapp"
arch="all"
license="AGPL-3.0-or-later"
makedepends="go olm-dev sqlite-dev"
install="$pkgname.pre-install $pkgname.pre-upgrade $pkgname.post-upgrade"
subpackages="$pkgname-openrc"
source="$pkgname-$pkgver.tar.gz::https://github.com/mautrix/whatsapp/archive/v$pkgver.tar.gz
	mautrix-whatsapp.initd
	mautrix-whatsapp.confd
	"
builddir="$srcdir/whatsapp-$pkgver"
options="net" # downloading go modules

export GOFLAGS="$GOFLAGS -tags=libsqlite3"
export GOCACHE="${GOCACHE:-"$srcdir/go-cache"}"
export GOTMPDIR="${GOTMPDIR:-"$srcdir"}"
export GOMODCACHE="${GOMODCACHE:-"$srcdir/go"}"

build() {
	export CGO_CFLAGS="$CFLAGS"
	export CGO_LDFLAGS="$LDFLAGS"
	local _goldflags="
		-X main.Tag=$pkgver
		-X 'main.BuildTime=$(date -d @"$SOURCE_DATE_EPOCH" '+%b %_d %Y, %H:%M:%S')'
		"

	go build -ldflags "$_goldflags" ./cmd/mautrix-whatsapp

	# write example config.yaml for installing in package()
	./mautrix-whatsapp -e
}

check() {
	go test -v ./...
}

package() {
	install -Dm755 mautrix-whatsapp \
		-t "$pkgdir"/usr/bin/
	install -Dm644 config.yaml \
		-t "$pkgdir"/etc/mautrix-whatsapp/

	install -Dm755 "$srcdir"/mautrix-whatsapp.initd \
		"$pkgdir"/etc/init.d/mautrix-whatsapp
	install -Dm644 "$srcdir"/mautrix-whatsapp.confd \
		"$pkgdir"/etc/conf.d/mautrix-whatsapp
}

sha512sums="
21bad4afbdd5a5d9337e9ab3a045dc6a2784d17a26f76728e73e423baaef3dd948c1ba09e4961341854dda4d257c2d5a0c3c6d811d1445c03c256013d4cf7934  mautrix-whatsapp-0.11.3.tar.gz
320ec426f033e93297bb3dd2ebe6996a9a677c53e76e8eb6d4b6f2bb24c1c756ef8d38d2dbb0d038369507fd9bf4864e73ab86783be3f6bbca150fe46a669841  mautrix-whatsapp.initd
9349b660273c63d2973f1b99ddbd98469dddc098157380603210159f17d3cb1eb55e71dbd21550b20d40831f4da320225e7c03441667e2750e30a2e1fa03acfe  mautrix-whatsapp.confd
"
