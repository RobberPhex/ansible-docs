.. _ec2_ami_search:


ec2_ami_search - Retrieve AWS AMI information for a given operating system.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 1

DEPRECATED
----------

in favor of the ec2_ami_find module

Synopsis
--------

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
    <td>arch<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>amd64</td>
        <td><ul><li>i386</li><li>amd64</li></ul></td>
        <td><div>C</div><div>P</div><div>U</div><div> </div><div>a</div><div>r</div><div>c</div><div>h</div><div>i</div><div>t</div><div>e</div><div>c</div><div>t</div><div>u</div><div>r</div><div>e</div></td></tr>
            <tr>
    <td>distro<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>ubuntu</li></ul></td>
        <td><div>L</div><div>i</div><div>n</div><div>u</div><div>x</div><div> </div><div>d</div><div>i</div><div>s</div><div>t</div><div>r</div><div>i</div><div>b</div><div>u</div><div>t</div><div>i</div><div>o</div><div>n</div><div> </div><div>(</div><div>e</div><div>.</div><div>g</div><div>.</div><div>,</div><div> </div><div>C</div><div>(</div><div>u</div><div>b</div><div>u</div><div>n</div><div>t</div><div>u</div><div>)</div><div>)</div></td></tr>
            <tr>
    <td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>us-east-1</td>
        <td><ul><li>ap-northeast-1</li><li>ap-southeast-1</li><li>ap-southeast-2</li><li>eu-central-1</li><li>eu-west-1</li><li>sa-east-1</li><li>us-east-1</li><li>us-west-1</li><li>us-west-2</li><li>us-gov-west-1</li></ul></td>
        <td><div>E</div><div>C</div><div>2</div><div> </div><div>r</div><div>e</div><div>g</div><div>i</div><div>o</div><div>n</div></td></tr>
            <tr>
    <td>release<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>s</div><div>h</div><div>o</div><div>r</div><div>t</div><div> </div><div>n</div><div>a</div><div>m</div><div>e</div><div> </div><div>o</div><div>f</div><div> </div><div>t</div><div>h</div><div>e</div><div> </div><div>r</div><div>e</div><div>l</div><div>e</div><div>a</div><div>s</div><div>e</div><div> </div><div>(</div><div>e</div><div>.</div><div>g</div><div>.</div><div>,</div><div> </div><div>C</div><div>(</div><div>p</div><div>r</div><div>e</div><div>c</div><div>i</div><div>s</div><div>e</div><div>)</div><div>)</div></td></tr>
            <tr>
    <td>store<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ebs</td>
        <td><ul><li>ebs</li><li>ebs-io1</li><li>ebs-ssd</li><li>instance-store</li></ul></td>
        <td><div>B</div><div>a</div><div>c</div><div>k</div><div>-</div><div>e</div><div>n</div><div>d</div><div> </div><div>s</div><div>t</div><div>o</div><div>r</div><div>e</div><div> </div><div>f</div><div>o</div><div>r</div><div> </div><div>i</div><div>n</div><div>s</div><div>t</div><div>a</div><div>n</div><div>c</div><div>e</div></td></tr>
            <tr>
    <td>stream<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>server</td>
        <td><ul><li>server</li><li>desktop</li></ul></td>
        <td><div>T</div><div>y</div><div>p</div><div>e</div><div> </div><div>o</div><div>f</div><div> </div><div>r</div><div>e</div><div>l</div><div>e</div><div>a</div><div>s</div><div>e</div><div>.</div></td></tr>
            <tr>
    <td>virt<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>paravirtual</td>
        <td><ul><li>paravirtual</li><li>hvm</li></ul></td>
        <td><div>v</div><div>i</div><div>r</div><div>u</div><div>t</div><div>a</div><div>l</div><div>i</div><div>z</div><div>a</div><div>t</div><div>i</div><div>o</div><div>n</div><div> </div><div>t</div><div>y</div><div>p</div><div>e</div></td></tr>
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
        ec2_ami_search: distro=ubuntu release=precise region=us-west-1 store=instance-store
        register: ubuntu_image
      - name: Start the EC2 instance
        ec2: image={{ ubuntu_image.ami }} instance_type=m1.small key_name=mykey





For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

