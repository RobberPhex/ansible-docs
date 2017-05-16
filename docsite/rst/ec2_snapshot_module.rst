.. _ec2_snapshot:


ec2_snapshot - creates a snapshot from an existing volume
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.5

creates an EC2 snapshot from an existing EBS volume

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
    <td>description</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>description to be applied to the snapshot</td>
    </tr>
            <tr>
    <td>device_name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>device name of a mounted volume to be snapshotted</td>
    </tr>
            <tr>
    <td>ec2_url</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Must be specified if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used</td>
    </tr>
            <tr>
    <td>instance_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>instance that has the required volume to snapshot mounted</td>
    </tr>
            <tr>
    <td>profile</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>uses a boto profile. Only works with boto &gt;= 2.24.0 (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>region</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The AWS region to use. If not specified then the value of the EC2_REGION environment variable, if any, is used.</td>
    </tr>
            <tr>
    <td>security_token</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>security token to authenticate against AWS (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>snapshot_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>snapshot id to remove (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>snapshot_tags</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>a hash/dictionary of tags to add to the snapshot (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td>whether to add or create a snapshot (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>volume_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>volume from which to take the snapshot</td>
    </tr>
            <tr>
    <td>wait</td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>wait for the snapshot to be ready (added in Ansible 1.5.1)</td>
    </tr>
            <tr>
    <td>wait_timeout</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>how long before wait gives up, in secondsspecify 0 to wait forever (added in Ansible 1.5.1)</td>
    </tr>
        </table>


.. note:: Requires boto


Examples
--------

.. raw:: html

    <br/>


::

    # Simple snapshot of volume using volume_id
    - ec2_snapshot:
        volume_id: vol-abcdef12   
        description: snapshot of /data from DB123 taken 2013/11/28 12:18:32
    
    # Snapshot of volume mounted on device_name attached to instance_id
    - ec2_snapshot:
        instance_id: i-12345678
        device_name: /dev/sdb1
        description: snapshot of /data from DB123 taken 2013/11/28 12:18:32
    
    # Snapshot of volume with tagging
    - ec2_snapshot:
        instance_id: i-12345678
        device_name: /dev/sdb1
        snapshot_tags:
            frequency: hourly
            source: /data
    
    # Remove a snapshot
    - local_action:
        module: ec2_snapshot
        snapshot_id: snap-abcd1234
        state: absent

.. note:: The following environment variables can be used ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY`` or ``AWS_ACCESS_KEY_ID``, ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY`` or ``AWS_SECRET_ACCESS_KEY``, ``AWS_REGION`` or ``EC2_REGION``, ``AWS_SECURITY_TOKEN``
.. note:: Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
.. note:: ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

