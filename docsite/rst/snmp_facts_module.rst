.. _snmp_facts:


snmp_facts - Retrive facts for a device using SNMP.
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.9

Retrieve facts for a device using SNMP, the facts will be inserted to the ansible_facts key.

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
    <td>authkey</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Authentication key, required if version is v3</td>
    </tr>
            <tr>
    <td>community</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The SNMP community string, required if version is v2/v2c</td>
    </tr>
            <tr>
    <td>host</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Set to target snmp server (normally {{inventory_hostname}})</td>
    </tr>
            <tr>
    <td>integrity</td>
    <td>no</td>
    <td></td>
        <td><ul><li>md5</li><li>sha</li></ul></td>
        <td>Hashing algoritm, required if version is v3</td>
    </tr>
            <tr>
    <td>level</td>
    <td>no</td>
    <td></td>
        <td><ul><li>authPriv</li><li>authNoPriv</li></ul></td>
        <td>Authentication level, required if version is v3</td>
    </tr>
            <tr>
    <td>privacy</td>
    <td>no</td>
    <td></td>
        <td><ul><li>des</li><li>aes</li></ul></td>
        <td>Encryption algoritm, required if level is authPriv</td>
    </tr>
            <tr>
    <td>privkey</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Encryption key, required if version is authPriv</td>
    </tr>
            <tr>
    <td>username</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Username for SNMPv3, required if version is v3</td>
    </tr>
            <tr>
    <td>version</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>v2</li><li>v2c</li><li>v3</li></ul></td>
        <td>SNMP Version to use, v2/v2c or v3</td>
    </tr>
        </table>


.. note:: Requires pysnmp


Examples
--------

.. raw:: html

    <br/>


::

    # Gather facts with SNMP version 2
    - snmp_facts: host={{ inventory_hostname }} version=2c community=public
      connection: local
    
    # Gather facts using SNMP version 3
    - snmp_facts:
        host={{ inventory_hostname }}
        version=v3
        level=authPriv
        integrity=sha
        privacy=aes
        username=snmp-user
        authkey=abc12345
        privkey=def6789
      delegate_to: localhost



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

