Database Modules
````````````````

.. toctree:: :maxdepth: 1


Influxdb
--------

.. toctree:: :maxdepth: 1

  influxdb_database - Manage InfluxDB databases <influxdb_database_module>
  influxdb_retention_policy - Manage InfluxDB retention policies <influxdb_retention_policy_module>

Misc
----

.. toctree:: :maxdepth: 1

  elasticsearch_plugin - Manage Elasticsearch plugins <elasticsearch_plugin_module>
  kibana_plugin - Manage Kibana plugins <kibana_plugin_module>
  redis - Various redis commands, slave and flush <redis_module>
  riak - This module handles some common Riak operations <riak_module>

Mongodb
-------

.. toctree:: :maxdepth: 1

  mongodb_parameter - Change an administrative parameter on a MongoDB server. <mongodb_parameter_module>
  mongodb_user - Adds or removes a user from a MongoDB database. <mongodb_user_module>

Mssql
-----

.. toctree:: :maxdepth: 1

  mssql_db - Add or remove MSSQL databases from a remote host. <mssql_db_module>

Mysql
-----

.. toctree:: :maxdepth: 1

  mysql_db - Add or remove MySQL databases from a remote host. <mysql_db_module>
  mysql_replication - Manage MySQL replication <mysql_replication_module>
  mysql_user - Adds or removes a user from a MySQL database. <mysql_user_module>
  mysql_variables - Manage MySQL global variables <mysql_variables_module>

Postgresql
----------

.. toctree:: :maxdepth: 1

  postgresql_db - Add or remove PostgreSQL databases from a remote host. <postgresql_db_module>
  postgresql_ext - Add or remove PostgreSQL extensions from a database. <postgresql_ext_module>
  postgresql_lang - Adds, removes or changes procedural languages with a PostgreSQL database. <postgresql_lang_module>
  postgresql_privs - Grant or revoke privileges on PostgreSQL database objects. <postgresql_privs_module>
  postgresql_schema - Add or remove PostgreSQL schema from a remote host <postgresql_schema_module>
  postgresql_user - Adds or removes a users (roles) from a PostgreSQL database. <postgresql_user_module>

Proxysql
--------

.. toctree:: :maxdepth: 1

  proxysql_backend_servers - Adds or removes mysql hosts from proxysql admin interface. <proxysql_backend_servers_module>
  proxysql_global_variables - Gets or sets the proxysql global variables. <proxysql_global_variables_module>
  proxysql_manage_config - Writes the proxysql configuration settings between layers. <proxysql_manage_config_module>
  proxysql_mysql_users - Adds or removes mysql users from proxysql admin interface. <proxysql_mysql_users_module>
  proxysql_query_rules - Modifies query rules using the proxysql admin interface. <proxysql_query_rules_module>
  proxysql_replication_hostgroups - Manages replication hostgroups using the proxysql admin interface. <proxysql_replication_hostgroups_module>
  proxysql_scheduler - Adds or removes schedules from proxysql admin interface. <proxysql_scheduler_module>

Vertica
-------

.. toctree:: :maxdepth: 1

  vertica_configuration - Updates Vertica configuration parameters. <vertica_configuration_module>
  vertica_facts - Gathers Vertica database facts. <vertica_facts_module>
  vertica_role - Adds or removes Vertica database roles and assigns roles to them. <vertica_role_module>
  vertica_schema - Adds or removes Vertica database schema and roles. <vertica_schema_module>
  vertica_user - Adds or removes Vertica database users and assigns roles. <vertica_user_module>



.. note::
    -  (D): This marks a module as deprecated, which means a module is kept for backwards compatibility but usage is discouraged.
       The module documentation details page may explain more about this rationale.
