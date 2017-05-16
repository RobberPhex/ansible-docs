.. _seport:


seport - Manages SELinux network port type definitions
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages SELinux network port type definitions.


Requirements
------------

  * libselinux-python
  * policycoreutils-python


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
    <td>ports<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Ports or port ranges, separated by a comma</div></td></tr>
            <tr>
    <td>proto<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>tcp</li><li>udp</li></ul></td>
        <td><div>Protocol for the specified port.</div></td></tr>
            <tr>
    <td>reload<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Reload SELinux policy after commit.</div></td></tr>
            <tr>
    <td>setype<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>SELinux type for the specified port.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Desired boolean value.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Allow Apache to listen on tcp port 8888
    - seport: ports=8888 proto=tcp setype=http_port_t state=present
    # Allow sshd to listen on tcp port 8991
    - seport: ports=8991 proto=tcp setype=ssh_port_t state=present
    # Allow memcached to listen on tcp ports 10000-10100 and 10112
    - seport: ports=10000-10100,10112 proto=tcp setype=memcache_port_t state=present


Notes
-----

.. note:: The changes are persistent across reboots
.. note:: Not tested on any debian based system


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

