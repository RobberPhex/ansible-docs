.. _swdepot:


swdepot - Manage packages with swdepot package manager (HP-UX)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Will install, upgrade and remove packages with swdepot package manager (HP-UX)




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
                <tr><td>depot<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The source repository from which install or upgrade a package.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>package name.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>latest</li><li>absent</li></ul></td>
        <td><div>whether to install (<code>present</code>, <code>latest</code>), or remove (<code>absent</code>) a package.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - swdepot:
        name: unzip-6.0
        state: installed
        depot: 'repository:/path'
    
    - swdepot:
        name: unzip
        state: latest
        depot: 'repository:/path'
    
    - swdepot:
        name: unzip
        state: absent





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
