.. _yum:


yum - Manages packages with the *yum* package manager
+++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Installs, upgrade, removes, and lists packages and groups with the *yum* package manager.


Requirements
------------

  * yum


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
        <td><div>The remote yum configuration file to use for the transaction.</div></td></tr>
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
    <td>exclude<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Package name(s) to exclude when state=present, or latest</div></td></tr>
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
        <td><div>Package name, or package specifier with version, like <code>name-1.0</code>. When using state=latest, this can be '*' which means run: yum -y update. You can also pass a url or a local path to a rpm file.  To operate on several packages this can accept a comma separated list of packages or (as of 2.0) a list of packages.</div></br>
        <div style="font-size: small;">aliases: pkg<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>installed</li><li>latest</li><li>absent</li><li>removed</li></ul></td>
        <td><div>Whether to install (<code>present</code> or <code>installed</code>, <code>latest</code>), or remove (<code>absent</code> or <code>removed</code>) a package.</div></td></tr>
            <tr>
    <td>update_cache<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Force updating the cache. Has an effect only if state is <em>present</em> or <em>latest</em>.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: install the latest version of Apache
      yum: name=httpd state=latest
    
    - name: remove the Apache package
      yum: name=httpd state=absent
    
    - name: install the latest version of Apache from the testing repo
      yum: name=httpd enablerepo=testing state=present
    
    - name: install one specific version of Apache
      yum: name=httpd-2.2.29-1.4.amzn1 state=present
    
    - name: upgrade all packages
      yum: name=* state=latest
    
    - name: install the nginx rpm from a remote repo
      yum: name=http://nginx.org/packages/centos/6/noarch/RPMS/nginx-release-centos-6-0.el6.ngx.noarch.rpm state=present
    
    - name: install nginx rpm from a local file
      yum: name=/usr/local/src/nginx-release-centos-6-0.el6.ngx.noarch.rpm state=present
    
    - name: install the 'Development tools' package group
      yum: name="@Development tools" state=present
    
    - name: install the 'Gnome desktop' environment group
      yum: name="@^gnome-desktop-environment" state=present


Notes
-----

.. note:: When used with a loop of package names in a playbook, ansible optimizes the call to the yum module.  Instead of calling the module with a single package each time through the loop, ansible calls the module once with all of the package names from the loop.
.. note:: In versions prior to 1.9.2 this module installed and removed each package given to the yum module separately. This caused problems when packages specified by filename or url had to be installed or removed together. In 1.9.2 this was fixed so that packages are installed in one yum transaction. However, if one of the packages adds a new yum repository that the other packages come from (such as epel-release) then that package needs to be installed in a separate task. This mimics yum's command line behaviour.
.. note:: Yum itself has two types of groups.  "Package groups" are specified in the rpm itself while "environment groups" are specified in a separate file (usually by the distribution).  Unfortunately, this division becomes apparent to ansible users because ansible needs to operate on the group of packages in a single transaction and yum requires groups to be specified in different ways when used in that way.  Package groups are specified as "@development-tools" and environment groups are "@^gnome-desktop-environment". Use the "yum group list" command to see which category of group the group you want to install falls into.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

