# Maintainer: Andrew Lubawy <dlubawy@gmail.com>

_pkgname="rune"

pkgname="google-rune-git"
pkgver=0.1.0
pkgrel=1
pkgdesc="Google's Rune programming language"
arch=('x86_64')
url="https://github.com/google/rune.git"
license=('Apache')
depends=(
    'bison'
    'flex'
    'gmp'
    'clang'   
    'datadraw'
)

_commit="6db80f3ae707605e34c93ee5448671ba0e5b7198"
source=("https://github.com/google/rune/archive/$_commit/main.zip")
md5sums=('5ab73208dc6ffbedaa49cc048352aae7')

prepare() {
    ln -s $_pkgname-$_commit $_pkgname-$_commit/../rune
    cd $_pkgname-$_commit/..
    git clone https://github.com/pornin/CTTK.git
    cp CTTK/inc/cttk.h CTTK
}

build() {
    cd $_pkgname-$_commit
    make PREFIX="/usr"
}

check() {
    cd $_pkgname-$_commit
    ./runtests.sh
}

package() {
    cd $_pkgname-$_commit
    make PREFIX="$pkgdir/usr/" install
}
