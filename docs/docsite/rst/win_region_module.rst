.. _win_region:


win_region - Set the region and format settings
+++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Set the location settings of a Windows Server.
* Set the format settings of a Windows Server.
* Set the unicode language settings of a Windows Server.
* Copy across these settings to the default profile.




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
                <tr><td>copy_settings<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>This will copy the current format and location values to new user profiles and the welcome screen. This will only run if <code>location</code>, <code>format</code> or <code>unicode_language</code> has resulted in a change. If this process runs then it will always result in a change.</div>        </td></tr>
                <tr><td>format<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The language format to set for the current user, see <a href='https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx'>https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx</a> for a list of culture names to use. This needs to be set if <code>location</code> or <code>unicode_language</code> is not set.</div>        </td></tr>
                <tr><td>location<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The location to set for the current user, see <a href='https://msdn.microsoft.com/en-us/library/dd374073.aspx'>https://msdn.microsoft.com/en-us/library/dd374073.aspx</a> for a list of GeoIDs you can use and what location it relates to. This needs to be set if <code>format</code> or <code>unicode_language</code> is not set.</div>        </td></tr>
                <tr><td>unicode_language<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The unicode language format to set for all users, see <a href='https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx'>https://msdn.microsoft.com/en-us/library/system.globalization.cultureinfo.aspx</a> for a list of culture names to use. This needs to be set if <code>location</code> or <code>format</code> is not set. After setting this value a reboot is required for it to take effect.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Set the region format to English United States
    - win_region:
        format: en-US
    
    # Set the region format to English Australia and copy settings to new profiles
    - win_region:
        format: en-AU
        copy_settings: True
    
    # Set the unicode language to English Great Britain
    - win_region:
        unicode_language: en-GB
      register: result
    
    - action: win_reboot
      when: result.restart_required
    
    # Set the location to United States
    - win_region:
        location: 244
    
    # Set format, location and unicode to English Australia and copy settings
    - win_region:
        location: 12
        format: en-AU
        unicode_language: en-AU
      register: result
    
    - action: win_reboot
      when: result.restart_required

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
        <td> changed </td>
        <td> Whether anything was changed </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> restart_required </td>
        <td> Whether a reboot is required for the change to take effect </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
