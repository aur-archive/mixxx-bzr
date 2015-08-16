#Mantainer : M0Rf30
pkgname=mixxx-bzr
pkgver=3312
pkgrel=1
pkgdesc="Digital DJ mixing software"
arch=('i686' 'x86_64')
url="http://www.mixxx.org/"
license=('GPL2')
depends=('libid3tag' 'libmad' 'portaudio' 'qt4' 'libogg' 'libshout' 'libvorbis' 'libsndfile' 'taglib' 'portmidi' 'protobuf')
makedepends=('bzr' 'scons>=0.98' 'pkgconfig>=0.15.0')
optdepends=('faad2: M4A support' 
	    'mp4v2: M4A support' 
	    'libshout: Shoutcast support')
provides=(mixxx)
conflicts=(mixxx1.10-bzr mixxx1.8-bzr mixxx1.9-bzr mixxx)
_bzrbranch=lp:mixxx
_bzrname=mixxx

build() {
  cd ${srcdir}
  msg "Connecting to BZR server..."

  if [ -d ${srcdir}/${_bzrname} ] ; then
    cd ${_bzrname} && bzr pull ${_bzrbranch}
    msg "Local repository updated."
  else
    bzr co ${_bzrbranch}
  fi
  
  cd ${startdir}

  msg "BZR checkout done or server timeout"
  msg "Starting make..."

  cd "$srcdir/$_bzrname/$_bzrname"
   scons qtdir=/usr/lib/qt4 prefix=/usr install_root=$pkgdir/usr tuned=1 || return 1
   scons qtdir=/usr/lib/qt4 prefix=/usr install_root=$pkgdir/usr install || return 1


}
