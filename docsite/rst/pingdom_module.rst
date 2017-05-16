.. _pingdom:


pingdom - Pause/unpause Pingdom alerts
++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.2

This module will let you pause/unpause Pingdom alerts

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
    <td>checkid</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Pingdom ID of the check.</td>
    </tr>
            <tr>
    <td>key</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Pingdom API key.</td>
    </tr>
            <tr>
    <td>passwd</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Pingdom user password.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>running</li><li>paused</li></ul></td>
        <td>Define whether or not the check should be running or paused.</td>
    </tr>
            <tr>
    <td>uid</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Pingdom user ID.</td>
    </tr>
        </table>


.. note:: Requires This pingdom python library: https://github.com/mbabineau/pingdom-python


Examples
--------

.. raw:: html

    <br/>


::

    # Pause the check with the ID of 12345.
    - pingdom: uid=example@example.com
               passwd=password123
               key=apipassword123
               checkid=12345
               state=paused
    
    # Unpause the check with the ID of 12345.
    - pingdom: uid=example@example.com
               passwd=password123
               key=apipassword123
               checkid=12345
               state=running

.. note:: This module does not yet have support to add/remove checks.


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

