.. _dnf:


dnf - Manages packages with the *dnf* package manager
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.9

Installs, upgrade, removes, and lists packages and groups with the *dnf* package manager.

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
        <td>The remote dnf configuration file to use for the transaction.</td>
    </tr>
            <tr>
    <td>disable_gpg_check</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Whether to disable the GPG checking of signatures of packages being installed. Has an effect only if state is <em>present</em> or <em>latest</em>.</td>
    </tr>
            <tr>
    <td>disablerepo</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><em>Repoid</em> of repositories to disable for the install/update operation. These repos will not persist beyond the transaction. When specifying multiple repos, separate them with a ",".</td>
    </tr>
            <tr>
    <td>enablerepo</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><em>Repoid</em> of repositories to enable for the install/update operation. These repos will not persist beyond the transaction. When specifying multiple repos, separate them with a ",".</td>
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
        <td>Package name, or package specifier with version, like <code>name-1.0</code>. When using state=latest, this can be '*' which means run: dnf -y update. You can also pass a url or a local path to a rpm file.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>latest</li><li>absent</li></ul></td>
        <td>Whether to install (<code>present</code>, <code>latest</code>), or remove (<code>absent</code>) a package.</td>
    </tr>
        </table>


.. note:: Requires dnf


.. note:: Requires yum-utils (for repoquery)


Examples
--------

.. raw:: html

    <br/>


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

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

