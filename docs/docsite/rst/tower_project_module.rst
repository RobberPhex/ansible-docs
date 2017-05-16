.. _tower_project:


tower_project - create, update, or destroy Ansible Tower projects
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, update, or destroy Ansible Tower projects. See https://www.ansible.com/tower for an overview.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * ansible-tower-cli >= 3.0.3


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
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Description to use for the project.</div>        </td></tr>
                <tr><td>local_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The server playbook directory for manual projects.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name to use for the project.</div>        </td></tr>
                <tr><td>organization<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Primary key of organization for project.</div>        </td></tr>
                <tr><td>scm_branch<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The branch to use for the scm resource.</div>        </td></tr>
                <tr><td>scm_clean<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Remove local modifications before updating.</div>        </td></tr>
                <tr><td>scm_credential<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the credential to use with this scm resource.</div>        </td></tr>
                <tr><td>scm_delete_on_update<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Remove the repository completely before updating.</div>        </td></tr>
                <tr><td>scm_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>manual</td>
        <td><ul><li>manual</li><li>git</li><li>hg</li><li>svn</li></ul></td>
        <td><div>Type of scm resource.</div>        </td></tr>
                <tr><td>scm_update_on_launch<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Before an update to the local repository before launching a job with this project.</div>        </td></tr>
                <tr><td>scm_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>URL of scm resource.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Desired state of the resource.</div>        </td></tr>
                <tr><td>tower_config_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Path to the Tower config file. See notes.</div>        </td></tr>
                <tr><td>tower_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>URL to your Tower instance.</div>        </td></tr>
                <tr><td>tower_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password for your Tower instance.</div>        </td></tr>
                <tr><td>tower_username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Username for your Tower instance.</div>        </td></tr>
                <tr><td>tower_verify_ssl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Dis/allow insecure connections to Tower. If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Add tower project
      tower_project:
        name: "Foo"
        description: "Foo bar project"
        organization: "test"
        state: present
        tower_config_file: "~/tower_cli.cfg"


Notes
-----

.. note::
    - If no *config_file* is provided we will attempt to use the tower-cli library defaults to find your Tower host information.
    - *config_file* should contain Tower configuration in the following format host=hostname username=username password=password



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
