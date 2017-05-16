.. _airbrake_deployment:


airbrake_deployment - Notify airbrake about app deployments
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.2

Notify airbrake about app deployments (see http://help.airbrake.io/kb/api-2/deploy-tracking)

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
    <td>environment</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The airbrake environment name, typically 'production', 'staging', etc.</td>
    </tr>
            <tr>
    <td>repo</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>URL of the project repository</td>
    </tr>
            <tr>
    <td>revision</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A hash, number, tag, or other identifier showing what revision was deployed</td>
    </tr>
            <tr>
    <td>token</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>API token.</td>
    </tr>
            <tr>
    <td>url</td>
    <td>no</td>
    <td>https://airbrake.io/deploys</td>
        <td><ul></ul></td>
        <td>Optional URL to submit the notification to. Use to send notifications to Airbrake-compliant tools like Errbit. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>user</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The username of the person doing the deployment</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>no</code>, SSL certificates for the target url will not be validated. This should only be used on personally controlled sites using self-signed certificates.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    - airbrake_deployment: token=AAAAAA
                           environment='staging'
                           user='ansible'
                           revision=4.2



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

