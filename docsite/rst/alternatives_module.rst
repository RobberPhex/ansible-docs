.. _alternatives:


alternatives - Manages alternative programs for common commands
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages symbolic links using the 'update-alternatives' tool
Useful when multiple programs are installed but provide similar functionality (e.g. different editors).


Requirements (on host that executes module)
-------------------------------------------

  * update-alternatives


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
    <td>link<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The path to the symbolic link that should point to the real executable.</div><div>This option is required on RHEL-based distributions</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The generic name of the link.</div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The path to the real executable that the link should point to.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: correct java version selected
      alternatives: name=java path=/usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java
    
    - name: alternatives link created
      alternatives: name=hadoop-conf link=/etc/hadoop/conf path=/etc/hadoop/conf.ansible




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

