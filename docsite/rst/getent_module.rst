.. _getent:


getent - a wrapper to the unix getent utility
+++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.8

Runs getent against one of it's various databases and returns information into the host's facts, in a getent_<database> prefixed variable

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
    <td>database</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>the name of a getent database supported by the target system (passwd, group, hosts, etc).</td>
    </tr>
            <tr>
    <td>fail_key</td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td>If a supplied key is missing this will make the task fail if True</td>
    </tr>
            <tr>
    <td>key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>key from which to return values from the specified database, otherwise the full contents are returned.</td>
    </tr>
            <tr>
    <td>split</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>character used to split the database values into lists/arrays such as ':' or '	', otherwise  it will try to pick one depending on the database</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # get root user info
    - getent: database=passwd key=root
    - debug: var=getent_passwd
    
    # get all groups
    - getent: database=group split=':'
    - debug: var=getent_group
    
    # get all hosts, split by tab
    - getent: database=hosts
    - debug: var=getent_hosts
    
    # get http service info, no error if missing
    - getent: database=services key=http fail_key=False
    - debug: var=getent_services
    
    # get user password hash (requires sudo/root)
    - getent: database=shadow key=www-data split=:
    - debug: var=getent_shadow
    

.. note:: Not all databases support enumeration, check system documentation for details


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

