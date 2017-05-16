.. _rds:


rds - create, delete, or modify an Amazon rds instance
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.3

Creates, deletes, or modifies rds instances.  When creating an instance it can be either a new instance or a read-only replica of an existing instance. This module has a dependency on python-boto >= 2.5. The 'promote' command requires boto >= 2.18.0.

Options
-------

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">parameter</th>
    <th class="head">required</th>
    <th class="head">default</th>
    <th class="head">choices</th>
    <th class="head">comments</th>
    </tr>
            <tr>
    <td>apply_immediately</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Used only when command=modify.  If enabled, the modifications will be applied as soon as possible rather than waiting for the next preferred maintenance window.</td>
    </tr>
            <tr>
    <td>aws_access_key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>AWS access key. If not set then the value of the AWS_ACCESS_KEY environment variable is used.</td>
    </tr>
            <tr>
    <td>aws_secret_key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>AWS secret key. If not set then the value of the AWS_SECRET_KEY environment variable is used.</td>
    </tr>
            <tr>
    <td>backup_retention</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Number of days backups are retained.  Set to 0 to disable backups.  Default is 1 day.  Valid range: 0-35. Used only when command=create or command=modify.</td>
    </tr>
            <tr>
    <td>backup_window</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Backup window in format of hh24:mi-hh24:mi.  If not specified then a random backup window is assigned. Used only when command=create or command=modify.</td>
    </tr>
            <tr>
    <td>command</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>create</li><li>replicate</li><li>delete</li><li>facts</li><li>modify</li><li>promote</li><li>snapshot</li><li>restore</li></ul></td>
        <td>Specifies the action to take.</td>
    </tr>
            <tr>
    <td>db_engine</td>
    <td>no</td>
    <td></td>
        <td><ul><li>MySQL</li><li>oracle-se1</li><li>oracle-se</li><li>oracle-ee</li><li>sqlserver-ee</li><li>sqlserver-se</li><li>sqlserver-ex</li><li>sqlserver-web</li><li>postgres</li></ul></td>
        <td>The type of database.  Used only when command=create.</td>
    </tr>
            <tr>
    <td>db_name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of a database to create within the instance.  If not specified then no database is created. Used only when command=create.</td>
    </tr>
            <tr>
    <td>engine_version</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Version number of the database engine to use. Used only when command=create. If not specified then the current Amazon RDS default engine version is used.</td>
    </tr>
            <tr>
    <td>instance_name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Database instance identifier.</td>
    </tr>
            <tr>
    <td>instance_type</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The instance type of the database.  Must be specified when command=create. Optional when command=replicate, command=modify or command=restore. If not specified then the replica inherits the same instance type as the source instance.</td>
    </tr>
            <tr>
    <td>iops</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Specifies the number of IOPS for the instance.  Used only when command=create or command=modify. Must be an integer greater than 1000.</td>
    </tr>
            <tr>
    <td>license_model</td>
    <td>no</td>
    <td></td>
        <td><ul><li>license-included</li><li>bring-your-own-license</li><li>general-public-license</li></ul></td>
        <td>The license model for this DB instance. Used only when command=create or command=restore.</td>
    </tr>
            <tr>
    <td>maint_window</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Maintenance window in format of ddd:hh24:mi-ddd:hh24:mi.  (Example: Mon:22:00-Mon:23:15) If not specified then a random maintenance window is assigned. Used only when command=create or command=modify.</td>
    </tr>
            <tr>
    <td>multi_zone</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Specifies if this is a Multi-availability-zone deployment. Can not be used in conjunction with zone parameter. Used only when command=create or command=modify.</td>
    </tr>
            <tr>
    <td>new_instance_name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name to rename an instance to. Used only when command=modify. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>option_group</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The name of the option group to use.  If not specified then the default option group is used. Used only when command=create.</td>
    </tr>
            <tr>
    <td>parameter_group</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of the DB parameter group to associate with this instance.  If omitted then the RDS default DBParameterGroup will be used. Used only when command=create or command=modify.</td>
    </tr>
            <tr>
    <td>password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Password for the master database username. Used only when command=create or command=modify.</td>
    </tr>
            <tr>
    <td>port</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Port number that the DB instance uses for connections.  Defaults to 3306 for mysql. Must be changed to 1521 for Oracle, 1443 for SQL Server, 5432 for PostgreSQL. Used only when command=create or command=replicate.</td>
    </tr>
            <tr>
    <td>region</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The AWS region to use. If not specified then the value of the EC2_REGION environment variable, if any, is used.</td>
    </tr>
            <tr>
    <td>security_groups</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Comma separated list of one or more security groups.  Used only when command=create or command=modify.</td>
    </tr>
            <tr>
    <td>size</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Size in gigabytes of the initial storage for the DB instance. Used only when command=create or command=modify.</td>
    </tr>
            <tr>
    <td>snapshot</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of snapshot to take. When command=delete, if no snapshot name is provided then no snapshot is taken. Used only when command=delete or command=snapshot.</td>
    </tr>
            <tr>
    <td>source_instance</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of the database to replicate. Used only when command=replicate.</td>
    </tr>
            <tr>
    <td>subnet</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>VPC subnet group.  If specified then a VPC instance is created. Used only when command=create.</td>
    </tr>
            <tr>
    <td>upgrade</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Indicates that minor version upgrades should be applied automatically. Used only when command=create or command=replicate.</td>
    </tr>
            <tr>
    <td>username</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Master database username. Used only when command=create.</td>
    </tr>
            <tr>
    <td>vpc_security_groups</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Comma separated list of one or more vpc security group ids. Also requires `subnet` to be specified. Used only when command=create or command=modify.</td>
    </tr>
            <tr>
    <td>wait</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>When command=create, replicate, modify or restore then wait for the database to enter the 'available' state.  When command=delete wait for the database to be terminated.</td>
    </tr>
            <tr>
    <td>wait_timeout</td>
    <td>no</td>
    <td>300</td>
        <td><ul></ul></td>
        <td>how long before wait gives up, in seconds</td>
    </tr>
            <tr>
    <td>zone</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>availability zone in which to launch the instance. Used only when command=create, command=replicate or command=restore.</td>
    </tr>
        </table>


.. note:: Requires boto


Examples
--------

.. raw:: html

    <br/>


::

    # Basic mysql provisioning example
    - rds: >
          command=create
          instance_name=new_database
          db_engine=MySQL
          size=10
          instance_type=db.m1.small
          username=mysql_admin
          password=1nsecure
    
    # Create a read-only replica and wait for it to become available
    - rds: >
          command=replicate
          instance_name=new_database_replica
          source_instance=new_database
          wait=yes
          wait_timeout=600
    
    # Delete an instance, but create a snapshot before doing so
    - rds: >
          command=delete
          instance_name=new_database
          snapshot=new_database_snapshot
    
    # Get facts about an instance
    - rds: >
          command=facts
          instance_name=new_database
          register: new_database_facts
    
    # Rename an instance and wait for the change to take effect
    - rds: >
          command=modify
          instance_name=new_database
          new_instance_name=renamed_database
          wait=yes
        



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

