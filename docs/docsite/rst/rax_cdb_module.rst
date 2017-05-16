.. _rax_cdb:


rax_cdb - create/delete or resize a Rackspace Cloud Databases instance
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.8


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* creates / deletes or resize a Rackspace Cloud Databases instance and optionally waits for it to be 'running'. The name option needs to be unique since it's used to identify the instance.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * pyrax


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
                <tr><td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Rackspace API key, overrides <em>credentials</em>.</div></br>
    <div style="font-size: small;">aliases: password<div>        </td></tr>
                <tr><td>cdb_type<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>MySQL</td>
        <td></td>
        <td><div>type of instance (i.e. MySQL, MariaDB, Percona)</div></br>
    <div style="font-size: small;">aliases: type<div>        </td></tr>
                <tr><td>cdb_version<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>5.1</li><li>5.6</li><li>10</li></ul></td>
        <td><div>version of database (MySQL supports 5.1 and 5.6, MariaDB supports 10, Percona supports 5.6)</div></br>
    <div style="font-size: small;">aliases: version<div>        </td></tr>
                <tr><td>credentials<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>File to find the Rackspace credentials in. Ignored if <em>api_key</em> and <em>username</em> are provided.</div></br>
    <div style="font-size: small;">aliases: creds_file<div>        </td></tr>
                <tr><td>env<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Environment as configured in <em>~/.pyrax.cfg</em>, see <a href='https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration'>https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration</a>.</div>        </td></tr>
                <tr><td>flavor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td></td>
        <td><div>flavor to use for the instance 1 to 6 (i.e. 512MB to 16GB)</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the databases server instance</div>        </td></tr>
                <tr><td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>DFW</td>
        <td></td>
        <td><div>Region to create an instance in.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the resource</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Rackspace username, overrides <em>credentials</em>.</div>        </td></tr>
                <tr><td>verify_ssl<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Whether or not to require SSL validation of API endpoints.</div>        </td></tr>
                <tr><td>volume<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>2</td>
        <td></td>
        <td><div>Volume size of the database 1-150GB</div>        </td></tr>
                <tr><td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>wait for the instance to be in state 'running' before returning</div>        </td></tr>
                <tr><td>wait_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>300</td>
        <td></td>
        <td><div>how long before wait gives up, in seconds</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Build a Cloud Databases
      gather_facts: False
      tasks:
        - name: Server build request
          local_action:
            module: rax_cdb
            credentials: ~/.raxpub
            region: IAD
            name: db-server1
            flavor: 1
            volume: 2
            cdb_type: MySQL
            cdb_version: 5.6
            wait: yes
            state: present
          register: rax_db_server


Notes
-----

.. note::
    - The following environment variables can be used, ``RAX_USERNAME``, ``RAX_API_KEY``, ``RAX_CREDS_FILE``, ``RAX_CREDENTIALS``, ``RAX_REGION``.
    - ``RAX_CREDENTIALS`` and ``RAX_CREDS_FILE`` points to a credentials file appropriate for pyrax. See https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#authenticating
    - ``RAX_USERNAME`` and ``RAX_API_KEY`` obviate the use of a credentials file
    - ``RAX_REGION`` defines a Rackspace Public Cloud region (DFW, ORD, LON, ...)



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
