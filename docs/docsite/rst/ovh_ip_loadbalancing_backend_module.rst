.. _ovh_ip_loadbalancing_backend:


ovh_ip_loadbalancing_backend - Manage OVH IP LoadBalancing backends
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage OVH (French European hosting provider) LoadBalancing IP backends


Requirements (on host that executes module)
-------------------------------------------

  * ovh >  0.3.5


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
                <tr><td>application_key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The applicationKey to use</div>        </td></tr>
                <tr><td>application_secret<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The application secret to use</div>        </td></tr>
                <tr><td>backend<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The IP address of the backend to update / modify / delete</div>        </td></tr>
                <tr><td>consumer_key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The consumer key to use</div>        </td></tr>
                <tr><td>endpoint<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The endpoint to use ( for instance ovh-eu)</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the LoadBalancing internal name (ip-X.X.X.X)</div>        </td></tr>
                <tr><td>probe<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td><ul><li>none</li><li>http</li><li>icmp</li><li>oco</li></ul></td>
        <td><div>Determines the type of probe to use for this backend</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Determines whether the backend is to be created/modified or deleted</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>120</td>
        <td></td>
        <td><div>The timeout in seconds used to wait for a task to be completed.</div>        </td></tr>
                <tr><td>weight<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>8</td>
        <td></td>
        <td><div>Determines the weight for this backend</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Adds or modify the backend '212.1.1.1' to a
    # loadbalancing 'ip-1.1.1.1'
    - ovh_ip_loadbalancing:
        name: ip-1.1.1.1
        backend: 212.1.1.1
        state: present
        probe: none
        weight: 8
        endpoint: ovh-eu
        application_key: yourkey
        application_secret: yoursecret
        consumer_key: yourconsumerkey
    
    # Removes a backend '212.1.1.1' from a loadbalancing 'ip-1.1.1.1'
    - ovh_ip_loadbalancing:
        name: ip-1.1.1.1
        backend: 212.1.1.1
        state: absent
        endpoint: ovh-eu
        application_key: yourkey
        application_secret: yoursecret
        consumer_key: yourconsumerkey


Notes
-----

.. note::
    - Uses the python OVH Api https://github.com/ovh/python-ovh. You have to create an application (a key and secret) with a consummer key as described into https://eu.api.ovh.com/g934.first_step_with_api



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
