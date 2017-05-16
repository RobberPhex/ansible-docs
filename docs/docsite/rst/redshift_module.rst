.. _redshift:


redshift - create, delete, or modify an Amazon Redshift instance
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Creates, deletes, or modifies amazon Redshift cluster instances.


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
                <tr><td>allow_version_upgrade<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>flag to determinate if upgrade of version is possible</div></br>
    <div style="font-size: small;">aliases: version_upgrade<div>        </td></tr>
                <tr><td>automated_snapshot_retention_period<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>period when the snapshot take place</div></br>
    <div style="font-size: small;">aliases: retention_period<div>        </td></tr>
                <tr><td>availability_zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>availability zone in which to launch cluster</div></br>
    <div style="font-size: small;">aliases: zone, aws_zone<div>        </td></tr>
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
                <tr><td>cluster_parameter_group_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>name of the cluster parameter group</div></br>
    <div style="font-size: small;">aliases: param_group_name<div>        </td></tr>
                <tr><td>cluster_security_groups<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>in which security group the cluster belongs</div></br>
    <div style="font-size: small;">aliases: security_groups<div>        </td></tr>
                <tr><td>cluster_subnet_group_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>which subnet to place the cluster</div></br>
    <div style="font-size: small;">aliases: subnet<div>        </td></tr>
                <tr><td>cluster_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>single-node</td>
        <td><ul><li>multi-node</li><li>single-node</li></ul></td>
        <td><div>The type of cluster.</div>        </td></tr>
                <tr><td>cluster_version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>1.0</li></ul></td>
        <td><div>which version the cluster should have</div></br>
    <div style="font-size: small;">aliases: version<div>        </td></tr>
                <tr><td>command<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>create</li><li>facts</li><li>delete</li><li>modify</li></ul></td>
        <td><div>Specifies the action to take.</div>        </td></tr>
                <tr><td>db_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the database.</div>        </td></tr>
                <tr><td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints). Ignored for modules where region is required. Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div>        </td></tr>
                <tr><td>elastic_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>if the cluster has an elastic IP or not</div>        </td></tr>
                <tr><td>encrypted<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>if the cluster is encrypted or not</div>        </td></tr>
                <tr><td>identifier<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Redshift cluster identifier.</div>        </td></tr>
                <tr><td>new_cluster_identifier<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Only used when command=modify.</div></br>
    <div style="font-size: small;">aliases: new_identifier<div>        </td></tr>
                <tr><td>node_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>ds1.xlarge</li><li>ds1.8xlarge</li><li>ds2.xlarge</li><li>ds2.8xlarge</li><li>dc1.large</li><li>dc1.8xlarge</li><li>dw1.xlarge</li><li>dw1.8xlarge</li><li>dw2.large</li><li>dw2.8xlarge</li></ul></td>
        <td><div>The node type of the cluster. Must be specified when command=create.</div>        </td></tr>
                <tr><td>number_of_nodes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Number of nodes. Only used when cluster_type=multi-node.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Master database password. Used only when command=create.</div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>which port the cluster is listining</div>        </td></tr>
                <tr><td>preferred_maintenance_window<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>maintenance window</div></br>
    <div style="font-size: small;">aliases: maintance_window, maint_window<div>        </td></tr>
                <tr><td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Uses a boto profile. Only works with boto &gt;= 2.24.0.</div>        </td></tr>
                <tr><td>publicly_accessible<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>if the cluster is accessible publicly or not</div>        </td></tr>
                <tr><td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
    <div style="font-size: small;">aliases: access_token<div>        </td></tr>
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
                <tr><td>vpc_security_group_ids<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>VPC security group</div></br>
    <div style="font-size: small;">aliases: vpc_security_groups<div>        </td></tr>
                <tr><td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When command=create, modify or restore then wait for the database to enter the 'available' state. When command=delete wait for the database to be terminated.</div>        </td></tr>
                <tr><td>wait_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>300</td>
        <td></td>
        <td><div>how long before wait gives up, in seconds</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Basic cluster provisioning example
    - redshift: >
        command=create
        node_type=ds1.xlarge
        identifier=new_cluster
        username=cluster_admin
        password=1nsecure

Return Values
-------------

Common return values are documented here :doc:`common_return_values`, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> cluster </td>
        <td> dictionary containing all the cluster information </td>
        <td align=center> success </td>
        <td align=center> dictionary </td>
        <td align=center>  </td>
    </tr>
        <tr><td>contains: </td>
    <td colspan=4>
        <table border=1 cellpadding=2>
        <tr>
        <th class="head">name</th>
        <th class="head">description</th>
        <th class="head">returned</th>
        <th class="head">type</th>
        <th class="head">sample</th>
        </tr>

                <tr>
        <td> status </td>
        <td> Stutus of the cluster. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> available </td>
        </tr>
                <tr>
        <td> public_ip_address </td>
        <td> Public IP address of the main node. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 0.0.0.0 </td>
        </tr>
                <tr>
        <td> availability_zone </td>
        <td> Amazon availability zone where the cluster is located. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> us-east-1b </td>
        </tr>
                <tr>
        <td> url </td>
        <td> FQDN of the main cluster node. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> new-redshift_cluster.jfkdjfdkj.us-east-1.redshift.amazonaws.com </td>
        </tr>
                <tr>
        <td> db_name </td>
        <td> Name of the database. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> new_db_name </td>
        </tr>
                <tr>
        <td> create_time </td>
        <td> Time of the cluster creation as timestamp. </td>
        <td align=center> success </td>
        <td align=center> float </td>
        <td align=center> 1430158536.31 </td>
        </tr>
                <tr>
        <td> private_ip_address </td>
        <td> Private IP address of the main node. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 10.10.10.10 </td>
        </tr>
                <tr>
        <td> identifier </td>
        <td> Id of the cluster. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> new_redshift_cluster </td>
        </tr>
                <tr>
        <td> port </td>
        <td> Port of the cluster. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 5439 </td>
        </tr>
                <tr>
        <td> maintenance_window </td>
        <td> Time frame when maintenance/upgrade are done. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> sun:09:30-sun:10:00 </td>
        </tr>
        
        </table>
    </td></tr>

        
    </table>
    </br></br>

Notes
-----

.. note::
    - If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``
    - Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
    - ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
