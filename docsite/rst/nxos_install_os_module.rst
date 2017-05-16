.. _nxos_install_os:


nxos_install_os - Set boot options like boot image and kickstart image.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Install an operating system by setting the boot options like boot image and kickstart image.




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
    <td>kickstart_image_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the kickstart image file on flash.</div></td></tr>
            <tr>
    <td>system_image_file<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the system (or combined) image file on flash.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - block:
        - name: Install OS
          nxos_install_os:
            system_image_file: nxos.7.0.3.I2.2d.bin
            host: "{{ inventory_hostname }}"
            username: "{{ un }}"
            password: "{{ pwd }}"
            transport: nxapi
        rescue:
          - name: Wait for device to perform checks 
            wait_for:
              port: 22
              state: stopped
              timeout: 300
              delay: 60
              host: "{{ inventory_hostname }}"
          - name: Wait for device to come back up
            wait_for:
              port: 22
              state: started
              timeout: 300
              delay: 60
              host: "{{ inventory_hostname }}"
          - name: Check installed OS
            nxos_command:
              commands:
                - show version
              username: "{{ un }}"
              password: "{{ pwd }}"
              host: "{{ inventory_hostname }}"
              transport: nxapi
            register: output
          - assert:
              that:
                - output['stdout'][0]['kickstart_ver_str'] == '7.0(3)I4(1)'

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
        <td> install_state </td>
        <td>  </td>
        <td align=center> always </td>
        <td align=center> dictionary </td>
        <td align=center> {'sys': 'n5000-uk9.7.2.1.N1.1.bin', 'status': 'This is the log of last installation.\nContinuing with installation process, please wait.\nThe login will be disabled until the installation is completed.\nPerforming supervisor state verification.\nSUCCESS\nSupervisor non-disruptive upgrade successful.\nInstall has been successful. ', 'kick': 'n5000-uk9-kickstart.7.2.1.N1.1.bin'} </td>
    </tr>
        <tr><td>contains: </td>
    <td colspan=4>
        <table border=1 cellpadding=2>
        <tr>
        <th class="head">name</th>
        <th class="head">description</th>
        <th class="head">returned</th>
        <th class="head">type</th>
        <th class="head">sample</th>
        </tr>

        
        </table>
    </td></tr>

        
    </table>
    </br></br>

Notes
-----

.. note:: The module will fail due to timeout issues, but the install will go on anyway. Ansible's block and rescue can be leveraged to handle this kind of failure and check actual module results. See EXAMPLE for more about this. The first task on the rescue block is needed to make sure the device has completed all checks and it started to reboot. The second task is needed to wait for the device to come back up. The last two tasks are used to verify the installation process was successful.
.. note:: Do not include full file paths, just the name of the file(s) stored on the top level flash directory.
.. note:: You must know if your platform supports taking a kickstart image as a parameter. If supplied but not supported, errors may occur.
.. note:: This module attempts to install the software immediately, which may trigger a reboot.
.. note:: In check mode, the module tells you if the current boot images are set to the desired images.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

