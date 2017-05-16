.. _ecs_cluster:


ecs_cluster - create or terminate ecs clusters
++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Creates or terminates ecs clusters.


Requirements (on host that executes module)
-------------------------------------------

  * boto
  * boto3
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
                <tr><td>delay<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Number of seconds to wait</div>        </td></tr>
                <tr><td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints). Ignored for modules where region is required. Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The cluster name</div>        </td></tr>
                <tr><td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Uses a boto profile. Only works with boto &gt;= 2.24.0.</div>        </td></tr>
                <tr><td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The AWS region to use. If not specified then the value of the AWS_REGION or EC2_REGION environment variable, if any, is used. See <a href='http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region'>http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region</a></div></br>
    <div style="font-size: small;">aliases: aws_region, ec2_region<div>        </td></tr>
                <tr><td>repeat<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The number of times to wait for the cluster to have an instance</div>        </td></tr>
                <tr><td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
    <div style="font-size: small;">aliases: access_token<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>has_instances</li></ul></td>
        <td><div>The desired state of the cluster</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Note: These examples do not set authentication details, see the AWS Guide for details.
    
    # Cluster creation
    - ecs_cluster:
        name: default
        state: present
    
    # Cluster deletion
    - ecs_cluster:
        name: default
        state: absent
    
    - name: Wait for register
      ecs_cluster:
        name: "{{ new_cluster }}"
        state: has_instances
        delay: 10
        repeat: 10
      register: task_output
    

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
        <td> status </td>
        <td> the status of the new cluster </td>
        <td align=center> ACTIVE </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> runningTasksCount </td>
        <td> how many tasks are running in this cluster </td>
        <td align=center> 0 if a new cluster </td>
        <td align=center> int </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> activeServicesCount </td>
        <td> how many services are active in this cluster </td>
        <td align=center> 0 if a new cluster </td>
        <td align=center> int </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> clusterArn </td>
        <td> the ARN of the cluster just created </td>
        <td align=center>  </td>
        <td align=center> string (ARN) </td>
        <td align=center> arn:aws:ecs:us-west-2:172139249013:cluster/test-cluster-mfshcdok </td>
    </tr>
            <tr>
        <td> clusterName </td>
        <td> name of the cluster just created (should match the input argument) </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> test-cluster-mfshcdok </td>
    </tr>
            <tr>
        <td> registeredContainerInstancesCount </td>
        <td> how many container instances are available in this cluster </td>
        <td align=center> 0 if a new cluster </td>
        <td align=center> int </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> pendingTasksCount </td>
        <td> how many tasks are waiting to run in this cluster </td>
        <td align=center> 0 if a new cluster </td>
        <td align=center> int </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - When deleting a cluster, the information returned is the state of the cluster prior to deletion.
    - It will also wait for a cluster to have instances registered to it.
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
