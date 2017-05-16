.. _dnf:


dnf - Manages packages with the *dnf* package manager
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.9


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Installs, upgrade, removes, and lists packages and groups with the *dnf* package manager.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * python-dnf


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
    <td>conf_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The remote dnf configuration file to use for the transaction.</div></td></tr>
            <tr>
    <td>disable_gpg_check<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether to disable the GPG checking of signatures of packages being installed. Has an effect only if state is <em>present</em> or <em>latest</em>.</div></td></tr>
            <tr>
    <td>disablerepo<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div><em>Repoid</em> of repositories to disable for the install/update operation. These repos will not persist beyond the transaction. When specifying multiple repos, separate them with a ",".</div></td></tr>
            <tr>
    <td>enablerepo<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div><em>Repoid</em> of repositories to enable for the install/update operation. These repos will not persist beyond the transaction. When specifying multiple repos, separate them with a ",".</div></td></tr>
            <tr>
    <td>list<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Various (non-idempotent) commands for usage with <code>/usr/bin/ansible</code> and <em>not</em> playbooks. See examples.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Package name, or package specifier with version, like <code>name-1.0</code>. When using state=latest, this can be '*' which means run: dnf -y update. You can also pass a url or a local path to a rpm file.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>latest</li><li>absent</li></ul></td>
        <td><div>Whether to install (<code>present</code>, <code>latest</code>), or remove (<code>absent</code>) a package.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: install the latest version of Apache
      dnf: name=httpd state=latest
    
    - name: remove the Apache package
      dnf: name=httpd state=absent
    
    - name: install the latest version of Apache from the testing repo
      dnf: name=httpd enablerepo=testing state=present
    
    - name: upgrade all packages
      dnf: name=* state=latest
    
    - name: install the nginx rpm from a remote repo
      dnf: name=http://nginx.org/packages/centos/6/noarch/RPMS/nginx-release-centos-6-0.el6.ngx.noarch.rpm state=present
    
    - name: install nginx rpm from a local file
      dnf: name=/usr/local/src/nginx-release-centos-6-0.el6.ngx.noarch.rpm state=present
    
    - name: install the 'Development tools' package group
      dnf: name="@Development tools" state=present
    




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

