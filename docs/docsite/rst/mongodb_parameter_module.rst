.. _mongodb_parameter:


mongodb_parameter - Change an administrative parameter on a MongoDB server.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Change an administrative parameter on a MongoDB server.


Requirements (on host that executes module)
-------------------------------------------

  * pymongo


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
        <td><div>The name of the database to add/remove the user from</div>        </td></tr>
                <tr><td>login_database<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The database where login credentials are stored</div>        </td></tr>
                <tr><td>login_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>localhost</td>
        <td></td>
        <td><div>The host running the database</div>        </td></tr>
                <tr><td>login_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The password used to authenticate with</div>        </td></tr>
                <tr><td>login_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>27017</td>
        <td></td>
        <td><div>The port to connect to</div>        </td></tr>
                <tr><td>login_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The username used to authenticate with</div>        </td></tr>
                <tr><td>param<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>MongoDB administrative parameter to modify</div>        </td></tr>
                <tr><td>param_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>str</td>
        <td></td>
        <td><div>Define the parameter value (str, int)</div>        </td></tr>
                <tr><td>replica_set<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Replica set to connect to (automatically connects to primary for writes)</div>        </td></tr>
                <tr><td>ssl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Whether to use an SSL connection when connecting to the database</div>        </td></tr>
                <tr><td>value<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>MongoDB administrative parameter value to set</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Set MongoDB syncdelay to 60 (this is an int)
    - mongodb_parameter:
        param: syncdelay
        value: 60
        param_type: int

Return Values
-------------

Common return values are documented here :doc:`common_return_values`, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> after </td>
        <td> value after modification </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> before </td>
        <td> value before modification </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Requires the pymongo Python package on the remote host, version 2.4.2+. This can be installed using pip or the OS package manager. @see http://api.mongodb.org/python/current/installation.html



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
