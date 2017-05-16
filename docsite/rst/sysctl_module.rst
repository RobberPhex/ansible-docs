.. _sysctl:


sysctl - Manage entries in sysctl.conf.
+++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module manipulates sysctl entries and optionally performs a ``/sbin/sysctl -p`` after changing them.




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
    <td>ignoreerrors<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Use this option to ignore errors about unknown keys.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The dot-separated path (aka <em>key</em>) specifying the sysctl variable.</div></br>
        <div style="font-size: small;">aliases: key<div></td></tr>
            <tr>
    <td>reload<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>yes</code>, performs a <em>/sbin/sysctl -p</em> if the <code>sysctl_file</code> is updated. If <code>no</code>, does not reload <em>sysctl</em> even if the <code>sysctl_file</code> is updated.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the entry should be present or absent in the sysctl file.</div></td></tr>
            <tr>
    <td>sysctl_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/etc/sysctl.conf</td>
        <td><ul></ul></td>
        <td><div>Specifies the absolute path to <code>sysctl.conf</code>, if not <code>/etc/sysctl.conf</code>.</div></td></tr>
            <tr>
    <td>sysctl_set<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Verify token value with the sysctl command and set with -w if necessary</div></td></tr>
            <tr>
    <td>value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Desired value of the sysctl key.</div></br>
        <div style="font-size: small;">aliases: val<div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Set vm.swappiness to 5 in /etc/sysctl.conf
    - sysctl: 
        name: vm.swappiness 
        value: 5
        state: present
    
    # Remove kernel.panic entry from /etc/sysctl.conf
    - sysctl:
        name: kernel.panic
        state: absent 
        sysctl_file: /etc/sysctl.conf
    
    # Set kernel.panic to 3 in /tmp/test_sysctl.conf
    - sysctl: name=kernel.panic value=3 sysctl_file=/tmp/test_sysctl.conf reload=no
    
    # Set ip forwarding on in /proc and do not reload the sysctl file
    - sysctl: name="net.ipv4.ip_forward" value=1 sysctl_set=yes
    
    # Set ip forwarding on in /proc and in the sysctl file and reload if necessary
    - sysctl: name="net.ipv4.ip_forward" value=1 sysctl_set=yes state=present reload=yes




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

