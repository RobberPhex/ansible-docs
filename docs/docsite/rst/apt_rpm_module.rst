.. _apt_rpm:


apt_rpm - apt_rpm package manager
+++++++++++++++++++++++++++++++++

.. versionadded:: 1.5


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages packages with *apt-rpm*. Both low-level (*rpm*) and high-level (*apt-get*) package manager binaries required.




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
                <tr><td>pkg<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>name of package to install, upgrade or remove.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>Indicates the desired package state</div>        </td></tr>
                <tr><td>update_cache<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>update the package database first <code>apt-get update</code>.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # install package foo
    - apt_rpm:
        pkg: foo
        state: present
    
    # remove package foo
    - apt_rpm:
        pkg: foo
        state: absent
    
    # description: remove packages foo and bar
    - apt_rpm:
        pkg: foo,bar
        state: absent
    
    # description: update the package database and install bar (bar will be the updated if a newer version exists)
    - apt_rpm:
        name: bar
        state: present
        update_cache: yes





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
