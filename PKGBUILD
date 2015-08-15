# Maintainer: Alan Bunbury
pkgname=flybots-git
pkgver=0.2.0
pkgrel=1
pkgdesc="A three-dimensional clone of the classic bsd-robots game."
arch=('any')
url="https://github.com/bunburya/FlyingRobots"
license=('MIT')
depends=('python')
makedepends=('git')
options=(!emptydirs)
conflicts=(flybots)

_gitroot='git://github.com/bunburya/FlyingRobots.git'
_gitname=FlyingRobots

build() {
  cd "${srcdir}"

  # Download/update library
  msg "Attempting to fetch files from GitHub repository..."
  if [[ -d "${_gitname}" ]]; then
    (cd "${_gitname}" && git pull origin)
    msg "Local repository updated."
  else
    git clone "${_gitroot}" "${_gitname}"
    msg "Cloned repository from GitHub."
  fi

  cd "${_gitname}"
  python setup.py install --root="${pkgdir}/" --optimize=1
  ls
  install -D -m644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

# vim:set ts=2 sw=2 et:
