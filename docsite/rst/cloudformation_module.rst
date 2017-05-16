.. _cloudformation:


cloudformation - create a AWS CloudFormation stack
++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.1

Launches an AWS CloudFormation stack and waits for it complete.

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
        <td>AWS access key. If not set then the value of the AWS_ACCESS_KEY environment variable is used. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>aws_secret_key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>AWS secret key. If not set then the value of the AWS_SECRET_KEY environment variable is used. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>disable_rollback</td>
    <td>no</td>
    <td>false</td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td>If a stacks fails to form, rollback will remove the stack</td>
    </tr>
            <tr>
    <td>region</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The AWS region to use. If not specified then the value of the EC2_REGION environment variable, if any, is used. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>stack_name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>name of the cloudformation stack</td>
    </tr>
            <tr>
    <td>stack_policy</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the path of the cloudformation stack policy (added in Ansible x.x)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>If state is "present", stack will be created.  If state is "present" and if stack exists and template has changed, it will be updated. If state is "absent", stack will be removed.</td>
    </tr>
            <tr>
    <td>tags</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Dictionary of tags to associate with stack and it's resources during stack creation. Cannot be updated later. Requires at least Boto version 2.6.0. (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>template</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>the path of the cloudformation template</td>
    </tr>
            <tr>
    <td>template_parameters</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>a list of hashes of all the template variables for the stack</td>
    </tr>
        </table>


.. note:: Requires boto


Examples
--------

.. raw:: html

    <br/>


::

    # Basic task example
    tasks:
    - name: launch ansible cloudformation example
      cloudformation:
        stack_name: "ansible-cloudformation" 
        state: "present"
        region: "us-east-1" 
        disable_rollback: true
        template: "files/cloudformation-example.json"
        template_parameters:
          KeyName: "jmartin"
          DiskType: "ephemeral"
          InstanceType: "m1.small"
          ClusterSize: 3
        tags:
          Stack: "ansible-cloudformation"



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

