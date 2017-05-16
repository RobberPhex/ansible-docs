Database Modules
````````````````

.. toctree:: :maxdepth: 1


Influxdb
--------

.. toctree:: :maxdepth: 1

  influxdb_database (E) - Manage InfluxDB databases <influxdb_database_module>
  influxdb_retention_policy (E) - Manage InfluxDB retention policies <influxdb_retention_policy_module>

Misc
----

.. toctree:: :maxdepth: 1

  mongodb_parameter (E) - Change an administrative parameter on a MongoDB server. <mongodb_parameter_module>
  mongodb_user (E) - Adds or removes a user from a MongoDB database. <mongodb_user_module>
  redis (E) - Various redis commands, slave and flush <redis_module>
  riak (E) - This module handles some common Riak operations <riak_module>

Mysql
-----

.. toctree:: :maxdepth: 1

  mysql_db - Add or remove MySQL databases from a remote host. <mysql_db_module>
  mysql_replication (E) - Manage MySQL replication <mysql_replication_module>
  mysql_user - Adds or removes a user from a MySQL database. <mysql_user_module>
  mysql_variables - Manage MySQL global variables <mysql_variables_module>

Postgresql
----------

.. toctree:: :maxdepth: 1

  postgresql_db - Add or remove PostgreSQL databases from a remote host. <postgresql_db_module>
  postgresql_ext (E) - Add or remove PostgreSQL extensions from a database. <postgresql_ext_module>
  postgresql_lang (E) - Adds, removes or changes procedural languages with a PostgreSQL database. <postgresql_lang_module>
  postgresql_privs - Grant or revoke privileges on PostgreSQL database objects. <postgresql_privs_module>
  postgresql_user - Adds or removes a users (roles) from a PostgreSQL database. <postgresql_user_module>

Vertica
-------

.. toctree:: :maxdepth: 1

  vertica_configuration (E) - Updates Vertica configuration parameters. <vertica_configuration_module>
  vertica_facts (E) - Gathers Vertica database facts. <vertica_facts_module>
  vertica_role (E) - Adds or removes Vertica database roles and assigns roles to them. <vertica_role_module>
  vertica_schema (E) - Adds or removes Vertica database schema and roles. <vertica_schema_module>
  vertica_user (E) - Adds or removes Vertica database users and assigns roles. <vertica_user_module>



.. note::
    -  (D): This marks a module as deprecated, which means a module is kept for backwards compatibility but usage is discouraged.  The module documentation details page may explain more about this rationale.
    -  (E): This marks a module as 'extras', which means it ships with ansible but may be a newer module and possibly (but not necessarily) less actively maintained than 'core' modules.
    - Tickets filed on modules are filed to different repos than those on the main open source project. Core module tickets should be filed at `ansible/ansible-modules-core on GitHub <http://github.com/ansible/ansible-modules-core>`_, extras tickets to `ansible/ansible-modules-extras on GitHub <http://github.com/ansible/ansible-modules-extras>`_
