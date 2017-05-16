.. _proxmox:


proxmox - management of instances in Proxmox VE cluster
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

allows you to create/delete/stop instances in Proxmox VE cluster


Requirements
------------

  * proxmoxer
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
            <tr>
    <td>api_host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the host of the Proxmox VE cluster</div></td></tr>
            <tr>
    <td>api_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the password to authenticate with</div><div>you can use PROXMOX_PASSWORD environment variable</div></td></tr>
            <tr>
    <td>api_user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the user to authenticate with</div></td></tr>
            <tr>
    <td>cpus<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>numbers of allocated cpus for instance</div></td></tr>
            <tr>
    <td>cpuunits<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1000</td>
        <td><ul></ul></td>
        <td><div>CPU weight for a VM</div></td></tr>
            <tr>
    <td>disk<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>3</td>
        <td><ul></ul></td>
        <td><div>hard disk size in GB for instance</div></td></tr>
            <tr>
    <td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>forcing operations</div><div>can be used only with states <code>present</code>, <code>stopped</code>, <code>restarted</code></div><div>with <code>state=present</code> force option allow to overwrite existing container</div><div>with states <code>stopped</code> , <code>restarted</code> allow to force stop instance</div></td></tr>
            <tr>
    <td>hostname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the instance hostname</div><div>required only for <code>state=present</code></div></td></tr>
            <tr>
    <td>ip_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>specifies the address the container will be assigned</div></td></tr>
            <tr>
    <td>memory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>512</td>
        <td><ul></ul></td>
        <td><div>memory size in MB for instance</div></td></tr>
            <tr>
    <td>nameserver<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>sets DNS server IP address for a container</div></td></tr>
            <tr>
    <td>netif<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>specifies network interfaces for the container</div></td></tr>
            <tr>
    <td>node<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Proxmox VE node, when new VM will be created</div><div>required only for <code>state=present</code></div><div>for another states will be autodiscovered</div></td></tr>
            <tr>
    <td>onboot<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>specifies whether a VM will be started during system bootup</div></td></tr>
            <tr>
    <td>ostemplate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the template for VM creating</div><div>required only for <code>state=present</code></div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the instance root password</div><div>required only for <code>state=present</code></div></td></tr>
            <tr>
    <td>searchdomain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>sets DNS search domain for a container</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>started</li><li>absent</li><li>stopped</li><li>restarted</li></ul></td>
        <td><div>Indicate desired state of the instance</div></td></tr>
            <tr>
    <td>storage<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>local</td>
        <td><ul></ul></td>
        <td><div>target storage</div></td></tr>
            <tr>
    <td>swap<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>swap memory size in MB for instance</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>30</td>
        <td><ul></ul></td>
        <td><div>timeout for operations</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>enable / disable https certificate verification</div></td></tr>
            <tr>
    <td>vmid<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the instance id</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create new container with minimal options
    - proxmox: vmid=100 node='uk-mc02' api_user='root@pam' api_password='1q2w3e' api_host='node1' password='123456' hostname='example.org' ostemplate='local:vztmpl/ubuntu-14.04-x86_64.tar.gz'
    
    # Create new container with minimal options with force(it will rewrite existing container)
    - proxmox: vmid=100 node='uk-mc02' api_user='root@pam' api_password='1q2w3e' api_host='node1' password='123456' hostname='example.org' ostemplate='local:vztmpl/ubuntu-14.04-x86_64.tar.gz' force=yes
    
    # Create new container with minimal options use environment PROXMOX_PASSWORD variable(you should export it before)
    - proxmox: vmid=100 node='uk-mc02' api_user='root@pam' api_host='node1' password='123456' hostname='example.org' ostemplate='local:vztmpl/ubuntu-14.04-x86_64.tar.gz'
    
    # Start container
    - proxmox: vmid=100 api_user='root@pam' api_password='1q2w3e' api_host='node1' state=started
    
    # Stop container
    - proxmox: vmid=100 api_user='root@pam' api_password='1q2w3e' api_host='node1' state=stopped
    
    # Stop container with force
    - proxmox: vmid=100 api_user='root@pam' api_password='1q2w3e' api_host='node1' force=yes state=stopped
    
    # Restart container(stopped or mounted container you can't restart)
    - proxmox: vmid=100 api_user='root@pam' api_password='1q2w3e' api_host='node1' state=stopped
    
    # Remove container
    - proxmox: vmid=100 api_user='root@pam' api_password='1q2w3e' api_host='node1' state=absent


Notes
-----

.. note:: Requires proxmoxer and requests modules on host. This modules can be installed with pip.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

