.. _vertica_configuration:


vertica_configuration - Updates Vertica configuration parameters.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Updates Vertica configuration parameters.


Requirements
------------

  * unixODBC
  * pyodbc


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
    <td>cluster<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>localhost</td>
        <td><ul></ul></td>
        <td><div>Name of the Vertica cluster.</div></td></tr>
            <tr>
    <td>db<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the Vertica database.</div></td></tr>
            <tr>
    <td>login_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password used to authenticate with.</div></td></tr>
            <tr>
    <td>login_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>dbadmin</td>
        <td><ul></ul></td>
        <td><div>The username used to authenticate with.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the parameter to update.</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5433</td>
        <td><ul></ul></td>
        <td><div>Vertica cluster port to connect to.</div></td></tr>
            <tr>
    <td>value<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Value of the parameter to be set.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: updating load_balance_policy
      vertica_configuration: name=failovertostandbyafter value='8 hours'


Notes
-----

.. note:: The default authentication assumes that you are either logging in as or sudo'ing to the ``dbadmin`` account on the host.
.. note:: This module uses ``pyodbc``, a Python ODBC database adapter. You must ensure that ``unixODBC`` and ``pyodbc`` is installed on the host and properly configured.
.. note:: Configuring ``unixODBC`` for Vertica requires ``Driver = /opt/vertica/lib64/libverticaodbc.so`` to be added to the ``Vertica`` section of either ``/etc/odbcinst.ini`` or ``$HOME/.odbcinst.ini`` and both ``ErrorMessagesPath = /opt/vertica/lib64`` and ``DriverManagerEncoding = UTF-16`` to be added to the ``Driver`` section of either ``/etc/vertica.ini`` or ``$HOME/.vertica.ini``.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

