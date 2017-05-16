Clustering Modules
``````````````````

.. toctree:: :maxdepth: 1

  consul (E) - Add, modify & delete services within a consul cluster. <consul_module>
  consul_acl (E) - manipulate consul acl keys and rules <consul_acl_module>
  consul_kv (E) - Manipulate entries in the key/value store of a consul cluster. <consul_kv_module>
  consul_session (E) - manipulate consul sessions <consul_session_module>
  znode (E) - Create, delete, retrieve, and update znodes using ZooKeeper. <znode_module>



.. note::
    -  (D): This marks a module as deprecated, which means a module is kept for backwards compatibility but usage is discouraged.  The module documentation details page may explain more about this rationale.
    -  (E): This marks a module as 'extras', which means it ships with ansible but may be a newer module and possibly (but not necessarily) less actively maintained than 'core' modules.
    - Tickets filed on modules are filed to different repos than those on the main open source project. Core module tickets should be filed at `ansible/ansible-modules-core on GitHub <http://github.com/ansible/ansible-modules-core>`_, extras tickets to `ansible/ansible-modules-extras on GitHub <http://github.com/ansible/ansible-modules-extras>`_
