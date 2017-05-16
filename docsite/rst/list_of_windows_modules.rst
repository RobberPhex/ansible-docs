Windows Modules
```````````````

.. toctree:: :maxdepth: 1

  win_chocolatey (E) - Installs packages using chocolatey <win_chocolatey_module>
  win_copy - Copies files to remote locations on windows hosts. <win_copy_module>
  win_feature - Installs and uninstalls Windows Features <win_feature_module>
  win_file - Creates, touches or removes files or directories. <win_file_module>
  win_get_url - Fetches a file from a given URL <win_get_url_module>
  win_group - Add and remove local groups <win_group_module>
  win_msi - Installs and uninstalls Windows MSI files <win_msi_module>
  win_ping - A windows version of the classic ping module. <win_ping_module>
  win_service - Manages Windows services <win_service_module>
  win_stat - returns information about a Windows file <win_stat_module>
  win_template - Templates a file out to a remote server. <win_template_module>
  win_updates (E) - Download and install Windows updates <win_updates_module>
  win_user - Manages local Windows user accounts <win_user_module>



.. note::
    -  (D): This marks a module as deprecated, which means a module is kept for backwards compatibility but usage is discouraged.  The module documentation details page may explain more about this rationale.
    -  (E): This marks a module as 'extras', which means it ships with ansible but may be a newer module and possibly (but not necessarily) less actively maintained than 'core' modules.
    - Tickets filed on modules are filed to different repos than those on the main open source project. Core module tickets should be filed at `ansible/ansible-modules-core on GitHub <http://github.com/ansible/ansible-modules-core>`_, extras tickets to `ansible/ansible-modules-extras on GitHub <http://github.com/ansible/ansible-modules-extras>`_
