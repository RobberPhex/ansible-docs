.. _firewalld:


firewalld - Manage arbitrary ports/services with firewalld
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.4

This module allows for addition or deletion of services and ports either tcp or udp in either running or permanent firewalld rules

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
    <td>permanent</td>
    <td>yes</td>
    <td>True</td>
        <td><ul></ul></td>
        <td>Should this configuration be in the running firewalld configuration or persist across reboots</td>
    </tr>
            <tr>
    <td>port</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of a port to add/remove to/from firewalld must be in the form PORT/PROTOCOL</td>
    </tr>
            <tr>
    <td>rich_rule</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Rich rule to add/remove to/from firewalld</td>
    </tr>
            <tr>
    <td>service</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of a service to add/remove to/from firewalld - service must be listed in /etc/services</td>
    </tr>
            <tr>
    <td>state</td>
    <td>yes</td>
    <td>enabled</td>
        <td><ul></ul></td>
        <td>Should this port accept(enabled) or reject(disabled) connections</td>
    </tr>
            <tr>
    <td>timeout</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The amount of time the rule should be in effect for when non-permanent</td>
    </tr>
            <tr>
    <td>zone</td>
    <td>no</td>
    <td>system-default(public)</td>
        <td><ul><li>work</li><li>drop</li><li>internal</li><li>external</li><li>trusted</li><li>home</li><li>dmz</li><li>public</li><li>block</li></ul></td>
        <td>The firewalld zone to add/remove to/from (NOTE: default zone can be configured per system but "public" is default from upstream. Available choices can be extended based on per-system configs, listed here are "out of the box" defaults).</td>
    </tr>
        </table>


.. note:: Requires firewalld >= 0.2.11


Examples
--------

.. raw:: html

    <br/>


::

    - firewalld: service=https permanent=true state=enabled
    - firewalld: port=8081/tcp permanent=true state=disabled
    - firewalld: zone=dmz service=http permanent=true state=enabled
    - firewalld: rich_rule='rule service name="ftp" audit limit value="1/m" accept' permanent=true state=enabled

.. note:: Not tested on any debian based system


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

