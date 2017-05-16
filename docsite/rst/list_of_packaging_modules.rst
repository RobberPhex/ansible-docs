Packaging Modules
`````````````````

.. toctree:: :maxdepth: 1


Language
--------

.. toctree:: :maxdepth: 1

  composer (E) - Dependency Manager for PHP <composer_module>
  cpanm (E) - Manages Perl library dependencies. <cpanm_module>
  easy_install - Installs Python libraries <easy_install_module>
  gem - Manage Ruby gems <gem_module>
  npm (E) - Manage node.js packages with npm <npm_module>
  pip - Manages Python library dependencies. <pip_module>

Os
--

.. toctree:: :maxdepth: 1

  apt - Manages apt-packages <apt_module>
  apt_key - Add or remove an apt key <apt_key_module>
  apt_repository - Add and remove APT repositories <apt_repository_module>
  apt_rpm - apt_rpm package manager <apt_rpm_module>
  homebrew (E) - Package manager for Homebrew <homebrew_module>
  homebrew_cask (E) - Install/uninstall homebrew casks. <homebrew_cask_module>
  homebrew_tap (E) - Tap a Homebrew repository. <homebrew_tap_module>
  layman (E) - Manage Gentoo overlays <layman_module>
  macports (E) - Package manager for MacPorts <macports_module>
  openbsd_pkg (E) - Manage packages on OpenBSD. <openbsd_pkg_module>
  opkg (E) - Package manager for OpenWrt <opkg_module>
  pacman (E) - Manage packages with I(pacman) <pacman_module>
  pkgin (E) - Package manager for SmartOS <pkgin_module>
  pkgng (E) - Package manager for FreeBSD >= 9.0 <pkgng_module>
  pkgutil (E) - Manage CSW-Packages on Solaris <pkgutil_module>
  portage (E) - Package manager for Gentoo <portage_module>
  portinstall (E) - Installing packages from FreeBSD's ports system <portinstall_module>
  redhat_subscription - Manage Red Hat Network registration and subscriptions using the C(subscription-manager) command <redhat_subscription_module>
  rhn_channel - Adds or removes Red Hat software channels <rhn_channel_module>
  rhn_register - Manage Red Hat Network registration using the C(rhnreg_ks) command <rhn_register_module>
  rpm_key - Adds or removes a gpg key from the rpm db <rpm_key_module>
  svr4pkg (E) - Manage Solaris SVR4 packages <svr4pkg_module>
  swdepot (E) - Manage packages with swdepot package manager (HP-UX) <swdepot_module>
  urpmi (E) - Urpmi manager <urpmi_module>
  yum - Manages packages with the I(yum) package manager <yum_module>
  zypper (E) - Manage packages on SUSE and openSUSE <zypper_module>
  zypper_repository (E) - Add and remove Zypper repositories <zypper_repository_module>



.. note::
    -  (D): This marks a module as deprecated, which means a module is kept for backwards compatibility but usage is discouraged.  The module documentation details page may explain more about this rationale.
    -  (E): This marks a module as 'extras', which means it ships with ansible but may be a newer module and possibly (but not neccessarily) less activity maintained than 'core' modules.
    - Tickets filed on modules are filed to different repos than those on the main open source project. Core module tickets should be filed at `ansible/ansible-modules-core on GitHub <http://github.com/ansible/ansible-modules-core>`_, extras tickets to `ansible/ansible-modules-extras on GitHub <http://github.com/ansible/ansible-modules-extras>`_
