.. _slackpkg:


slackpkg - Package manager for Slackware >= 12.2
++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage binary packages for Slackware using 'slackpkg' which is available in versions after 12.2.


Requirements
------------

  * Slackware >= 12.2


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
        <td><div>name of package to install/remove</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>latest</li></ul></td>
        <td><div>state of the package, you can use "installed" as an alias for <code>present</code> and removed as one for c(absent).</div></td></tr>
            <tr>
    <td>update_cache<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>update the package database first</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Install package foo
    - slackpkg: name=foo state=present
    
    # Remove packages foo and bar
    - slackpkg: name=foo,bar state=absent
    
    # Make sure that it is the most updated package
    - slackpkg: name=foo state=latest
    




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

