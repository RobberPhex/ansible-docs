.. _hg:


hg - Manages Mercurial (hg) repositories.
+++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages Mercurial (hg) repositories. Supports SSH, HTTP/S and local address.




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
        <td><div>Absolute path of where the repository should be cloned to.</div></td></tr>
            <tr>
    <td>executable<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to hg executable to use. If not supplied, the normal mechanism for resolving binary paths will be used.</div></td></tr>
            <tr>
    <td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Discards uncommitted changes. Runs <code>hg update -C</code>.  Prior to 1.9, the default was `yes`.</div></td></tr>
            <tr>
    <td>purge<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Deletes untracked files. Runs <code>hg purge</code>.</div></td></tr>
            <tr>
    <td>repo<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The repository address.</div></br>
        <div style="font-size: small;">aliases: name<div></td></tr>
            <tr>
    <td>revision<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Equivalent <code>-r</code> option in hg command which could be the changeset, revision number, branch name or even tag.</div></br>
        <div style="font-size: small;">aliases: version<div></td></tr>
            <tr>
    <td>update<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, do not retrieve new revisions from the origin repository</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Ensure the current working copy is inside the stable branch and deletes untracked files if any.
    - hg: repo=https://bitbucket.org/user/repo1 dest=/home/user/repo1 revision=stable purge=yes


Notes
-----

.. note:: If the task seems to be hanging, first verify remote host is in ``known_hosts``. SSH will prompt user to authorize the first contact with a remote host.  To avoid this prompt, one solution is to add the remote host public key in ``/etc/ssh/ssh_known_hosts`` before calling the hg module, with the following command: ssh-keyscan remote_host.com >> /etc/ssh/ssh_known_hosts.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

