.. _azure:


azure - create or terminate a virtual machine in azure
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.7

Creates or terminates azure instances. When created optionally waits for it to be 'running'. This module has a dependency on python-azure >= 0.7.1

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
    <td>endpoints</td>
    <td>no</td>
    <td>22</td>
        <td><ul></ul></td>
        <td>a comma-separated list of TCP ports to expose on the virtual machine (e.g., "22,80")</td>
    </tr>
            <tr>
    <td>hostname</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>hostname to write /etc/hostname. Defaults to &lt;name&gt;.cloudapp.net.</td>
    </tr>
            <tr>
    <td>image</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>system image for creating the virtual machine (e.g., b39f27a8b8c64d52b05eac6a62ebad85__Ubuntu_DAILY_BUILD-precise-12_04_3-LTS-amd64-server-20131205-en-us-30GB)</td>
    </tr>
            <tr>
    <td>location</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>the azure location to use (e.g. 'East US')</td>
    </tr>
            <tr>
    <td>management_cert_path</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>path to an azure management certificate associated with the subscription id. Overrides the AZURE_CERT_PATH environement variable.</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>name of the virtual machine and associated cloud service.</td>
    </tr>
            <tr>
    <td>password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the unix password for the new virtual machine.</td>
    </tr>
            <tr>
    <td>role_size</td>
    <td>no</td>
    <td>Small</td>
        <td><ul></ul></td>
        <td>azure role size for the new virtual machine (e.g., Small, ExtraLarge, A6)</td>
    </tr>
            <tr>
    <td>ssh_cert_path</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>path to an X509 certificate containing the public ssh key to install in the virtual machine. See http://www.windowsazure.com/en-us/manage/linux/tutorials/intro-to-linux/ for more details.if this option is specified, password-based ssh authentication will be disabled.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul></ul></td>
        <td>create or terminate instances</td>
    </tr>
            <tr>
    <td>storage_account</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>the azure storage account in which to store the data disks.</td>
    </tr>
            <tr>
    <td>subscription_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>azure subscription id. Overrides the AZURE_SUBSCRIPTION_ID environement variable.</td>
    </tr>
            <tr>
    <td>user</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the unix username for the new virtual machine.</td>
    </tr>
            <tr>
    <td>virtual_network_name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of virtual network.</td>
    </tr>
            <tr>
    <td>wait</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>wait for the instance to be in state 'running' before returning</td>
    </tr>
            <tr>
    <td>wait_timeout</td>
    <td>no</td>
    <td>600</td>
        <td><ul></ul></td>
        <td>how long before wait gives up, in seconds</td>
    </tr>
            <tr>
    <td>wait_timeout_redirects</td>
    <td>no</td>
    <td>300</td>
        <td><ul></ul></td>
        <td>how long before wait gives up for redirects, in seconds</td>
    </tr>
        </table>


.. note:: Requires azure


Examples
--------

.. raw:: html

    <br/>


::

    # Note: None of these examples set subscription_id or management_cert_path
    # It is assumed that their matching environment variables are set.
    
    # Provision virtual machine example
    - local_action:
        module: azure
        name: my-virtual-machine
        role_size: Small
        image: b39f27a8b8c64d52b05eac6a62ebad85__Ubuntu_DAILY_BUILD-precise-12_04_3-LTS-amd64-server-20131205-en-us-30GB
        location: 'East US'
        user: ubuntu
        ssh_cert_path: /path/to/azure_x509_cert.pem
        storage_account: my-storage-account
        wait: yes
    
    # Terminate virtual machine example
    - local_action:
        module: azure
        name: my-virtual-machine
        state: absent



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

