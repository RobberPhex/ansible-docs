.. _tempfile:


tempfile - Creates temporary files and directories.
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* The ``tempfile`` module creates temporary files and directories. ``mktemp`` command takes different parameters on various systems, this module helps to avoid troubles related to that. Files/directories created by module are accessible only by creator. In case you need to make them world-accessible you need to use :ref:`file <file>` module.




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
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Location where temporary file or directory should be created. If path is not specified default system temporary directory will be used.</div>        </td></tr>
                <tr><td>prefix<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ansible.</td>
        <td></td>
        <td><div>Prefix of file/directory name created by module.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>file</td>
        <td><ul><li>file</li><li>directory</li></ul></td>
        <td><div>Whether to create file or directory.</div>        </td></tr>
                <tr><td>suffix<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Suffix of file/directory name created by module.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: create temporary build directory
      tempfile:
        state: directory
        suffix: build
    
    - name: create temporary file
      tempfile:
        state: file
        suffix: temp

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
        <td> path </td>
        <td> Path to created file or directory </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> /tmp/ansible.bMlvdk </td>
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
