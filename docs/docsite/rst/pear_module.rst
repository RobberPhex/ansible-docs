.. _pear:


pear - Manage pear/pecl packages
++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage PHP packages with the pear package manager.




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
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the package to install, upgrade, or remove.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>latest</li></ul></td>
        <td><div>Desired state of the package.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Install pear package
    - pear:
        name: Net_URL2
        state: present
    
    # Install pecl package
    - pear:
        name: pecl/json_post
        state: present
    
    # Upgrade package
    - pear:
        name: Net_URL2
        state: latest
    
    # Remove packages
    - pear:
        name: Net_URL2,pecl/json_post
        state: absent





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
