.. _rhevm:


rhevm - RHEV/oVirt automation
+++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module only supports oVirt/RHEV version 3. A newer module :ref:`ovirt_vms <ovirt_vms>` supports oVirt/RHV version 4.
* Allows you to create/remove/update or powermanage virtual machines on a RHEV/oVirt platform.


Requirements (on host that executes module)
-------------------------------------------

  * ovirtsdk


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
                <tr><td>boot_order<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>[u'network', u'hd']</td>
        <td></td>
        <td><div>This option uses complex arguments and is a list of items that specify the bootorder.</div>        </td></tr>
                <tr><td>cd_drive<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The CD you wish to have mounted on the VM when <em>state = 'CD'</em>.</div>        </td></tr>
                <tr><td>cluster<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The rhev/ovirt cluster in which you want you VM to start.</div>        </td></tr>
                <tr><td>cpu_share<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0</td>
        <td></td>
        <td><div>This parameter is used to configure the cpu share.</div>        </td></tr>
                <tr><td>datacenter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Default</td>
        <td></td>
        <td><div>The rhev/ovirt datacenter in which you want you VM to start.</div>        </td></tr>
                <tr><td>del_prot<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>This option sets the delete protection checkbox.</div>        </td></tr>
                <tr><td>disks<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>This option uses complex arguments and is a list of disks with the options name, size and domain.</div>        </td></tr>
                <tr><td>ifaces<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>This option uses complex arguments and is a list of interfaces with the options name and vlan.</div></br>
    <div style="font-size: small;">aliases: nics, interfaces<div>        </td></tr>
                <tr><td>image<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The template to use for the VM.</div>        </td></tr>
                <tr><td>insecure_api<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A boolean switch to make a secure or insecure connection to the server.</div>        </td></tr>
                <tr><td>mempol<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td></td>
        <td><div>The minimum amount of memory you wish to reserve for this system.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The name of the VM.</div>        </td></tr>
                <tr><td>osver<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>rhel_6x64</td>
        <td></td>
        <td><div>The operationsystem option in RHEV/oVirt.</div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>443</td>
        <td></td>
        <td><div>The port on which the API is reacheable.</div>        </td></tr>
                <tr><td>server<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>127.0.0.1</td>
        <td></td>
        <td><div>The name/ip of your RHEV-m/oVirt instance.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>ping</li><li>present</li><li>absent</li><li>up</li><li>down</li><li>restarted</li><li>cd</li><li>info</li></ul></td>
        <td><div>This serves to create/remove/update or powermanage your VM.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The timeout you wish to define for power actions.</div><div>When <em>state = 'up'</em></div><div>When <em>state = 'down'</em></div><div>When <em>state = 'restarted'</em></div>        </td></tr>
                <tr><td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>server</td>
        <td><ul><li>server</li><li>desktop</li><li>host</li></ul></td>
        <td><div>To define if the VM is a server or desktop.</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>admin@internal</td>
        <td></td>
        <td><div>The user to authenticate with.</div>        </td></tr>
                <tr><td>vm_ha<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>To make your VM High Available.</div>        </td></tr>
                <tr><td>vmcpu<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>2</td>
        <td></td>
        <td><div>The number of CPUs you want in your VM.</div>        </td></tr>
                <tr><td>vmhost<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The host you wish your VM to run on.</div>        </td></tr>
                <tr><td>vmmem<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td></td>
        <td><div>The amount of memory you want your VM to use (in GB).</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # basic get info from VM
      - rhevm:
          name: "demo"
          user: "{{ rhev.admin.name }}"
          password: "{{ rhev.admin.pass }}"
          server: "rhevm01"
          state: "info"
    
    # basic create example from image
      - rhevm:
          name: "demo"
          user: "{{ rhev.admin.name }}"
          password: "{{ rhev.admin.pass }}"
          server: "rhevm01"
          state: "present"
          image: "centos7_x64"
          cluster: "centos"
    
    # power management
      - rhevm:
          name: "uptime_server"
          user: "{{ rhev.admin.name }}"
          password: "{{ rhev.admin.pass }}"
          server: "rhevm01"
          cluster: "RH"
          state: "down"
          image: "centos7_x64"
          cluster: "centos"
    
    # multi disk, multi nic create example
      - rhevm:
          name: "server007"
          user: "{{ rhev.admin.name }}"
          password: "{{ rhev.admin.pass }}"
          server: "rhevm01"
          cluster: "RH"
          state: "present"
          type: "server"
          vmcpu: 4
          vmmem: 2
          ifaces:
            - name: "eth0"
              vlan: "vlan2202"
            - name: "eth1"
              vlan: "vlan36"
            - name: "eth2"
              vlan: "vlan38"
            - name: "eth3"
              vlan: "vlan2202"
          disks:
            - name: "root"
              size: 10
              domain: "ssd-san"
            - name: "swap"
              size: 10
              domain: "15kiscsi-san"
            - name: "opt"
              size: 10
              domain: "15kiscsi-san"
            - name: "var"
              size: 10
              domain: "10kiscsi-san"
            - name: "home"
              size: 10
              domain: "sata-san"
          boot_order:
            - "network"
            - "hd"
    
    # add a CD to the disk cd_drive
      - rhevm:
          name: 'server007'
          user: "{{ rhev.admin.name }}"
          password: "{{ rhev.admin.pass }}"
          state: 'cd'
          cd_drive: 'rhev-tools-setup.iso'
    
    # new host deployment + host network configuration
      - rhevm:
          name: "ovirt_node007"
          password: "{{ rhevm.admin.pass }}"
          type: "host"
          state: present
          cluster: "rhevm01"
          ifaces:
            - name: em1
            - name: em2
            - name: p3p1
              ip: '172.31.224.200'
              netmask: '255.255.254.0'
            - name: p3p2
              ip: '172.31.225.200'
              netmask: '255.255.254.0'
            - name: bond0
              bond:
                - em1
                - em2
              network: 'rhevm'
              ip: '172.31.222.200'
              netmask: '255.255.255.0'
              management: True
            - name: bond0.36
              network: 'vlan36'
              ip: '10.2.36.200'
              netmask: '255.255.254.0'
              gateway: '10.2.36.254'
            - name: bond0.2202
              network: 'vlan2202'
            - name: bond0.38
              network: 'vlan38'

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
        <td> vm </td>
        <td> Returns all of the VMs variables and execution. </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> { "boot_order": [ "hd", "network" ], "changed": true, "changes": [ "Delete Protection" ], "cluster": "C1", "cpu_share": "0", "created": false, "datacenter": "Default", "del_prot": true, "disks": [ { "domain": "ssd-san", "name": "OS", "size": 40 } ], "eth0": "00:00:5E:00:53:00", "eth1": "00:00:5E:00:53:01", "eth2": "00:00:5E:00:53:02", "exists": true, "failed": false, "ifaces": [ { "name": "eth0", "vlan": "Management" }, { "name": "eth1", "vlan": "Internal" }, { "name": "eth2", "vlan": "External" } ], "image": false, "mempol": "0", "msg": [ "VM exists", "cpu_share was already set to 0", "VM high availability was already set to True", "The boot order has already been set", "VM delete protection has been set to True", "Disk web2_Disk0_OS already exists", "The VM starting host was already set to host416" ], "name": "web2", "type": "server", "uuid": "4ba5a1be-e60b-4368-9533-920f156c817b", "vm_ha": true, "vmcpu": "4", "vmhost": "host416", "vmmem": "16" } </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
