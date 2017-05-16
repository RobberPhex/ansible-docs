.. _getent:


getent - a wrapper to the unix getent utility
+++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.8


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Runs getent against one of it's various databases and returns information into the host's facts, in a getent_<database> prefixed variable




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
                <tr><td>database<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>the name of a getent database supported by the target system (passwd, group, hosts, etc).</div>        </td></tr>
                <tr><td>fail_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>If a supplied key is missing this will make the task fail if True</div>        </td></tr>
                <tr><td>key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>key from which to return values from the specified database, otherwise the full contents are returned.</div>        </td></tr>
                <tr><td>split<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>character used to split the database values into lists/arrays such as ':' or '	', otherwise  it will try to pick one depending on the database</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # get root user info
    - getent:
        database: passwd
        key: root
    - debug:
        var: getent_passwd
    
    # get all groups
    - getent:
        database: group
        split: ':'
    - debug:
        var: getent_group
    
    # get all hosts, split by tab
    - getent:
        database: hosts
    - debug:
        var: getent_hosts
    
    # get http service info, no error if missing
    - getent:
        database: services
        key: http
        fail_key: False
    - debug:
        var: getent_services
    
    # get user password hash (requires sudo/root)
    - getent:
        database: shadow
        key: www-data
        split: ':'
    - debug:
        var: getent_shadow
    


Notes
-----

.. note::
    - Not all databases support enumeration, check system documentation for details



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
