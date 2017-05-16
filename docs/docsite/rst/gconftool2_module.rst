.. _gconftool2:


gconftool2 - Edit GNOME Configurations
++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module allows for the manipulation of GNOME 2 Configuration via gconftool-2.  Please see the gconftool-2(1) man pages for more details.




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
                <tr><td>config_source<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify a configuration source to use rather than the default path. See man gconftool-2(1)</div>        </td></tr>
                <tr><td>direct<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Access the config database directly, bypassing server.  If direct is specified then the config_source must be specified as well. See man gconftool-2(1)</div>        </td></tr>
                <tr><td>key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>A GConf preference key is an element in the GConf repository that corresponds to an application preference. See man gconftool-2(1)</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>get</li><li>present</li><li>absent</li></ul></td>
        <td><div>The action to take upon the key/value.</div>        </td></tr>
                <tr><td>value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Preference keys typically have simple values such as strings, integers, or lists of strings and integers. This is ignored if the state is "get". See man gconftool-2(1)</div>        </td></tr>
                <tr><td>value_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>int</li><li>bool</li><li>float</li><li>string</li></ul></td>
        <td><div>The type of value being set. This is ignored if the state is "get".</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Change the widget font to "Serif 12"
      gconftool2:
        key: "/desktop/gnome/interface/font_name"
        value_type: "string"
        value: "Serif 12"

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
        <td> value_type </td>
        <td> The type of the value that was changed </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> string </td>
    </tr>
            <tr>
        <td> key </td>
        <td> The key specified in the module parameters </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> /desktop/gnome/interface/font_name </td>
    </tr>
            <tr>
        <td> value </td>
        <td> The value of the preference key after executing the module </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Serif 12 </td>
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
