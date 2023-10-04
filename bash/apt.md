
### sudo apt --help
```bash
sudo apt --help
apt 2.4.10 (amd64)
Usage: apt [options] command

apt is a commandline package manager and provides commands for
searching and managing as well as querying information about packages.
It provides the same functionality as the specialized APT tools,
like apt-get and apt-cache, but enables options more suitable for
interactive use by default.

Most used commands:
  list - list packages based on package names
  search - search in package descriptions
  show - show package details
  install - install packages
  reinstall - reinstall packages
  remove - remove packages
  autoremove - Remove automatically all unused packages
  update - update list of available packages
  upgrade - upgrade the system by installing/upgrading packages
  full-upgrade - upgrade the system by removing/installing/upgrading packages
  edit-sources - edit the source information file
  satisfy - satisfy dependency strings

See apt(8) for more information about the available commands.
Configuration options and syntax is detailed in apt.conf(5).
Information about how to configure sources can be found in sources.list(5).
Package and version choices can be expressed via apt_preferences(5).
Security details are available in apt-secure(8).
                                        This APT has Super Cow Powers.
```

### sudo apt list --installed
### sudo apt list | grep 'package name'
```bash
 sudo apt list | grep mkcert

mkcert/jammy-updates,jammy-security 1.4.3-1ubuntu0.2 amd64

 sudo apt list | grep ^mk

mk-configure/jammy,jammy 0.36.0-1 all
mkalias/jammy,jammy 1.0.10-2.1 all
mkbootimg/jammy,jammy 1:10.0.0+r36-9 all
=== mkcert/jammy-updates,jammy-security 1.4.3-1ubuntu0.2 amd64 ===
mkchromecast-alsa/jammy,jammy 0.3.9~git20200902+db2964a-2 all
mkchromecast-gstreamer/jammy,jammy 0.3.9~git20200902+db2964a-2 all
mkchromecast-pulseaudio/jammy,jammy 0.3.9~git20200902+db2964a-2 all
mkchromecast/jammy,jammy 0.3.9~git20200902+db2964a-2 all
mkcue/jammy 1-7 amd64
mkdepend/jammy,jammy 0.0~svn45-3 all
mkdocs-bootstrap/jammy,jammy 1.1+dfsg-0.1 all
mkdocs-doc/jammy,jammy 1.1.2+dfsg-2ubuntu1 all
mkdocs-nature/jammy,jammy 0.4+dfsg-1 all
mkdocs/jammy,jammy 1.1.2+dfsg-2ubuntu1 all
mkelfimage/jammy 2.7-7build1 amd64
mkgmap-splitter/jammy,jammy 0.0.0+svn645-1 all
mkgmap/jammy,jammy 0.0.0+svn4885-1 all
mkgmapgui/jammy,jammy 1.1.ds-11 all
mklibs-copy/jammy 0.1.45 amd64
mklibs/jammy,jammy 0.1.45 all
mknfonts.tool/jammy 0.5-12build4 amd64
mkosi/jammy,jammy 12-1 all
mksh/jammy 59c-16 amd64
mktorrent/jammy 1.1-2build1 amd64
mkvtoolnix-gui/jammy 65.0.0-1 amd64
mkvtoolnix/jammy 65.0.0-1 amd64

```
### sudo apt install mkcert

### sudo apt-get --help
```bash
sudo apt-get --help
apt 2.4.10 (amd64)
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a command line interface for retrieval of packages
and information about them from authenticated sources and
for installation, upgrade and removal of packages together
with their dependencies.

Most used commands:
  update - Retrieve new lists of packages
  upgrade - Perform an upgrade
  install - Install new packages (pkg is libc6 not libc6.deb)
  reinstall - Reinstall packages (pkg is libc6 not libc6.deb)
  remove - Remove packages
  purge - Remove packages and config files
  autoremove - Remove automatically all unused packages
  dist-upgrade - Distribution upgrade, see apt-get(8)
  dselect-upgrade - Follow dselect selections
  build-dep - Configure build-dependencies for source packages
  satisfy - Satisfy dependency strings
  clean - Erase downloaded archive files
  autoclean - Erase old downloaded archive files
  check - Verify that there are no broken dependencies
  source - Download source archives
  download - Download the binary package into the current directory
  changelog - Download and display the changelog for the given package

See apt-get(8) for more information about the available commands.
Configuration options and syntax is detailed in apt.conf(5).
Information about how to configure sources can be found in sources.list(5).
Package and version choices can be expressed via apt_preferences(5).
Security details are available in apt-secure(8).
                                        This APT has Super Cow Powers.
```
 
