.. _rabbitmq_user:


rabbitmq_user - Adds or removes users to RabbitMQ
+++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.1

Add or remove users to RabbitMQ and assign permissions

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
    <td>configure_priv</td>
    <td>no</td>
    <td>^$</td>
        <td><ul></ul></td>
        <td>Regular expression to restrict configure actions on a resource for the specified vhost.By default all actions are restricted.</td>
    </tr>
            <tr>
    <td>force</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Deletes and recreates the user.</td>
    </tr>
            <tr>
    <td>node</td>
    <td>no</td>
    <td>rabbit</td>
        <td><ul></ul></td>
        <td>erlang node name of the rabbit we wish to configure (added in Ansible 1.2)</td>
    </tr>
            <tr>
    <td>password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Password of user to add.To change the password of an existing user, you must also specify <code>force=yes</code>.</td>
    </tr>
            <tr>
    <td>read_priv</td>
    <td>no</td>
    <td>^$</td>
        <td><ul></ul></td>
        <td>Regular expression to restrict configure actions on a resource for the specified vhost.By default all actions are restricted.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Specify if user is to be added or removed</td>
    </tr>
            <tr>
    <td>tags</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>User tags specified as comma delimited</td>
    </tr>
            <tr>
    <td>user</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of user to add</td>
    </tr>
            <tr>
    <td>vhost</td>
    <td>no</td>
    <td>/</td>
        <td><ul></ul></td>
        <td>vhost to apply access privileges.</td>
    </tr>
            <tr>
    <td>write_priv</td>
    <td>no</td>
    <td>^$</td>
        <td><ul></ul></td>
        <td>Regular expression to restrict configure actions on a resource for the specified vhost.By default all actions are restricted.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Add user to server and assign full access control
    - rabbitmq_user: user=joe
                     password=changeme
                     vhost=/
                     configure_priv=.*
                     read_priv=.*
                     write_priv=.*
                     state=present



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

