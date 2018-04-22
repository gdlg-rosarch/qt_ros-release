# Script generated with Bloom
pkgdesc="ROS - Example qt programs, generated from code similar to that used by the roscreate-qt-pkg script and styled on roscpp_tutorials."


pkgname='ros-kinetic-qt-tutorials'
pkgver='0.2.10_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('qt4'
'ros-kinetic-catkin'
'ros-kinetic-message-generation'
'ros-kinetic-qt-build'
'ros-kinetic-roscpp'
'ros-kinetic-std-msgs'
)

depends=('qt4'
'ros-kinetic-message-runtime'
'ros-kinetic-qt-build'
'ros-kinetic-roscpp'
'ros-kinetic-std-msgs'
)

conflicts=()
replaces=()

_dir=qt_tutorials
source=()
md5sums=()

prepare() {
    cp -R $startdir/qt_tutorials $srcdir/qt_tutorials
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

