Windows Modules
```````````````

.. toctree:: :maxdepth: 1

  win_acl (E) - Set file/directory permissions for a system user or group. <win_acl_module>
  win_chocolatey (E) - Installs packages using chocolatey <win_chocolatey_module>
  win_copy - Copies files to remote locations on windows hosts. <win_copy_module>
  win_dotnet_ngen (E) - Runs ngen to recompile DLLs after .NET  updates <win_dotnet_ngen_module>
  win_environment (E) - Modifies environment variables on windows hosts. <win_environment_module>
  win_feature - Installs and uninstalls Windows Features <win_feature_module>
  win_file - Creates, touches or removes files or directories. <win_file_module>
  win_firewall_rule (E) - Windows firewall automation <win_firewall_rule_module>
  win_get_url - Fetches a file from a given URL <win_get_url_module>
  win_group - Add and remove local groups <win_group_module>
  win_iis_virtualdirectory (E) - Configures a virtual directory in IIS. <win_iis_virtualdirectory_module>
  win_iis_webapplication (E) - Configures a IIS Web application. <win_iis_webapplication_module>
  win_iis_webapppool (E) - Configures a IIS Web Application Pool. <win_iis_webapppool_module>
  win_iis_webbinding (E) - Configures a IIS Web site. <win_iis_webbinding_module>
  win_iis_website (E) - Configures a IIS Web site. <win_iis_website_module>
  win_lineinfile - Ensure a particular line is in a file, or replace an existing line using a back-referenced regular expression. <win_lineinfile_module>
  win_msi - Installs and uninstalls Windows MSI files <win_msi_module>
  win_nssm (E) - NSSM - the Non-Sucking Service Manager <win_nssm_module>
  win_package (E) - Installs/Uninstalls a installable package, either from local file system or url <win_package_module>
  win_ping - A windows version of the classic ping module. <win_ping_module>
  win_regedit (E) - Add, Edit, or Remove Registry Keys and Values <win_regedit_module>
  win_scheduled_task (E) - Manage scheduled tasks <win_scheduled_task_module>
  win_service - Manages Windows services <win_service_module>
  win_stat - returns information about a Windows file <win_stat_module>
  win_template - Templates a file out to a remote server. <win_template_module>
  win_unzip (E) - Unzips compressed files and archives on the Windows node <win_unzip_module>
  win_updates (E) - Download and install Windows updates <win_updates_module>
  win_user - Manages local Windows user accounts <win_user_module>
  win_webpicmd (E) - Installs packages using Web Platform Installer command-line <win_webpicmd_module>



.. note::
    -  (D): This marks a module as deprecated, which means a module is kept for backwards compatibility but usage is discouraged.  The module documentation details page may explain more about this rationale.
    -  (E): This marks a module as 'extras', which means it ships with ansible but may be a newer module and possibly (but not necessarily) less actively maintained than 'core' modules.
    - Tickets filed on modules are filed to different repos than those on the main open source project. Core module tickets should be filed at `ansible/ansible-modules-core on GitHub <http://github.com/ansible/ansible-modules-core>`_, extras tickets to `ansible/ansible-modules-extras on GitHub <http://github.com/ansible/ansible-modules-extras>`_
