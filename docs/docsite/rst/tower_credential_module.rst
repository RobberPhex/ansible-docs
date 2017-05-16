.. _tower_credential:


tower_credential - create, update, or destroy Ansible Tower credential.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, update, or destroy Ansible Tower credentials. See https://www.ansible.com/tower for an overview.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * ansible-tower-cli >= 3.0.2


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
                <tr><td>authorize<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Should use authroize for net type.</div>        </td></tr>
                <tr><td>authorize_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password for net credentials that require authroize.</div>        </td></tr>
                <tr><td>become_method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul><li>None</li><li>sudo</li><li>su</li><li>pbrun</li><li>pfexec</li></ul></td>
        <td><div>Become method to Use for privledge escalation.</div>        </td></tr>
                <tr><td>become_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Become password. Use ASK for prompting.</div>        </td></tr>
                <tr><td>become_username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Become username. Use ASK for prompting.</div>        </td></tr>
                <tr><td>client<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Client or application ID for azure_rm type.</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The description to use for the credential.</div>        </td></tr>
                <tr><td>domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Domain for openstack type.</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Host for this credential.</div>        </td></tr>
                <tr><td>kind<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>ssh</li><li>net</li><li>scm</li><li>aws</li><li>rax</li><li>vmware</li><li>satellite6</li><li>cloudforms</li><li>gce</li><li>azure</li><li>azure_rm</li><li>openstack</li></ul></td>
        <td><div>Type of credential being added.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name to use for the credential.</div>        </td></tr>
                <tr><td>organization<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Organization that should own the credential.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password for this credential. Use ASK for prompting. secret_key for AWS. api_key for RAX.</div>        </td></tr>
                <tr><td>project<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Project that should for this credential.</div>        </td></tr>
                <tr><td>secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Secret token for azure_rm type.</div>        </td></tr>
                <tr><td>ssh_key_data<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Path to SSH private key.</div>        </td></tr>
                <tr><td>ssh_key_unlock<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Unlock password for ssh_key. Use ASK for prompting.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Desired state of the resource.</div>        </td></tr>
                <tr><td>subscription<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Subscription ID for azure_rm type.</div>        </td></tr>
                <tr><td>team<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Team that should own this credential.</div>        </td></tr>
                <tr><td>tenant<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Tenant ID for azure_rm type.</div>        </td></tr>
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
        <td><div>User that should own this credential.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Username for this credential. access_key for AWS.</div>        </td></tr>
                <tr><td>vault_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Valut password. Use ASK for prompting.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Add tower credential
      tower_credential:
        name: Team Name
        description: Team Description
        organization: test-org
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
