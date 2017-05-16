.. _atomic_image:


atomic_image - Manage the container images on the atomic host platform
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage the container images on the atomic host platform
Allows to execute the commands on the container images


Requirements (on host that executes module)
-------------------------------------------

  * atomic
  * python >= 2.6


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
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the container image</div></td></tr>
            <tr>
    <td>started<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Start or Stop the continer</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>latest</td>
        <td><ul><li>present</li><li>absent</li><li>latest</li></ul></td>
        <td><div>The state of the container image.</div><div>The state ```latest``` will ensure container image is upgraded to the latest version and forcefully restart container, if running.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    # Execute the run command on rsyslog container image (atomic run rhel7/rsyslog)
    - atomic_image: name=rhel7/rsyslog state=latest
    

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
        <td> The command standard output </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> [{"u'Using default tag": "latest ...'"}] </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: Host should be support ```atomic``` command


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

