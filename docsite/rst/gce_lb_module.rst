.. _gce_lb:


gce_lb - create/destroy GCE load-balancer resources
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.5


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module can create and destroy Google Compute Engine ``loadbalancer`` and ``httphealthcheck`` resources.  The primary LB resource is the ``load_balancer`` resource and the health check parameters are all prefixed with *httphealthcheck*. The full documentation for Google Compute Engine load balancing is at https://developers.google.com/compute/docs/load-balancing/.  However, the ansible module simplifies the configuration by following the libcloud model. Full install/configuration instructions for the gce* modules can be found in the comments of ansible/test/gce_tests.py.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * apache-libcloud >= 0.13.3, >= 0.17.0 if using JSON credentials


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
    <td>credentials_file<br/><div style="font-size: small;"> (added in 2.1.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>path to the JSON file associated with the service account email</div></td></tr>
            <tr>
    <td>external_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the external static IPv4 (or auto-assigned) address for the LB</div></td></tr>
            <tr>
    <td>httphealthcheck_healthy_count<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>2</td>
        <td><ul></ul></td>
        <td><div>number of consecutive successful checks before marking a node healthy</div></td></tr>
            <tr>
    <td>httphealthcheck_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>host header to pass through on HTTP check requests</div></td></tr>
            <tr>
    <td>httphealthcheck_interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5</td>
        <td><ul></ul></td>
        <td><div>the duration in seconds between each health check request</div></td></tr>
            <tr>
    <td>httphealthcheck_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the name identifier for the HTTP health check</div></td></tr>
            <tr>
    <td>httphealthcheck_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/</td>
        <td><ul></ul></td>
        <td><div>the url path to use for HTTP health checking</div></td></tr>
            <tr>
    <td>httphealthcheck_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>80</td>
        <td><ul></ul></td>
        <td><div>the TCP port to use for HTTP health checking</div></td></tr>
            <tr>
    <td>httphealthcheck_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5</td>
        <td><ul></ul></td>
        <td><div>the timeout in seconds before a request is considered a failed check</div></td></tr>
            <tr>
    <td>httphealthcheck_unhealthy_count<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>2</td>
        <td><ul></ul></td>
        <td><div>number of consecutive failed checks before marking a node unhealthy</div></td></tr>
            <tr>
    <td>members<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>a list of zone/nodename pairs, e.g ['us-central1-a/www-a', ...]</div></br>
        <div style="font-size: small;">aliases: nodes<div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of the load-balancer resource</div></td></tr>
            <tr>
    <td>pem_file<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>path to the pem file associated with the service account email This option is deprecated. Use 'credentials_file'.</div></td></tr>
            <tr>
    <td>port_range<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the port (range) to forward, e.g. 80 or 8000-8888 defaults to all ports</div></td></tr>
            <tr>
    <td>project_id<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>your GCE project ID</div></td></tr>
            <tr>
    <td>protocol<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>tcp</td>
        <td><ul><li>tcp</li><li>udp</li></ul></td>
        <td><div>the protocol used for the load-balancer packet forwarding, tcp or udp</div></td></tr>
            <tr>
    <td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the GCE region where the load-balancer is defined</div></td></tr>
            <tr>
    <td>service_account_email<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>service account email</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>active</li><li>present</li><li>absent</li><li>deleted</li></ul></td>
        <td><div>desired state of the LB</div></td></tr>
        </table>
    </br>



Examples
--------

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

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

