# iLCInstall for EUTelescope

Installation script that enable a fully automated installation of EUTelescope and its dependencies, based on the installation of iLCSoft (original version can be found on [GitHub](https://github.com/iLCSoft/iLCInstall)).


## General Usage

The script can be called with the following syntax:
```
./ilcsoft-install install.cfg [ -p, -i ]
```
options description:
* -p to preview installation environment
* -i to install the software

If called without options a summary of the installation is displayed. Examples of configuration files can be found under releases.


## Usage for EUTelescope:

* prerequisites: some installations (e.g. java) are not supported in ilcinstall, these packages need to be available on the system, paths can be changed in releases/release-versions.py

* for debian/ubuntu distributions you may need to install a few packages beforehand such as (TO BE CHECKED):
  ```
  apt-get install build-essential cmake subversion libmysqlclient-dev freeglut3-dev zlib1g-dev \
  default-jdk libxpm-dev libxmu-dev lesstif2-dev
  ```

* In general, it is possible to set the path for the installation to elsewhere by setting the environment variable ILCSOFT, by default it is on the parent directory where the iLCInstaller is cloned to.

### LOCAL (standalone version)

1. Check the prerequisites on your system.
2. Choose installation location and define path using the ILCSOFT environment variable:
  ```
  export ILCSOFT=/PATH-WHERE-TO-INSTALL
  mkdir -p $ILCSOFT
  ```
3. Get iLCInstall code:
  ```
  cd $ILCSOFT
  git clone -b master https://github.com/eutelescope/ilcinstall
  ```
4. Run the installation using the appropiate installation configuration:
  ```
  cd ilcinstall
  ./ilcsoft-install -i releases/release-local-standalone.cfg
  ```

### LOCAL (nocmakenoroot version)

1. Check the prerequisites on your system. Source your CMake and ROOT installations.
2. Choose installation location and define path using the ILCSOFT environment variable:
  ```
  export ILCSOFT=/PATH-WHERE-TO-INSTALL
  mkdir -p $ILCSOFT
  ```
3. Get iLCInstall code:
  ```
  cd $ILCSOFT
  git clone -b master https://github.com/eutelescope/ilcinstall
  ```
4. Run the installation using the appropiate installation configuration:
  ```
  cd ilcinstall
  ./ilcsoft-install -i releases/release-local-nocmakenoroot.cfg
  ```

### DESY NAF (standalone version)

1. Login to NAF.
2. Enable the right compilers, modern git version and environments:
  ```
  scl enable devtoolset-4 rh-git29 bash
  ```
3. Choose installation location (e.g. on dust) and define path using the ILCSOFT environment variable: 
  ```
  export ILCSOFT=/nfs/dust/GROUP/user/USER/NAME
  mkdir -p $ILCSOFT
  ```
4. Get iLCInstall code:
  ```
  cd $ILCSOFT
  git clone -b master https://github.com/eutelescope/ilcinstall
  ```
5. Run the installation using the appropiate installation configuration:
  ```
  cd ilcinstall
  ./ilcsoft-install -i releases/release-desynaf-standalone.cfg
  ```

### DESY NAF (cvmfs version)

1. Login to NAF (current default is SLC6 machines).
2. Enable the modern git version for bash: and :
  ```
  scl enable rh-git29 bash
  ```
3. Source ROOT-environment from CVMFS appropiate to your system:
  ```
  //for SLC6 machine
  source /cvmfs/sft.cern.ch/lcg/releases/LCG_94/ROOT/6.14.04/x86_64-slc6-gcc62-opt/ROOT-env.sh
  
  //for Centos7 machine
  source /cvmfs/sft.cern.ch/lcg/releases/LCG_94/ROOT/6.14.04/x86_64-centos7-gcc62-opt/ROOT-env.sh
  ```
4. Choose installation location (e.g. on dust) and define path using the ILCSOFT environment variable:
  ```
  export ILCSOFT=/nfs/dust/GROUP/user/USER/NAME
  mkdir -p $ILCSOFT
  ```
5. Get iLCInstall code:
  ```
  cd $ILCSOFT
  git clone -b master https://github.com/eutelescope/ilcinstall
  ```
6. Run the installation	using the appropiate installation configuration:
  ```
  cd ilcinstall
  ./ilcsoft-install -i releases/release-desynaf-cvmfs.cfg
  ```

### CERN LXPLUS (cvmfs version)

1. Login to LXPLUS (by default it is Centos7, but you can also connect to SLC6 with `lxplus6.cern.ch` as login node).
2. Enable modern git version for bash:
  ```
  scl enable rh-git29 bash
  ```
3. Source ROOT-environment from CVMFS appropiate to your system:
  ```
  //for SLC6 machine
  source /cvmfs/sft.cern.ch/lcg/releases/LCG_94/ROOT/6.14.04/x86_64-slc6-gcc62-opt/ROOT-env.sh
  
  //for Centos7 machine
  source /cvmfs/sft.cern.ch/lcg/releases/LCG_94/ROOT/6.14.04/x86_64-centos7-gcc62-opt/ROOT-env.sh
  ```
4. Choose installation location (e.g. on eos) and define path using the ILCSOFT environment variable:
  ```
  export ILCSOFT=/eos/user/USERINTIAL/USERNAME
  mkdir -p $ILCSOFT
  ```
5. Get iLCInstall code:
  ```
  cd $ILCSOFT
  git clone -b master https://github.com/eutelescope/ilcinstall
  ```
6. Run the installation using the appropiate installation configuration:
  ```
  cd ilcinstall
  ./ilcsoft-install -i releases/release-lxplus-cvmfs.cfg
  ```

### Informations/Caveats:

* A standalone version for LXPLUS is not supported currently, because of the required ROOT installation. Anyway, if
CVMFS is mounted on your system, it is advisable to link it with the installation due to the speed up in time.
For this check the releases named with cvmfs to get an idea.

* Sometimes it is possible that a dependency for EUTelescope is changing which can have then implications on the 
installation process itself. In case of problems with the installation, please report on the 
[GitHub issue tracker](https://github.com/eutelescope/iLCInstall/issues).

* When running EUTelescope, go to the EUTelescope installation with `cd $EUTELESCOPE/RELEASEVERSION/Eutelescope/master`
and source the environment script `build_env.sh`. If you started from a fresh terminal, do NOT forget to also prepare
the general environment (e.g. when using CVMFS, source the ROOT environment). Maybe it is an option to add this to 
your `.bashrc`.

* For information about EUTelescope itself, please refer to its [GitHub](https://github.com/eutelescope/eutelescope).


## License and Copyright
Copyright (C), iLCInstall Authors

iLCInstall is distributed under the [GPLv3 License](http://www.gnu.org/licenses/gpl-3.0.en.html)
[![License](https://www.gnu.org/graphics/gplv3-127x51.png)](https://www.gnu.org/licenses/gpl-3.0.en.html)

iLCInstall is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License long with this program.  If not, see <http://www.gnu.org/licenses/>.
