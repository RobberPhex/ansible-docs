.. _yum:


yum - Manages packages with the *yum* package manager
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Installs, upgrade, removes, and lists packages and groups with the *yum* package manager.

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
    <td>conf_file</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The remote yum configuration file to use for the transaction. (added in Ansible 0.6)</td>
    </tr>
            <tr>
    <td>disable_gpg_check</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Whether to disable the GPG checking of signatures of packages being installed. Has an effect only if state is <em>present</em> or <em>latest</em>. (added in Ansible 1.2)</td>
    </tr>
            <tr>
    <td>disablerepo</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><em>Repoid</em> of repositories to disable for the install/update operation. These repos will not persist beyond the transaction. When specifying multiple repos, separate them with a ",". (added in Ansible 0.9)</td>
    </tr>
            <tr>
    <td>enablerepo</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><em>Repoid</em> of repositories to enable for the install/update operation. These repos will not persist beyond the transaction. When specifying multiple repos, separate them with a ",". (added in Ansible 0.9)</td>
    </tr>
            <tr>
    <td>list</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Various (non-idempotent) commands for usage with <code>/usr/bin/ansible</code> and <em>not</em> playbooks. See examples.</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Package name, or package specifier with version, like <code>name-1.0</code>. When using state=latest, this can be '*' which means run: yum -y update. You can also pass a url or a local path to a rpm file.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>latest</li><li>absent</li></ul></td>
        <td>Whether to install (<code>present</code>, <code>latest</code>), or remove (<code>absent</code>) a package.</td>
    </tr>
        </table>


.. note:: Requires yum


.. note:: Requires rpm


Examples
--------

.. raw:: html

    <br/>


::

    - name: install the latest version of Apache
      yum: name=httpd state=latest
    
    - name: remove the Apache package
      yum: name=httpd state=absent
    
    - name: install the latest version of Apache from the testing repo
      yum: name=httpd enablerepo=testing state=present
    
    - name: upgrade all packages
      yum: name=* state=latest
    
    - name: install the nginx rpm from a remote repo
      yum: name=http://nginx.org/packages/centos/6/noarch/RPMS/nginx-release-centos-6-0.el6.ngx.noarch.rpm state=present
    
    - name: install nginx rpm from a local file
      yum: name=/usr/local/src/nginx-release-centos-6-0.el6.ngx.noarch.rpm state=present
    
    - name: install the 'Development tools' package group
      yum: name="@Development tools" state=present



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

