.. _ec2_ami_search:


ec2_ami_search - Retrieve AWS AMI for a given operating system.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

Look up the most recent AMI on AWS for a given operating system.
Returns ``ami``, ``aki``, ``ari``, ``serial``, ``tag``
If there is no AKI or ARI associated with an image, these will be ``null``.
Only supports images from cloud-images.ubuntu.com
Example output: ``{"ami": "ami-69f5a900", "changed": false, "aki": "aki-88aa75e1", "tag": "release", "ari": null, "serial": "20131024"}``

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
    <td>arch</td>
    <td>no</td>
    <td>amd64</td>
        <td><ul><li>i386</li><li>amd64</li></ul></td>
        <td>CPU architecture</td>
    </tr>
            <tr>
    <td>distro</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>ubuntu</li></ul></td>
        <td>Linux distribution (e.g., C(ubuntu))</td>
    </tr>
            <tr>
    <td>region</td>
    <td>no</td>
    <td>us-east-1</td>
        <td><ul><li>ap-northeast-1</li><li>ap-southeast-1</li><li>ap-southeast-2</li><li>eu-central-1</li><li>eu-west-1</li><li>sa-east-1</li><li>us-east-1</li><li>us-west-1</li><li>us-west-2</li><li>us-gov-west-1</li></ul></td>
        <td>EC2 region</td>
    </tr>
            <tr>
    <td>release</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>short name of the release (e.g., C(precise))</td>
    </tr>
            <tr>
    <td>store</td>
    <td>no</td>
    <td>ebs</td>
        <td><ul><li>ebs</li><li>ebs-io1</li><li>ebs-ssd</li><li>instance-store</li></ul></td>
        <td>Back-end store for instance</td>
    </tr>
            <tr>
    <td>stream</td>
    <td>no</td>
    <td>server</td>
        <td><ul><li>server</li><li>desktop</li></ul></td>
        <td>Type of release.</td>
    </tr>
            <tr>
    <td>virt</td>
    <td>no</td>
    <td>paravirtual</td>
        <td><ul><li>paravirtual</li><li>hvm</li></ul></td>
        <td>virutalization type</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    - name: Launch an Ubuntu 12.04 (Precise Pangolin) EC2 instance
      hosts: 127.0.0.1
      connection: local
      tasks:
      - name: Get the Ubuntu precise AMI
        ec2_ami_search: distro=ubuntu release=precise region=us-west-1 store=instance-store
        register: ubuntu_image
      - name: Start the EC2 instance
        ec2: image={{ ubuntu_image.ami }} instance_type=m1.small key_name=mykey



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

