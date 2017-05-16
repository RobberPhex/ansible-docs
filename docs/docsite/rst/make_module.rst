.. _make:


make - Run targets in a Makefile
++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Run targets in a Makefile.


Requirements (on host that executes module)
-------------------------------------------

  * make


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
                <tr><td>chdir<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>cd into this directory before running make</div>        </td></tr>
                <tr><td>params<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td></td>
        <td><div>Any extra parameters to pass to make</div>        </td></tr>
                <tr><td>target<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td></td>
        <td><div>The target to run</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Build the default target
    - make:
        chdir: /home/ubuntu/cool-project
    
    # Run `install` target as root
    - make:
        chdir: /home/ubuntu/cool-project
        target: install
      become: yes
    
    # Pass in extra arguments to build
    - make:
        chdir: /home/ubuntu/cool-project
        target: all
        params:
          NUM_THREADS: 4
          BACKEND: lapack





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
