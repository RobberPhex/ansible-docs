.. _ec2_ami_search:


ec2_ami_search - Retrieve AWS AMI information for a given operating system.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 2

DEPRECATED
----------

Use :ref:`ec2_ami_find <ec2_ami_find>` instead.

Synopsis
--------

* Look up the most recent AMI on AWS for a given operating system.
* Returns ``ami``, ``aki``, ``ari``, ``serial``, ``tag``
* If there is no AKI or ARI associated with an image, these will be ``null``.
* Only supports images from cloud-images.ubuntu.com
* Example output: ``{"ami": "ami-69f5a900", "changed": false, "aki": "aki-88aa75e1", "tag": "release", "ari": null, "serial": "20131024"}``




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
                <tr><td>arch<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>amd64</td>
        <td><ul><li>i386</li><li>amd64</li></ul></td>
        <td><div>CPU architecture</div>        </td></tr>
                <tr><td>distro<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>ubuntu</li></ul></td>
        <td><div>Linux distribution (e.g., <code>ubuntu</code>)</div>        </td></tr>
                <tr><td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>us-east-1</td>
        <td><ul><li>ap-northeast-1</li><li>ap-southeast-1</li><li>ap-northeast-2</li><li>ap-southeast-2</li><li>ca-central-1</li><li>eu-central-1</li><li>eu-west-1</li><li>eu-west-2</li><li>sa-east-1</li><li>us-east-1</li><li>us-east-2</li><li>us-west-1</li><li>us-west-2</li><li>us-gov-west-1</li></ul></td>
        <td><div>EC2 region</div>        </td></tr>
                <tr><td>release<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>short name of the release (e.g., <code>precise</code>)</div>        </td></tr>
                <tr><td>store<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ebs</td>
        <td><ul><li>ebs</li><li>ebs-io1</li><li>ebs-ssd</li><li>instance-store</li></ul></td>
        <td><div>Back-end store for instance</div>        </td></tr>
                <tr><td>stream<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>server</td>
        <td><ul><li>server</li><li>desktop</li></ul></td>
        <td><div>Type of release.</div>        </td></tr>
                <tr><td>virt<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>paravirtual</td>
        <td><ul><li>paravirtual</li><li>hvm</li></ul></td>
        <td><div>virutalization type</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Launch an Ubuntu 12.04 (Precise Pangolin) EC2 instance
      hosts: 127.0.0.1
      connection: local
      tasks:
      - name: Get the Ubuntu precise AMI
        ec2_ami_search:
          distro: ubuntu
          release: precise
          region: us-west-1
          store: instance-store
        register: ubuntu_image
    
      - name: Start the EC2 instance
        ec2:
          image: "{{ ubuntu_image.ami }}"
          instance_type: m1.small
          key_name: mykey




For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
