.. _proxmox:


proxmox - management of instances in Proxmox VE cluster
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* allows you to create/delete/stop instances in Proxmox VE cluster
* Starting in Ansible 2.1, it automatically detects containerization type (lxc for PVE 4, openvz for older)


Requirements (on host that executes module)
-------------------------------------------

  * proxmoxer
  * python >= 2.7
  * requests


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
                <tr><td>api_host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>the host of the Proxmox VE cluster</div>        </td></tr>
                <tr><td>api_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>the password to authenticate with</div><div>you can use PROXMOX_PASSWORD environment variable</div>        </td></tr>
                <tr><td>api_user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>the user to authenticate with</div>        </td></tr>
                <tr><td>cpus<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td></td>
        <td><div>numbers of allocated cpus for instance</div>        </td></tr>
                <tr><td>cpuunits<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1000</td>
        <td></td>
        <td><div>CPU weight for a VM</div>        </td></tr>
                <tr><td>disk<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>3</td>
        <td></td>
        <td><div>hard disk size in GB for instance</div>        </td></tr>
                <tr><td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>forcing operations</div><div>can be used only with states <code>present</code>, <code>stopped</code>, <code>restarted</code></div><div>with <code>state=present</code> force option allow to overwrite existing container</div><div>with states <code>stopped</code> , <code>restarted</code> allow to force stop instance</div>        </td></tr>
                <tr><td>hostname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>the instance hostname</div><div>required only for <code>state=present</code></div><div>must be unique if vmid is not passed</div>        </td></tr>
                <tr><td>ip_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>specifies the address the container will be assigned</div>        </td></tr>
                <tr><td>memory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>512</td>
        <td></td>
        <td><div>memory size in MB for instance</div>        </td></tr>
                <tr><td>mounts<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>specifies additional mounts (separate disks) for the container. As a hash/dictionary defining mount points</div>        </td></tr>
                <tr><td>nameserver<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>sets DNS server IP address for a container</div>        </td></tr>
                <tr><td>netif<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>specifies network interfaces for the container. As a hash/dictionary defining interfaces.</div>        </td></tr>
                <tr><td>node<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Proxmox VE node, when new VM will be created</div><div>required only for <code>state=present</code></div><div>for another states will be autodiscovered</div>        </td></tr>
                <tr><td>onboot<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>specifies whether a VM will be started during system bootup</div>        </td></tr>
                <tr><td>ostemplate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>the template for VM creating</div><div>required only for <code>state=present</code></div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>the instance root password</div><div>required only for <code>state=present</code></div>        </td></tr>
                <tr><td>pool<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Proxmox VE resource pool</div>        </td></tr>
                <tr><td>pubkey<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Public key to add to /root/.ssh/authorized_keys. This was added on Proxmox 4.2, it is ignored for earlier versions</div>        </td></tr>
                <tr><td>searchdomain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>sets DNS search domain for a container</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>started</li><li>absent</li><li>stopped</li><li>restarted</li></ul></td>
        <td><div>Indicate desired state of the instance</div>        </td></tr>
                <tr><td>storage<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>local</td>
        <td></td>
        <td><div>target storage</div>        </td></tr>
                <tr><td>swap<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>swap memory size in MB for instance</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>30</td>
        <td></td>
        <td><div>timeout for operations</div>        </td></tr>
                <tr><td>unprivileged<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Indicate if the container should be unprivileged</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>enable / disable https certificate verification</div>        </td></tr>
                <tr><td>vmid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>the instance id</div><div>if not set, the next available VM ID will be fetched from ProxmoxAPI.</div><div>if not set, will be fetched from PromoxAPI based on the hostname</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create new container with minimal options
    - proxmox:
        vmid: 100
        node: uk-mc02
        api_user: root@pam
        api_password: 1q2w3e
        api_host: node1
        password: 123456
        hostname: example.org
        ostemplate: 'local:vztmpl/ubuntu-14.04-x86_64.tar.gz'
    
    # Create new container automatically selecting the next available vmid.
    - proxmox: node='uk-mc02' api_user='root@pam' api_password='1q2w3e' api_host='node1' password='123456' hostname='example.org' ostemplate='local:vztmpl/ubuntu-14.04-x86_64.tar.gz'
    
    # Create new container with minimal options with force(it will rewrite existing container)
    - proxmox:
        vmid: 100
        node: uk-mc02
        api_user: root@pam
        api_password: 1q2w3e
        api_host: node1
        password: 123456
        hostname: example.org
        ostemplate: 'local:vztmpl/ubuntu-14.04-x86_64.tar.gz'
        force: yes
    
    # Create new container with minimal options use environment PROXMOX_PASSWORD variable(you should export it before)
    - proxmox:
        vmid: 100
        node: uk-mc02
        api_user: root@pam
        api_host: node1
        password: 123456
        hostname: example.org
        ostemplate: 'local:vztmpl/ubuntu-14.04-x86_64.tar.gz'
    
    # Create new container with minimal options defining network interface with dhcp
    - proxmox:
        vmid: 100
        node: uk-mc02
        api_user: root@pam
        api_password: 1q2w3e
        api_host: node1
        password: 123456
        hostname: example.org
        ostemplate: 'local:vztmpl/ubuntu-14.04-x86_64.tar.gz'
        netif: '{"net0":"name=eth0,ip=dhcp,ip6=dhcp,bridge=vmbr0"}'
    
    # Create new container with minimal options defining network interface with static ip
    - proxmox:
        vmid: 100
        node: uk-mc02
        api_user: root@pam
        api_password: 1q2w3e
        api_host: node1
        password: 123456
        hostname: example.org
        ostemplate: 'local:vztmpl/ubuntu-14.04-x86_64.tar.gz'
        netif: '{"net0":"name=eth0,gw=192.168.0.1,ip=192.168.0.2/24,bridge=vmbr0"}'
    
    # Create new container with minimal options defining a mount
    - proxmox:
        vmid: 100
        node: uk-mc02
        api_user: root@pam
        api_password: 1q2w3e
        api_host: node1
        password: 123456
        hostname: example.org
        ostemplate: local:vztmpl/ubuntu-14.04-x86_64.tar.gz'
        mounts: '{"mp0":"local:8,mp=/mnt/test/"}'
    
    # Start container
    - proxmox:
        vmid: 100
        api_user: root@pam
        api_password: 1q2w3e
        api_host: node1
        state: started
    
    # Stop container
    - proxmox:
        vmid: 100
        api_user: root@pam
        api_password: 1q2w3e
        api_host: node1
        state: stopped
    
    # Stop container with force
    - proxmox:
        vmid: 100
        api_user: root@pam
        api_password: 1q2w3e
        api_host: node1
        force: yes
        state: stopped
    
    # Restart container(stopped or mounted container you can't restart)
    - proxmox:
        vmid: 100
        api_user: root@pam
        api_password: 1q2w3e
        api_host: node1
        state: stopped
    
    # Remove container
    - proxmox:
        vmid: 100
        api_user: root@pam
        api_password: 1q2w3e
        api_host: node1
        state: absent


Notes
-----

.. note::
    - Requires proxmoxer and requests modules on host. This modules can be installed with pip.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
