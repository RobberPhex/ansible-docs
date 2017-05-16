.. _gce_net:


gce_net - create/destroy GCE networks and firewall rules
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.5

This module can create and destroy Google Compue Engine networks and firewall rules https://developers.google.com/compute/docs/networking. The *name* parameter is reserved for referencing a network while the *fwname* parameter is used to reference firewall rules. IPv4 Address ranges must be specified using the CIDR http://en.wikipedia.org/wiki/Classless_Inter-Domain_Routing format. Full install/configuration instructions for the gce* modules can be found in the comments of ansible/test/gce_tests.py.

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
    <td>allowed</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the protocol:ports to allow ('tcp:80' or 'tcp:80,443' or 'tcp:80-800')</td>
    </tr>
            <tr>
    <td>fwname</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>name of the firewall rule</td>
    </tr>
            <tr>
    <td>ipv4_range</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the IPv4 address range in CIDR notation for the network</td>
    </tr>
            <tr>
    <td>name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>name of the network</td>
    </tr>
            <tr>
    <td>pem_file</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>path to the pem file associated with the service account email (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>project_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>your GCE project ID (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>service_account_email</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>service account email (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>src_range</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the source IPv4 address range in CIDR notation</td>
    </tr>
            <tr>
    <td>src_tags</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the source instance tags for creating a firewall rule</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>active</li><li>present</li><li>absent</li><li>deleted</li></ul></td>
        <td>desired state of the persistent disk</td>
    </tr>
            <tr>
    <td>target_tags</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the target instance tags for creating a firewall rule (added in Ansible 1.9)</td>
    </tr>
        </table>


.. note:: Requires libcloud


Examples
--------

.. raw:: html

    <br/>


::

    # Simple example of creating a new network
    - local_action:
        module: gce_net
        name: privatenet
        ipv4_range: '10.240.16.0/24'
    
    # Simple example of creating a new firewall rule
    - local_action:
        module: gce_net
        name: privatenet
        fwname: all-web-webproxy
        allowed: tcp:80,8080
        src_tags: ["web", "proxy"]
    



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

