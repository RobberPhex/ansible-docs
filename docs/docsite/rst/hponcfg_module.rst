.. _hponcfg:


hponcfg - Configure HP iLO interface using hponcfg
++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This modules configures the HP iLO interface using hponcfg.


Requirements (on host that executes module)
-------------------------------------------

  * hponcfg tool


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
                <tr><td>minfw<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The minimum firmware level needed</div>        </td></tr>
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The XML file as accepted by hponcfg</div></br>
    <div style="font-size: small;">aliases: src<div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Example hponcfg configuration XML
      copy:
        content: |
          <ribcl VERSION="2.0">
            <login USER_LOGIN="user" PASSWORD="password">
              <rib_info MODE="WRITE">
                <mod_global_settings>
                  <session_timeout value="0"/>
                  <ssh_status value="Y"/>
                  <ssh_port value="22"/>
                  <serial_cli_status value="3"/>
                  <serial_cli_speed value="5"/>
                </mod_global_settings>
              </rib_info>
            </login>
          </ribcl>
        dest: /tmp/enable-ssh.xml
    
    - name: Configure HP iLO using enable-ssh.xml
      hponcfg:
        src: /tmp/enable-ssh.xml


Notes
-----

.. note::
    - You need a working hponcfg on the target system.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
