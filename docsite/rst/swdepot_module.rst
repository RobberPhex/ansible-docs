.. _swdepot:


swdepot - Manage packages with swdepot package manager (HP-UX)
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Will install, upgrade and remove packages with swdepot package manager (HP-UX)




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
    <td>depot<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The source repository from which install or upgrade a package.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>package name.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>latest</li><li>absent</li></ul></td>
        <td><div>whether to install (<code>present</code>, <code>latest</code>), or remove (<code>absent</code>) a package.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - swdepot: name=unzip-6.0 state=installed depot=repository:/path
    - swdepot: name=unzip state=latest depot=repository:/path
    - swdepot: name=unzip state=absent




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

