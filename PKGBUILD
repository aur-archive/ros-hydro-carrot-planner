# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - This planner attempts to find a legal place to put a carrot for the robot to follow."
url='http://wiki.ros.org/carrot_planner'

pkgname='ros-hydro-carrot-planner'
pkgver='1.11.11'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('BSD')

ros_makedepends=(ros-hydro-base-local-planner
  ros-hydro-costmap-2d
  ros-hydro-roscpp
  ros-hydro-catkin
  ros-hydro-nav-core
  ros-hydro-tf
  ros-hydro-pluginlib)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]}
  eigen3)

ros_depends=(ros-hydro-base-local-planner
  ros-hydro-costmap-2d
  ros-hydro-roscpp
  ros-hydro-nav-core
  ros-hydro-tf
  ros-hydro-pluginlib)
depends=(${ros_depends[@]}
  eigen3)

_tag=release/hydro/carrot_planner/${pkgver}-${_pkgver_patch}
_dir=carrot_planner
source=("${_dir}"::"git+https://github.com/ros-gbp/navigation-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/hydro/setup.bash ] && source /opt/ros/hydro/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/hydro \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
