.. _tower_role:


tower_role - create, update, or destroy Ansible Tower role.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, update, or destroy Ansible Tower roles. See https://www.ansible.com/tower for an overview.


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
                <tr><td>credential<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Credential the role acts on.</div>        </td></tr>
                <tr><td>inventory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Inventory the role acts on.</div>        </td></tr>
                <tr><td>job_template<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The job_template the role acts on.</div>        </td></tr>
                <tr><td>organization<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Organiation the role acts on.</div>        </td></tr>
                <tr><td>project<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Project the role acts on.</div>        </td></tr>
                <tr><td>role<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>admin</li><li>read</li><li>member</li><li>execute</li><li>adhoc</li><li>update</li><li>use</li><li>auditor</li></ul></td>
        <td><div>The role type to grant/revoke.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Desired state of the resource.</div>        </td></tr>
                <tr><td>target_team<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Team that the role acts on.</div>        </td></tr>
                <tr><td>team<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Team that receives the permissions specified by the role.</div>        </td></tr>
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
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>User that receives the permissions specified by the role.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Add jdoe to the member role of My Team
      tower_role:
        user: jdoe
        target_team: "My Team"
        role: member
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
