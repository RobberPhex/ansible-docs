.. _azure:


azure - create or terminate a virtual machine in azure
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.7


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Creates or terminates azure instances. When created optionally waits for it to be 'running'.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * azure >= 0.7.1


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
                <tr><td>auto_updates<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Enable Auto Updates on Windows Machines</div>        </td></tr>
                <tr><td>enable_winrm<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Enable winrm on Windows Machines</div>        </td></tr>
                <tr><td>endpoints<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>22</td>
        <td></td>
        <td><div>a comma-separated list of TCP ports to expose on the virtual machine (e.g., "22,80")</div>        </td></tr>
                <tr><td>hostname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>hostname to write /etc/hostname. Defaults to &lt;name&gt;.cloudapp.net.</div>        </td></tr>
                <tr><td>image<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>system image for creating the virtual machine (e.g., b39f27a8b8c64d52b05eac6a62ebad85__Ubuntu_DAILY_BUILD-precise-12_04_3-LTS-amd64-server-20131205-en-us-30GB)</div>        </td></tr>
                <tr><td>location<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>the azure location to use (e.g. 'East US')</div>        </td></tr>
                <tr><td>management_cert_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>path to an azure management certificate associated with the subscription id. Overrides the AZURE_CERT_PATH environment variable.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>name of the virtual machine and associated cloud service.</div>        </td></tr>
                <tr><td>os_type<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>linux</td>
        <td><ul><li>windows</li><li>linux</li></ul></td>
        <td><div>The type of the os that is gettings provisioned</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>the unix password for the new virtual machine.</div>        </td></tr>
                <tr><td>role_size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Small</td>
        <td></td>
        <td><div>azure role size for the new virtual machine (e.g., Small, ExtraLarge, A6). You have to pay attention to the fact that instances of type G and DS are not available in all regions (locations). Make sure if you selected the size and type of instance available in your chosen location.</div>        </td></tr>
                <tr><td>ssh_cert_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>path to an X509 certificate containing the public ssh key to install in the virtual machine. See http://www.windowsazure.com/en-us/manage/linux/tutorials/intro-to-linux/ for more details.</div><div>if this option is specified, password-based ssh authentication will be disabled.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td></td>
        <td><div>create or terminate instances</div>        </td></tr>
                <tr><td>storage_account<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>the azure storage account in which to store the data disks.</div>        </td></tr>
                <tr><td>subscription_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>azure subscription id. Overrides the AZURE_SUBSCRIPTION_ID environment variable.</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>the unix username for the new virtual machine.</div>        </td></tr>
                <tr><td>virtual_network_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of virtual network.</div>        </td></tr>
                <tr><td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>wait for the instance to be in state 'running' before returning</div>        </td></tr>
                <tr><td>wait_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>600</td>
        <td></td>
        <td><div>how long before wait gives up, in seconds</div>        </td></tr>
                <tr><td>wait_timeout_redirects<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>300</td>
        <td></td>
        <td><div>how long before wait gives up for redirects, in seconds</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Note: None of these examples set subscription_id or management_cert_path
    # It is assumed that their matching environment variables are set.
    
    - name: Provision virtual machine example
      azure:
        name: my-virtual-machine
        role_size: Small
        image: b39f27a8b8c64d52b05eac6a62ebad85__Ubuntu_DAILY_BUILD-precise-12_04_3-LTS-amd64-server-20131205-en-us-30GB
        location: East US
        user: ubuntu
        ssh_cert_path: /path/to/azure_x509_cert.pem
        storage_account: my-storage-account
        wait: True
        state: present
      delegate_to: localhost
    
    - name: Terminate virtual machine example
      azure:
        name: my-virtual-machine
        state: absent
      delegate_to: localhost
    
    - name: Create windows machine
      azure:
        name: ben-Winows-23
        hostname: win123
        os_type: windows
        enable_winrm: True
        subscription_id: '{{ azure_sub_id }}'
        management_cert_path: '{{ azure_cert_path }}'
        role_size: Small
        image: bd507d3a70934695bc2128e3e5a255ba__RightImage-Windows-2012-x64-v13.5
        location: East Asia
        password: xxx
        storage_account: benooytes
        user: admin
        wait: True
        state: present
        virtual_network_name: '{{ vnet_name }}'
      delegate_to: localhost





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is supported mainly by the community and is curated by core committers.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
