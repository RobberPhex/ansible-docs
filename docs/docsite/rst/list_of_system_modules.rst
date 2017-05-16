System Modules
``````````````

.. toctree:: :maxdepth: 1

  aix_inittab - Manages the inittab on AIX. <aix_inittab_module>
  alternatives - Manages alternative programs for common commands <alternatives_module>
  at - Schedule the execution of a command or script file via the at command. <at_module>
  authorized_key - Adds or removes an SSH authorized key <authorized_key_module>
  beadm - Manage ZFS boot environments on FreeBSD/Solaris/illumos systems. <beadm_module>
  capabilities - Manage Linux capabilities <capabilities_module>
  cron - Manage cron.d and crontab entries. <cron_module>
  cronvar - Manage variables in crontabs <cronvar_module>
  crypttab - Encrypted Linux block devices <crypttab_module>
  debconf - Configure a .deb package <debconf_module>
  facter - Runs the discovery program *facter* on the remote system <facter_module>
  filesystem - Makes file system on block device <filesystem_module>
  firewalld - Manage arbitrary ports/services with firewalld <firewalld_module>
  gconftool2 - Edit GNOME Configurations <gconftool2_module>
  getent - a wrapper to the unix getent utility <getent_module>
  gluster_volume - Manage GlusterFS volumes <gluster_volume_module>
  group - Add or remove groups <group_module>
  hostname - Manage hostname <hostname_module>
  iptables - Modify the systems iptables <iptables_module>
  java_cert - Uses keytool to import/remove key from java keystore(cacerts) <java_cert_module>
  kernel_blacklist - Blacklist kernel modules <kernel_blacklist_module>
  known_hosts - Add or remove a host from the ``known_hosts`` file <known_hosts_module>
  locale_gen - Creates or removes locales. <locale_gen_module>
  lvg - Configure LVM volume groups <lvg_module>
  lvol - Configure LVM logical volumes <lvol_module>
  make - Run targets in a Makefile <make_module>
  modprobe - Add or remove kernel modules <modprobe_module>
  mount - Control active and configured mount points <mount_module>
  ohai - Returns inventory data from *Ohai* <ohai_module>
  open_iscsi - Manage iscsi targets with open-iscsi <open_iscsi_module>
  openwrt_init - Manage services on OpenWrt. <openwrt_init_module>
  osx_defaults - osx_defaults allows users to read, write, and delete Mac OS X user defaults from Ansible <osx_defaults_module>
  pam_limits - Modify Linux PAM limits <pam_limits_module>
  pamd - Manage PAM Modules <pamd_module>
  parted - Configure block device partitions <parted_module>
  ping - Try to connect to host, verify a usable python and return ``pong`` on success. <ping_module>
  puppet - Runs puppet <puppet_module>
  runit - Manage runit services. <runit_module>
  seboolean - Toggles SELinux booleans. <seboolean_module>
  sefcontext - Manages SELinux file context mapping definitions <sefcontext_module>
  selinux - Change policy and state of SELinux <selinux_module>
  selinux_permissive - Change permissive domain in SELinux policy <selinux_permissive_module>
  seport - Manages SELinux network port type definitions <seport_module>
  service - Manage services. <service_module>
  setup - Gathers facts about remote hosts <setup_module>
  solaris_zone - Manage Solaris zones <solaris_zone_module>
  svc - Manage daemontools services. <svc_module>
  sysctl - Manage entries in sysctl.conf. <sysctl_module>
  systemd - Manage services. <systemd_module>
  timezone - Configure timezone setting <timezone_module>
  ufw - Manage firewall with UFW <ufw_module>
  user - Manage user accounts <user_module>



.. note::
    -  (D): This marks a module as deprecated, which means a module is kept for backwards compatibility but usage is discouraged.
       The module documentation details page may explain more about this rationale.
