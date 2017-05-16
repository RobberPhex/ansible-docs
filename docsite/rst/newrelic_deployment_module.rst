.. _newrelic_deployment:


newrelic_deployment - Notify newrelic about app deployments
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.2

Notify newrelic about app deployments (see http://newrelic.github.io/newrelic_api/NewRelicApi/Deployment.html)

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
    <td>app_name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>(one of app_name or application_id are required) The value of app_name in the newrelic.yml file used by the application</td>
    </tr>
            <tr>
    <td>application_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>(one of app_name or application_id are required) The application id, found in the URL when viewing the application in RPM</td>
    </tr>
            <tr>
    <td>appname</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of the application</td>
    </tr>
            <tr>
    <td>changelog</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A list of changes for this deployment</td>
    </tr>
            <tr>
    <td>description</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Text annotation for the deployment - notes for you</td>
    </tr>
            <tr>
    <td>environment</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The environment for this deployment</td>
    </tr>
            <tr>
    <td>revision</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A revision number (e.g., git commit SHA)</td>
    </tr>
            <tr>
    <td>token</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>API token.</td>
    </tr>
            <tr>
    <td>user</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The name of the user/process that triggered this deployment</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates. (added in Ansible 1.5.1)</td>
    </tr>
        </table>


.. note:: Requires urllib


.. note:: Requires urllib2


Examples
--------

.. raw:: html

    <br/>


::

    - newrelic_deployment: token=AAAAAA
                           app_name=myapp
                           user='ansible deployment'
                           revision=1.0



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

