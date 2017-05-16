.. _linode:


linode - create / delete / stop / restart an instance in Linode Public Cloud
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* creates / deletes a Linode Public Cloud instance and optionally waits for it to be 'running'.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * linode-python
  * pycurl


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
                <tr><td>additional_disks<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of dictionaries for creating additional disks that are added to the Linode configuration settings. Dictionary takes Size, Label, Type. Size is in MB.
    </div>        </td></tr>
                <tr><td>alert_bwin_enabled<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Set status of bandwidth in alerts.</div>        </td></tr>
                <tr><td>alert_bwin_threshold<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Set threshold in MB of bandwidth in alerts.</div>        </td></tr>
                <tr><td>alert_bwout_enabled<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Set status of bandwidth out alerts.</div>        </td></tr>
                <tr><td>alert_bwout_threshold<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Set threshold in MB of bandwidth out alerts.</div>        </td></tr>
                <tr><td>alert_bwquota_enabled<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Set status of bandwidth quota alerts as percentage of network tranfer quota.</div>        </td></tr>
                <tr><td>alert_bwquota_threshold<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Set threshold in MB of bandwidth quota alerts.</div>        </td></tr>
                <tr><td>alert_cpu_enabled<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Set status of receiving CPU usage alerts.</div>        </td></tr>
                <tr><td>alert_cpu_threshold<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Set percentage threshold for receiving CPU usage alerts. Each CPU core adds 100% to total.</div>        </td></tr>
                <tr><td>alert_diskio_enabled<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Set status of receiving disk IO alerts.</div>        </td></tr>
                <tr><td>alert_diskio_threshold<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Set threshold for average IO ops/sec over 2 hour period.</div>        </td></tr>
                <tr><td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Linode API key</div>        </td></tr>
                <tr><td>backupweeklyday<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Integer value for what day of the week to store weekly backups.</div>        </td></tr>
                <tr><td>datacenter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>datacenter to create an instance in (Linode Datacenter)</div>        </td></tr>
                <tr><td>displaygroup<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Add the instance to a Display Group in Linode Manager</div>        </td></tr>
                <tr><td>distribution<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>distribution to use for the instance (Linode Distribution)</div>        </td></tr>
                <tr><td>linode_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Unique ID of a linode server</div></br>
    <div style="font-size: small;">aliases: lid<div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name to give the instance (alphanumeric, dashes, underscore)</div><div>To keep sanity on the Linode Web Console, name is prepended with LinodeID_</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>root password to apply to a new server (auto generated if missing)</div>        </td></tr>
                <tr><td>payment_term<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul><li>1</li><li>12</li><li>24</li></ul></td>
        <td><div>payment term to use for the instance (payment term in months)</div>        </td></tr>
                <tr><td>plan<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>plan to use for the instance (Linode plan)</div>        </td></tr>
                <tr><td>private_ip<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Add private IPv4 address when Linode is created.</div>        </td></tr>
                <tr><td>ssh_pub_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>SSH public key applied to root user</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>active</li><li>started</li><li>absent</li><li>deleted</li><li>stopped</li><li>restarted</li></ul></td>
        <td><div>Indicate desired state of the resource</div>        </td></tr>
                <tr><td>swap<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>512</td>
        <td></td>
        <td><div>swap size in MB</div>        </td></tr>
                <tr><td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>wait for the instance to be in state 'running' before returning</div>        </td></tr>
                <tr><td>wait_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>300</td>
        <td></td>
        <td><div>how long before wait gives up, in seconds</div>        </td></tr>
                <tr><td>watchdog<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Set status of Lassie watchdog.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a server with a private IP Address
    - local_action:
         module: linode
         api_key: 'longStringFromLinodeApi'
         name: linode-test1
         plan: 1
         datacenter: 2
         distribution: 99
         password: 'superSecureRootPassword'
         private_ip: yes
         ssh_pub_key: 'ssh-rsa qwerty'
         swap: 768
         wait: yes
         wait_timeout: 600
         state: present
    
    # Fully configure new server
    - local_action:
         module: linode
         api_key: 'longStringFromLinodeApi'
         name: linode-test1
         plan: 4
         datacenter: 2
         distribution: 99
         password: 'superSecureRootPassword'
         private_ip: yes
         ssh_pub_key: 'ssh-rsa qwerty'
         swap: 768
         wait: yes
         wait_timeout: 600
         state: present
         alert_bwquota_enabled: True
         alert_bwquota_threshold: 80
         alert_bwin_enabled: True
         alert_bwin_threshold: 10
         alert_cpu_enabled: True
         alert_cpu_threshold: 210
         alert_diskio_enabled: True
         alert_bwout_enabled: True
         alert_bwout_threshold: 10
         alert_diskio_enabled: True
         alert_diskio_threshold: 10000
         backupweeklyday: 1
         backupwindow: 2
         displaygroup: 'test'
         additional_disks:
          - {Label: 'disk1', Size: 2500, Type: 'raw'}
          - {Label: 'newdisk', Size: 2000}
         watchdog: True
    
    # Ensure a running server (create if missing)
    - local_action:
         module: linode
         api_key: 'longStringFromLinodeApi'
         name: linode-test1
         linode_id: 12345678
         plan: 1
         datacenter: 2
         distribution: 99
         password: 'superSecureRootPassword'
         ssh_pub_key: 'ssh-rsa qwerty'
         swap: 768
         wait: yes
         wait_timeout: 600
         state: present
    
    # Delete a server
    - local_action:
         module: linode
         api_key: 'longStringFromLinodeApi'
         name: linode-test1
         linode_id: 12345678
         state: absent
    
    # Stop a server
    - local_action:
         module: linode
         api_key: 'longStringFromLinodeApi'
         name: linode-test1
         linode_id: 12345678
         state: stopped
    
    # Reboot a server
    - local_action:
         module: linode
         api_key: 'longStringFromLinodeApi'
         name: linode-test1
         linode_id: 12345678
         state: restarted


Notes
-----

.. note::
    - LINODE_API_KEY env variable can be used instead



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
