.. _aix_inittab:


aix_inittab - Manages the inittab on AIX.
+++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages the inittab on AIX.


Requirements (on host that executes module)
-------------------------------------------

  * itertools


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
                <tr><td>action<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>respawn</li><li>wait</li><li>once</li><li>boot</li><li>bootwait</li><li>powerfail</li><li>powerwait</li><li>off</li><li>hold</li><li>ondemand</li><li>initdefault</li><li>sysinit</li></ul></td>
        <td><div>Action what the init has to do with this entry.</div>        </td></tr>
                <tr><td>command<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>What command has to run.</div>        </td></tr>
                <tr><td>insertafter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>After which inittabline should the new entry inserted.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the inittab entry.</div></br>
    <div style="font-size: small;">aliases: service<div>        </td></tr>
                <tr><td>runlevel<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Runlevel of the entry.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the entry should be present or absent in the inittab file</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Add service startmyservice to the inittab, directly after service existingservice.
    - name: Add startmyservice to inittab
      aix_inittab:
        name: startmyservice
        runlevel: 4
        action: once
        command: "echo hello"
        insertafter: existingservice
        state: present
      become: yes
    
    # Change inittab enrty startmyservice to runlevel "2" and processaction "wait".
    - name: Change startmyservice to inittab
      aix_inittab:
        name: startmyservice
        runlevel: 2
        action: wait
        command: "echo hello"
        state: present
      become: yes
    
    # Remove inittab entry startmyservice.
    - name: remove startmyservice from inittab
      aix_inittab:
        name: startmyservice
        runlevel: 2
        action: wait
        command: "echo hello"
        state: absent
      become: yes

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
        <td> msg </td>
        <td> action done with the inittab entry </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> changed inittab entry startmyservice </td>
    </tr>
            <tr>
        <td> changed </td>
        <td> whether the inittab changed or not </td>
        <td align=center>  </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> name </td>
        <td> name of the adjusted inittab entry </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> startmyservice </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - The changes are persistent across reboots, you need root rights to read or adjust the inittab with the lsitab, chitab, mkitab or rmitab commands.
    - tested on AIX 7.1.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
