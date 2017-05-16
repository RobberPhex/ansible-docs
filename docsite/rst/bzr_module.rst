.. _bzr:


bzr - Deploy software (or files) from bzr branches
++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage *bzr* branches to deploy files or software.




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
    <td>dest<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Absolute path of where the branch should be cloned to.</div></td></tr>
            <tr>
    <td>executable<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to bzr executable to use. If not supplied, the normal mechanism for resolving binary paths will be used.</div></td></tr>
            <tr>
    <td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>yes</code>, any modified files in the working tree will be discarded.  Before 1.9 the default value was "yes".</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>SSH or HTTP protocol address of the parent branch.</div></br>
        <div style="font-size: small;">aliases: parent<div></td></tr>
            <tr>
    <td>version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>head</td>
        <td><ul></ul></td>
        <td><div>What version of the branch to clone.  This can be the bzr revno or revid.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example bzr checkout from Ansible Playbooks
    - bzr: name=bzr+ssh://foosball.example.org/path/to/branch dest=/srv/checkout version=22




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

