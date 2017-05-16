.. _rds_param_group:


rds_param_group - manage RDS parameter groups
+++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.5

Creates, modifies, and deletes RDS parameter groups. This module has a dependency on python-boto >= 2.5.

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
    <td>aws_access_key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>AWS access key. If not set then the value of the AWS_ACCESS_KEY environment variable is used.</td>
    </tr>
            <tr>
    <td>aws_secret_key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>AWS secret key. If not set then the value of the AWS_SECRET_KEY environment variable is used.</td>
    </tr>
            <tr>
    <td>description</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Database parameter group description. Only set when a new group is added.</td>
    </tr>
            <tr>
    <td>engine</td>
    <td>no</td>
    <td></td>
        <td><ul><li>mysql5.1</li><li>mysql5.5</li><li>mysql5.6</li><li>oracle-ee-11.2</li><li>oracle-se-11.2</li><li>oracle-se1-11.2</li><li>postgres9.3</li><li>postgres9.4</li><li>sqlserver-ee-10.5</li><li>sqlserver-ee-11.0</li><li>sqlserver-ex-10.5</li><li>sqlserver-ex-11.0</li><li>sqlserver-se-10.5</li><li>sqlserver-se-11.0</li><li>sqlserver-web-10.5</li><li>sqlserver-web-11.0</li></ul></td>
        <td>The type of database for this group. Required for state=present.</td>
    </tr>
            <tr>
    <td>immediate</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Whether to apply the changes immediately, or after the next reboot of any associated instances.</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Database parameter group identifier.</td>
    </tr>
            <tr>
    <td>params</td>
    <td>no</td>
    <td></td>
        <td><ul><li>mysql5.1</li><li>mysql5.5</li><li>mysql5.6</li><li>oracle-ee-11.2</li><li>oracle-se-11.2</li><li>oracle-se1-11.2</li><li>postgres9.3</li><li>postgres9.4</li><li>sqlserver-ee-10.5</li><li>sqlserver-ee-11.0</li><li>sqlserver-ex-10.5</li><li>sqlserver-ex-11.0</li><li>sqlserver-se-10.5</li><li>sqlserver-se-11.0</li><li>sqlserver-web-10.5</li><li>sqlserver-web-11.0</li></ul></td>
        <td>Map of parameter names and values. Numeric values may be represented as K for kilo (1024), M for mega (1024^2), G for giga (1024^3), or T for tera (1024^4), and these values will be expanded into the appropriate number before being set in the parameter group.</td>
    </tr>
            <tr>
    <td>region</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The AWS region to use. If not specified then the value of the EC2_REGION environment variable, if any, is used.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>yes</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Specifies whether the group should be present or absent.</td>
    </tr>
        </table>


.. note:: Requires boto


Examples
--------

.. raw:: html

    <br/>


::

    # Add or change a parameter group, in this case setting auto_increment_increment to 42 * 1024
    - rds_param_group:
          state: present
          name: norwegian_blue
          description: 'My Fancy Ex Parrot Group'
          engine: 'mysql5.6'
          params:
              auto_increment_increment: "42K"
    
    # Remove a parameter group
    - rds_param_group:
          state: absent
          name: norwegian_blue



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

