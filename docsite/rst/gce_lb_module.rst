.. _gce_lb:


gce_lb - create/destroy GCE load-balancer resources
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.5

This module can create and destroy Google Compute Engine ``loadbalancer`` and ``httphealthcheck`` resources.  The primary LB resource is the ``load_balancer`` resource and the health check parameters are all prefixed with *httphealthcheck*. The full documentation for Google Compute Engine load balancing is at https://developers.google.com/compute/docs/load-balancing/.  However, the ansible module simplifies the configuration by following the libcloud model. Full install/configuration instructions for the gce* modules can be found in the comments of ansible/test/gce_tests.py.

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
    <td>external_ip</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the external static IPv4 (or auto-assigned) address for the LB</td>
    </tr>
            <tr>
    <td>httphealthcheck_healthy_count</td>
    <td>no</td>
    <td>2</td>
        <td><ul></ul></td>
        <td>number of consecutive successful checks before marking a node healthy</td>
    </tr>
            <tr>
    <td>httphealthcheck_host</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>host header to pass through on HTTP check requests</td>
    </tr>
            <tr>
    <td>httphealthcheck_interval</td>
    <td>no</td>
    <td>5</td>
        <td><ul></ul></td>
        <td>the duration in seconds between each health check request</td>
    </tr>
            <tr>
    <td>httphealthcheck_name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the name identifier for the HTTP health check</td>
    </tr>
            <tr>
    <td>httphealthcheck_path</td>
    <td>no</td>
    <td>/</td>
        <td><ul></ul></td>
        <td>the url path to use for HTTP health checking</td>
    </tr>
            <tr>
    <td>httphealthcheck_port</td>
    <td>no</td>
    <td>80</td>
        <td><ul></ul></td>
        <td>the TCP port to use for HTTP health checking</td>
    </tr>
            <tr>
    <td>httphealthcheck_timeout</td>
    <td>no</td>
    <td>5</td>
        <td><ul></ul></td>
        <td>the timeout in seconds before a request is considered a failed check</td>
    </tr>
            <tr>
    <td>httphealthcheck_unhealthy_count</td>
    <td>no</td>
    <td>2</td>
        <td><ul></ul></td>
        <td>number of consecutive failed checks before marking a node unhealthy</td>
    </tr>
            <tr>
    <td>members</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>a list of zone/nodename pairs, e.g ['us-central1-a/www-a', ...]</td>
    </tr>
            <tr>
    <td>name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>name of the load-balancer resource</td>
    </tr>
            <tr>
    <td>pem_file</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>path to the pem file associated with the service account email (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>port_range</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the port (range) to forward, e.g. 80 or 8000-8888 defaults to all ports</td>
    </tr>
            <tr>
    <td>project_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>your GCE project ID (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>protocol</td>
    <td>no</td>
    <td>tcp</td>
        <td><ul><li>tcp</li><li>udp</li></ul></td>
        <td>the protocol used for the load-balancer packet forwarding, tcp or udp</td>
    </tr>
            <tr>
    <td>region</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the GCE region where the load-balancer is defined</td>
    </tr>
            <tr>
    <td>service_account_email</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>service account email (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>active</li><li>present</li><li>absent</li><li>deleted</li></ul></td>
        <td>desired state of the LB</td>
    </tr>
        </table>


.. note:: Requires libcloud


Examples
--------

.. raw:: html

    <br/>


::

    # Simple example of creating a new LB, adding members, and a health check
    - local_action: 
        module: gce_lb
        name: testlb
        region: us-central1
        members: ["us-central1-a/www-a", "us-central1-b/www-b"]
        httphealthcheck_name: hc
        httphealthcheck_port: 80
        httphealthcheck_path: "/up"



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

