System Modules
``````````````

.. toctree:: :maxdepth: 1

  alternatives (E) - Manages alternative programs for common commands <alternatives_module>
  at (E) - Schedule the execution of a command or script file via the at command. <at_module>
  authorized_key - Adds or removes an SSH authorized key <authorized_key_module>
  capabilities (E) - Manage Linux capabilities <capabilities_module>
  cron - Manage cron.d and crontab entries. <cron_module>
  cronvar (E) - Manage variables in crontabs <cronvar_module>
  crypttab (E) - Encrypted Linux block devices <crypttab_module>
  debconf (E) - Configure a .deb package <debconf_module>
  facter (E) - Runs the discovery program *facter* on the remote system <facter_module>
  filesystem (E) - Makes file system on block device <filesystem_module>
  firewalld (E) - Manage arbitrary ports/services with firewalld <firewalld_module>
  getent (E) - a wrapper to the unix getent utility <getent_module>
  gluster_volume (E) - Manage GlusterFS volumes <gluster_volume_module>
  group - Add or remove groups <group_module>
  hostname - Manage hostname <hostname_module>
  iptables (E) - Modify the systems iptables <iptables_module>
  kernel_blacklist (E) - Blacklist kernel modules <kernel_blacklist_module>
  known_hosts (E) - Add or remove a host from the ``known_hosts`` file <known_hosts_module>
  locale_gen (E) - Creates or removes locales. <locale_gen_module>
  lvg (E) - Configure LVM volume groups <lvg_module>
  lvol (E) - Configure LVM logical volumes <lvol_module>
  make (E) - Run targets in a Makefile <make_module>
  modprobe (E) - Add or remove kernel modules <modprobe_module>
  mount - Control active and configured mount points <mount_module>
  ohai (E) - Returns inventory data from *Ohai* <ohai_module>
  open_iscsi (E) - Manage iscsi targets with open-iscsi <open_iscsi_module>
  osx_defaults (E) - osx_defaults allows users to read, write, and delete Mac OS X user defaults from Ansible <osx_defaults_module>
  pam_limits (E) - Modify Linux PAM limits <pam_limits_module>
  ping - Try to connect to host, verify a usable python and return ``pong`` on success. <ping_module>
  puppet (E) - Runs puppet <puppet_module>
  seboolean - Toggles SELinux booleans. <seboolean_module>
  selinux - Change policy and state of SELinux <selinux_module>
  selinux_permissive (E) - Change permissive domain in SELinux policy <selinux_permissive_module>
  seport (E) - Manages SELinux network port type definitions <seport_module>
  service - Manage services. <service_module>
  setup - Gathers facts about remote hosts <setup_module>
  solaris_zone (E) - Manage Solaris zones <solaris_zone_module>
  svc (E) - Manage daemontools services. <svc_module>
  sysctl - Manage entries in sysctl.conf. <sysctl_module>
  ufw (E) - Manage firewall with UFW <ufw_module>
  user - Manage user accounts <user_module>
  zfs (E) - Manage zfs <zfs_module>



.. note::
    -  (D): This marks a module as deprecated, which means a module is kept for backwards compatibility but usage is discouraged.  The module documentation details page may explain more about this rationale.
    -  (E): This marks a module as 'extras', which means it ships with ansible but may be a newer module and possibly (but not necessarily) less actively maintained than 'core' modules.
    - Tickets filed on modules are filed to different repos than those on the main open source project. Core module tickets should be filed at `ansible/ansible-modules-core on GitHub <http://github.com/ansible/ansible-modules-core>`_, extras tickets to `ansible/ansible-modules-extras on GitHub <http://github.com/ansible/ansible-modules-extras>`_
