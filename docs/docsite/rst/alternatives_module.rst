.. _alternatives:


alternatives - Manages alternative programs for common commands
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages symbolic links using the 'update-alternatives' tool
* Useful when multiple programs are installed but provide similar functionality (e.g. different editors).


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
                <tr><td>link<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The path to the symbolic link that should point to the real executable.</div><div>This option is required on RHEL-based distributions</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The generic name of the link.</div>        </td></tr>
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The path to the real executable that the link should point to.</div>        </td></tr>
                <tr><td>priority<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>50</td>
        <td></td>
        <td><div>The priority of the alternative</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: correct java version selected
      alternatives:
        name: java
        path: /usr/lib/jvm/java-7-openjdk-amd64/jre/bin/java
    
    - name: alternatives link created
      alternatives:
        name: hadoop-conf
        link: /etc/hadoop/conf
        path: /etc/hadoop/conf.ansible
    
    - name: make java 32 bit an alternative with low priority
      alternatives:
        name: java
        path: /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java
        priority: -10





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
