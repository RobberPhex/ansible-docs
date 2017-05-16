.. _rds:


rds - create, delete, or modify an Amazon rds instance
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Creates, deletes, or modifies rds instances.  When creating an instance it can be either a new instance or a read-only replica of an existing instance. This module has a dependency on python-boto >= 2.5. The 'promote' command requires boto >= 2.18.0. Certain features such as tags rely on boto.rds2 (boto >= 2.26.0)


Requirements (on host that executes module)
-------------------------------------------

  * boto
  * python >= 2.6


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
                <tr><td>apply_immediately<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Used only when command=modify.  If enabled, the modifications will be applied as soon as possible rather than waiting for the next preferred maintenance window.</div>        </td></tr>
                <tr><td>aws_access_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS access key. If not set then the value of the AWS_ACCESS_KEY_ID, AWS_ACCESS_KEY or EC2_ACCESS_KEY environment variable is used.</div></br>
    <div style="font-size: small;">aliases: ec2_access_key, access_key<div>        </td></tr>
                <tr><td>aws_secret_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS secret key. If not set then the value of the AWS_SECRET_ACCESS_KEY, AWS_SECRET_KEY, or EC2_SECRET_KEY environment variable is used.</div></br>
    <div style="font-size: small;">aliases: ec2_secret_key, secret_key<div>        </td></tr>
                <tr><td>backup_retention<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Number of days backups are retained.  Set to 0 to disable backups.  Default is 1 day.  Valid range: 0-35. Used only when command=create or command=modify.</div>        </td></tr>
                <tr><td>backup_window<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Backup window in format of hh24:mi-hh24:mi.  If not specified then a random backup window is assigned. Used only when command=create or command=modify.</div>        </td></tr>
                <tr><td>character_set_name<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Associate the DB instance with a specified character set. Used with command=create.</div>        </td></tr>
                <tr><td>command<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>create</li><li>replicate</li><li>delete</li><li>facts</li><li>modify</li><li>promote</li><li>snapshot</li><li>reboot</li><li>restore</li></ul></td>
        <td><div>Specifies the action to take. The 'reboot' option is available starting at version 2.0</div>        </td></tr>
                <tr><td>db_engine<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>mariadb</li><li>MySQL</li><li>oracle-se1</li><li>oracle-se</li><li>oracle-ee</li><li>sqlserver-ee</li><li>sqlserver-se</li><li>sqlserver-ex</li><li>sqlserver-web</li><li>postgres</li><li>aurora</li></ul></td>
        <td><div>The type of database.  Used only when command=create.</div><div>mariadb was added in version 2.2</div>        </td></tr>
                <tr><td>db_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of a database to create within the instance.  If not specified then no database is created. Used only when command=create.</div>        </td></tr>
                <tr><td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints). Ignored for modules where region is required. Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div>        </td></tr>
                <tr><td>engine_version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Version number of the database engine to use. Used only when command=create. If not specified then the current Amazon RDS default engine version is used.</div>        </td></tr>
                <tr><td>force_failover<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Used only when command=reboot.  If enabled, the reboot is done using a MultiAZ failover.</div>        </td></tr>
                <tr><td>instance_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Database instance identifier. Required except when using command=facts or command=delete on just a snapshot</div>        </td></tr>
                <tr><td>instance_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The instance type of the database.  Must be specified when command=create. Optional when command=replicate, command=modify or command=restore. If not specified then the replica inherits the same instance type as the source instance.</div>        </td></tr>
                <tr><td>iops<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the number of IOPS for the instance.  Used only when command=create or command=modify. Must be an integer greater than 1000.</div>        </td></tr>
                <tr><td>license_model<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>license-included</li><li>bring-your-own-license</li><li>general-public-license</li><li>postgresql-license</li></ul></td>
        <td><div>The license model for this DB instance. Used only when command=create or command=restore.</div>        </td></tr>
                <tr><td>maint_window<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Maintenance window in format of ddd:hh24:mi-ddd:hh24:mi.  (Example: Mon:22:00-Mon:23:15) If not specified then a random maintenance window is assigned. Used only when command=create or command=modify.</div>        </td></tr>
                <tr><td>multi_zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Specifies if this is a Multi-availability-zone deployment. Can not be used in conjunction with zone parameter. Used only when command=create or command=modify.</div>        </td></tr>
                <tr><td>new_instance_name<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name to rename an instance to. Used only when command=modify.</div>        </td></tr>
                <tr><td>option_group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The name of the option group to use.  If not specified then the default option group is used. Used only when command=create.</div>        </td></tr>
                <tr><td>parameter_group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the DB parameter group to associate with this instance.  If omitted then the RDS default DBParameterGroup will be used. Used only when command=create or command=modify.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password for the master database username. Used only when command=create or command=modify.</div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>3306 for mysql, 1521 for Oracle, 1433 for SQL Server, 5432 for PostgreSQL.</td>
        <td></td>
        <td><div>Port number that the DB instance uses for connections. Used only when command=create or command=replicate.</div><div>Prior to 2.0 it always defaults to null and the API would use 3306, it had to be set to other DB default values when not using MySql. Starting at 2.0 it automatically defaults to what is expected for each c(db_engine).</div>        </td></tr>
                <tr><td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Uses a boto profile. Only works with boto &gt;= 2.24.0.</div>        </td></tr>
                <tr><td>publicly_accessible<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>explicitly set whether the resource should be publicly accessible or not. Used with command=create, command=replicate. Requires boto &gt;= 2.26.0</div>        </td></tr>
                <tr><td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The AWS region to use. If not specified then the value of the AWS_REGION or EC2_REGION environment variable, if any, is used. See <a href='http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region'>http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region</a></div></br>
    <div style="font-size: small;">aliases: aws_region, ec2_region<div>        </td></tr>
                <tr><td>security_groups<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Comma separated list of one or more security groups.  Used only when command=create or command=modify.</div>        </td></tr>
                <tr><td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
    <div style="font-size: small;">aliases: access_token<div>        </td></tr>
                <tr><td>size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Size in gigabytes of the initial storage for the DB instance. Used only when command=create or command=modify.</div>        </td></tr>
                <tr><td>snapshot<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of snapshot to take. When command=delete, if no snapshot name is provided then no snapshot is taken. If used with command=delete with no instance_name, the snapshot is deleted. Used with command=facts, command=delete or command=snapshot.</div>        </td></tr>
                <tr><td>source_instance<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the database to replicate. Used only when command=replicate.</div>        </td></tr>
                <tr><td>subnet<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>VPC subnet group.  If specified then a VPC instance is created. Used only when command=create.</div>        </td></tr>
                <tr><td>tags<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>tags dict to apply to a resource. Used with command=create, command=replicate, command=restore. Requires boto &gt;= 2.26.0</div>        </td></tr>
                <tr><td>upgrade<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Indicates that minor version upgrades should be applied automatically. Used only when command=create or command=replicate.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Master database username. Used only when command=create.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div>        </td></tr>
                <tr><td>vpc_security_groups<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Comma separated list of one or more vpc security group ids. Also requires `subnet` to be specified. Used only when command=create or command=modify.</div>        </td></tr>
                <tr><td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When command=create, replicate, modify or restore then wait for the database to enter the 'available' state.  When command=delete wait for the database to be terminated.</div>        </td></tr>
                <tr><td>wait_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>300</td>
        <td></td>
        <td><div>how long before wait gives up, in seconds</div>        </td></tr>
                <tr><td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>availability zone in which to launch the instance. Used only when command=create, command=replicate or command=restore.</div></br>
    <div style="font-size: small;">aliases: aws_zone, ec2_zone<div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Basic mysql provisioning example
    - rds:
        command: create
        instance_name: new-database
        db_engine: MySQL
        size: 10
        instance_type: db.m1.small
        username: mysql_admin
        password: 1nsecure
        tags:
          Environment: testing
          Application: cms
    
    # Create a read-only replica and wait for it to become available
    - rds:
        command: replicate
        instance_name: new-database-replica
        source_instance: new_database
        wait: yes
        wait_timeout: 600
    
    # Delete an instance, but create a snapshot before doing so
    - rds:
        command: delete
        instance_name: new-database
        snapshot: new_database_snapshot
    
    # Get facts about an instance
    - rds:
        command: facts
        instance_name: new-database
      register: new_database_facts
    
    # Rename an instance and wait for the change to take effect
    - rds:
        command: modify
        instance_name: new-database
        new_instance_name: renamed-database
        wait: yes
    
    # Reboot an instance and wait for it to become available again
    - rds:
        command: reboot
        instance_name: database
        wait: yes
    
    # Restore a Postgres db instance from a snapshot, wait for it to become available again, and
    #  then modify it to add your security group. Also, display the new endpoint.
    #  Note that the "publicly_accessible" option is allowed here just as it is in the AWS CLI
    - local_action:
         module: rds
         command: restore
         snapshot: mypostgres-snapshot
         instance_name: MyNewInstanceName
         region: us-west-2
         zone: us-west-2b
         subnet: default-vpc-xx441xxx
         publicly_accessible: yes
         wait: yes
         wait_timeout: 600
         tags:
             Name: pg1_test_name_tag
      register: rds
    
    - local_action:
         module: rds
         command: modify
         instance_name: MyNewInstanceName
         region: us-west-2
         vpc_security_groups: sg-xxx945xx
    
    - debug:
        msg: "The new db endpoint is {{ rds.instance.endpoint }}"


Notes
-----

.. note::
    - If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``
    - Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
    - ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
