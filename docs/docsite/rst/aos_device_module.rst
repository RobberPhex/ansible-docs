.. _aos_device:


aos_device - Manage Devices on AOS Server
+++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Apstra AOS Device module let you manage your devices in AOS easily. You can approve devices and define in which state the device should be. Currently only the state *normal* is supported but the goal is to extend this module with additional state. This module is idempotent and support the *check* mode. It's using the AOS REST API.


Requirements (on host that executes module)
-------------------------------------------

  * aos-pyez >= 0.6.0


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
                <tr><td>approve<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>The approve argument instruct the module to convert a device in quarantine mode into approved mode.</div>        </td></tr>
                <tr><td>id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The AOS internal id for a device; i.e. uniquely identifies the device in the AOS system. Only one of <em>name</em> or <em>id</em> can be set.</div>        </td></tr>
                <tr><td>location<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>When approving a device using the <em>approve</em> argument, it's possible define the location of the device.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The device serial-number; i.e. uniquely identifies the device in the AOS system. Only one of <em>name</em> or <em>id</em> can be set.</div>        </td></tr>
                <tr><td>session<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>An existing AOS session as obtained by <span class='module'>aos_login</span> module.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>normal</td>
        <td><ul><li>normal</li></ul></td>
        <td><div>Define in which state the device should be. Currently only <em>normal</em> is supported but the goal is to add <em>maint</em> and <em>decomm</em>.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    - name: Approve a new device
      aos_device:
        session: "{{ aos_session }}"
        name: D2060B2F105429GDABCD123
        state: 'normal'
        approve: true
        location: "rack-45, ru-18"





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
