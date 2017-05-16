.. _osx_defaults:


osx_defaults - osx_defaults allows users to read, write, and delete Mac OS X user defaults from Ansible
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* osx_defaults allows users to read, write, and delete Mac OS X user defaults from Ansible scripts. Mac OS X applications and other programs use the defaults system to record user preferences and other information that must be maintained when the applications aren't running (such as default font for new documents, or the position of an Info panel).




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
                <tr><td>array_add<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Add new elements to the array for a key which has an array as its value.</div>        </td></tr>
                <tr><td>domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>NSGlobalDomain</td>
        <td></td>
        <td><div>The domain is a domain name of the form com.companyname.appname.</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The host on which the preference should apply. The special value "currentHost" corresponds to the "-currentHost" switch of the defaults commandline tool.</div>        </td></tr>
                <tr><td>key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The key of the user preference</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>The state of the user defaults</div>        </td></tr>
                <tr><td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>string</td>
        <td><ul><li>array</li><li>bool</li><li>boolean</li><li>date</li><li>float</li><li>int</li><li>integer</li><li>string</li></ul></td>
        <td><div>The type of value to write.</div>        </td></tr>
                <tr><td>value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The value to write. Only required when state = present.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - osx_defaults:
        domain: com.apple.Safari
        key: IncludeInternalDebugMenu
        type: bool
        value: true
        state: present
    
    - osx_defaults:
        domain: NSGlobalDomain
        key: AppleMeasurementUnits
        type: string
        value: Centimeters
        state: present
    
    - osx_defaults:
        domain: com.apple.screensaver
        host: currentHost
        key: showClock
        type: int
        value: 1
    
    - osx_defaults:
        key: AppleMeasurementUnits
        type: string
        value: Centimeters
    
    - osx_defaults:
        key: AppleLanguages
        type: array
        value:
          - en
          - nl
    
    - osx_defaults:
        domain: com.geekchimp.macable
        key: ExampleKeyToRemove
        state: absent


Notes
-----

.. note::
    - Apple Mac caches defaults. You may need to logout and login to apply the changes.



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
