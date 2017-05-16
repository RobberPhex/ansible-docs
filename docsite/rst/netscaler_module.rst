.. _netscaler:


netscaler - Manages Citrix NetScaler entities
+++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.1

Manages Citrix NetScaler server and service entities.

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
    <td>action</td>
    <td>no</td>
    <td>disable</td>
        <td><ul><li>enable</li><li>disable</li></ul></td>
        <td>the action you want to perform on the entity</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td>hostname</td>
        <td><ul></ul></td>
        <td>name of the entity</td>
    </tr>
            <tr>
    <td>nsc_host</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>hostname or ip of your netscaler</td>
    </tr>
            <tr>
    <td>nsc_protocol</td>
    <td>no</td>
    <td>https</td>
        <td><ul></ul></td>
        <td>protocol used to access netscaler</td>
    </tr>
            <tr>
    <td>password</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>password</td>
    </tr>
            <tr>
    <td>type</td>
    <td>no</td>
    <td>server</td>
        <td><ul><li>server</li><li>service</li></ul></td>
        <td>type of the entity</td>
    </tr>
            <tr>
    <td>user</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>username</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>no</code>, SSL certificates for the target url will not be validated. This should only be used on personally controlled sites using self-signed certificates.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Disable the server
    ansible host -m netscaler -a "nsc_host=nsc.example.com user=apiuser password=apipass"
    
    # Enable the server
    ansible host -m netscaler -a "nsc_host=nsc.example.com user=apiuser password=apipass action=enable"
    
    # Disable the service local:8080
    ansible host -m netscaler -a "nsc_host=nsc.example.com user=apiuser password=apipass name=local:8080 type=service action=disable"



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

