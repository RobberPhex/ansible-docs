Storage Modules
```````````````

.. toctree:: :maxdepth: 1


Netapp
------

.. toctree:: :maxdepth: 1

  netapp_e_amg (E) - Create, Remove, and Update Asynchronous Mirror Groups <netapp_e_amg_module>
  netapp_e_amg_role (E) - Update the role of a storage array within an Asynchronous Mirror Group (AMG). <netapp_e_amg_role_module>
  netapp_e_amg_sync (E) - Conduct synchronization actions on asynchronous member groups. <netapp_e_amg_sync_module>
  netapp_e_auth (E) - Sets or updates the password for a storage array. <netapp_e_auth_module>
  netapp_e_facts (E) - Get facts about NetApp E-Series arrays <netapp_e_facts_module>
  netapp_e_flashcache (E) - Manage NetApp SSD caches <netapp_e_flashcache_module>
  netapp_e_host (E) - manage eseries hosts <netapp_e_host_module>
  netapp_e_hostgroup (E) - Manage NetApp Storage Array Host Groups <netapp_e_hostgroup_module>
  netapp_e_lun_mapping (E) - Create or Remove LUN Mappings <netapp_e_lun_mapping_module>
  netapp_e_snapshot_group (E) - Manage snapshot groups <netapp_e_snapshot_group_module>
  netapp_e_snapshot_images (E) - Create and delete snapshot images <netapp_e_snapshot_images_module>
  netapp_e_snapshot_volume (E) - Manage E/EF-Series snapshot volumes. <netapp_e_snapshot_volume_module>
  netapp_e_storage_system (E) - Add/remove arrays from the Web Services Proxy <netapp_e_storage_system_module>
  netapp_e_storagepool (E) - Manage disk groups and disk pools <netapp_e_storagepool_module>
  netapp_e_volume (E) - Manage storage volumes (standard and thin) <netapp_e_volume_module>
  netapp_e_volume_copy (E) - Create volume copy pairs <netapp_e_volume_copy_module>



.. note::
    -  (D): This marks a module as deprecated, which means a module is kept for backwards compatibility but usage is discouraged.  The module documentation details page may explain more about this rationale.
    -  (E): This marks a module as 'extras', which means it ships with ansible but may be a newer module and possibly (but not necessarily) less actively maintained than 'core' modules.
    - Tickets filed on modules are filed to different repos than those on the main open source project. Core module tickets should be filed at `ansible/ansible-modules-core on GitHub <http://github.com/ansible/ansible-modules-core>`_, extras tickets to `ansible/ansible-modules-extras on GitHub <http://github.com/ansible/ansible-modules-extras>`_
