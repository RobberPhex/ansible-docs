.. _apache2_module:


apache2_module - enables/disables a module of the Apache2 webserver
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Enables or disables a specified module of the Apache2 webserver.


Requirements (on host that executes module)
-------------------------------------------

  * a2enmod
  * a2dismod


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
                <tr><td>force<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>force disabling of default modules and override Debian warnings</div>        </td></tr>
                <tr><td>ignore_configcheck<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Ignore configuration checks about inconsistent module configuration. Especially for mpm_* modules.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>name of the module to enable/disable</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>indicate the desired state of the resource</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # enables the Apache2 module "wsgi"
    - apache2_module:
        state: present
        name: wsgi
    # disables the Apache2 module "wsgi"
    - apache2_module:
        state: absent
        name: wsgi
    # disable default modules for Debian
    - apache2_module:
        state: absent
        name: autoindex
        force: True
    # disable mpm_worker and ignore warnings about missing mpm module
    - apache2_module:
        state: absent
        name: mpm_worker
        ignore_configcheck: True

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
        <td> warnings </td>
        <td> list of warning messages </td>
        <td align=center> when needed </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stdout </td>
        <td> stdout of underlying command </td>
        <td align=center> failed </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> result </td>
        <td> message about action taken </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stderr </td>
        <td> stderr of underlying command </td>
        <td align=center> failed </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> rc </td>
        <td> return code of underlying command </td>
        <td align=center> failed </td>
        <td align=center> int </td>
        <td align=center>  </td>
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
