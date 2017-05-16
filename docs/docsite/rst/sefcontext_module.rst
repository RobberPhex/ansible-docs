.. _sefcontext:


sefcontext - Manages SELinux file context mapping definitions
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages SELinux file context mapping definitions
* Similar to the ``semanage fcontext`` command


Requirements (on host that executes module)
-------------------------------------------

  * libselinux-python
  * policycoreutils-python


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
                <tr><td>ftype<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>a</td>
        <td></td>
        <td><div>File type.</div>        </td></tr>
                <tr><td>reload<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Reload SELinux policy after commit.</div>        </td></tr>
                <tr><td>selevel<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>SELinux range for the specified target.</div></br>
    <div style="font-size: small;">aliases: serange<div>        </td></tr>
                <tr><td>setype<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>SELinux type for the specified target.</div>        </td></tr>
                <tr><td>seuser<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>SELinux user for the specified target.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Desired boolean value.</div>        </td></tr>
                <tr><td>target<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Target path (expression).</div></br>
    <div style="font-size: small;">aliases: path<div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Allow apache to modify files in /srv/git_repos
    - sefcontext:
        target: '/srv/git_repos(/.*)?'
        setype: httpd_git_rw_content_t
        state: present


Notes
-----

.. note::
    - The changes are persistent across reboots



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
