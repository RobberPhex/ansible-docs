.. _ecs_cluster:


ecs_cluster - create or terminate ecs clusters
++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Creates or terminates ecs clusters.


Requirements
------------

  * json
  * time
  * boto
  * boto3


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
    <td>delay<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Number of seconds to wait</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The cluster name</div></td></tr>
            <tr>
    <td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The AWS region to use. If not specified then the value of the AWS_REGION or EC2_REGION environment variable, if any, is used. See <a href='http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region'>http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region</a></div></br>
        <div style="font-size: small;">aliases: aws_region, ec2_region<div></td></tr>
            <tr>
    <td>repeat<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The number of times to wait for the cluster to have an instance</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>has_instances</li></ul></td>
        <td><div>The desired state of the cluster</div></td></tr>
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

.. note:: When deleting a cluster, the information returned is the state of the cluster prior to deletion.
.. note:: It will also wait for a cluster to have instances registered to it.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

