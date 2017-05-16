.. _ec2_vol:


ec2_vol - create and attach a volume, return volume id and device map
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.1

creates an EBS volume and optionally attaches it to an instance.  If both an instance ID and a device name is given and the instance has a device at the device name, then no volume is created and no attachment is made.  This module has a dependency on python-boto.

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
    <td>device_name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>device id to override device mapping. Assumes /dev/sdf for Linux/UNIX and /dev/xvdf for Windows.</td>
    </tr>
            <tr>
    <td>ec2_url</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Must be specified if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used</td>
    </tr>
            <tr>
    <td>encrypted</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Enable encryption at rest for this volume. (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>volume id if you wish to attach an existing volume (requires instance) or remove an existing volume (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>instance</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>instance ID if you wish to attach the volume. Since 1.9 you can set to None to detach.</td>
    </tr>
            <tr>
    <td>iops</td>
    <td>no</td>
    <td>100</td>
        <td><ul></ul></td>
        <td>the provisioned IOPs you want to associate with this volume (integer). (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>volume Name tag if you wish to attach an existing volume (requires instance) (added in Ansible 1.6)</td>
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
    <td>snapshot</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>snapshot ID on which to base the volume (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li><li>list</li></ul></td>
        <td>whether to ensure the volume is present or absent, or to list existing volumes (The <code>list</code> option was added in version 1.8). (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>volume_size</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>size of volume (in GB) to create.</td>
    </tr>
            <tr>
    <td>volume_type</td>
    <td>no</td>
    <td>standard</td>
        <td><ul></ul></td>
        <td>Type of EBS volume; standard (magnetic), gp2 (SSD), io1 (Provisioned IOPS). "Standard" is the old EBS default and continues to remain the Ansible default for backwards compatibility. (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>zone</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>zone in which to create the volume, if unset uses the zone the instance is in (if set)</td>
    </tr>
        </table>


.. note:: Requires boto


Examples
--------

.. raw:: html

    <br/>


::

    # Simple attachment action
    - ec2_vol: 
        instance: XXXXXX 
        volume_size: 5 
        device_name: sdd
    
    # Example using custom iops params   
    - ec2_vol:
        instance: XXXXXX 
        volume_size: 5 
        iops: 200
        device_name: sdd
    
    # Example using snapshot id
    - ec2_vol:
        instance: XXXXXX
        snapshot: "{{ snapshot }}"
    
    # Playbook example combined with instance launch 
    - ec2:
        keypair: "{{ keypair }}"
        image: "{{ image }}"
        wait: yes 
        count: 3
        register: ec2
    - ec2_vol:
        instance: "{{ item.id }} " 
        volume_size: 5
        with_items: ec2.instances
        register: ec2_vol
    
    # Example: Launch an instance and then add a volue if not already present
    #   * Nothing will happen if the volume is already attached.
    #   * Volume must exist in the same zone.
    
    - ec2:
        keypair: "{{ keypair }}"
        image: "{{ image }}"
        zone: YYYYYY
        id: my_instance
        wait: yes
        count: 1
        register: ec2
    
    - ec2_vol:
        instance: "{{ item.id }}"
        name: my_existing_volume_Name_tag
        device_name: /dev/xvdf
        with_items: ec2.instances
        register: ec2_vol
    
    # Remove a volume
    - ec2_vol:
        id: vol-XXXXXXXX
        state: absent
    
    # Detach a volume (since 1.9)
    - ec2_vol:
        id: vol-XXXXXXXX
        instance: None
    
    # List volumes for an instance
    - ec2_vol:
        instance: i-XXXXXX
        state: list
    
    # Create new volume using SSD storage
    - ec2_vol:
        instance: XXXXXX
        volume_size: 50
        volume_type: gp2
        device_name: /dev/xvdf

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

