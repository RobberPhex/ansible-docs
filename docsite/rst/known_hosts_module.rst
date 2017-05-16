.. _known_hosts:


known_hosts - Add or remove a host from the ``known_hosts`` file
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.9


.. contents::
   :local:
   :depth: 1


Synopsis
--------

The :ref:`known_hosts <known_hosts>` module lets you add or remove a host keys from the ``known_hosts`` file.
Starting at Ansible 2.2, multiple entries per host are allowed, but only one for each key type supported by ssh. This is useful if you're going to want to use the :ref:`git <git>` module over ssh, for example.
If you have a very large number of host keys to manage, you will find the :ref:`template <template>` module more useful.




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
    <td>key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The SSH public host key, as a string (required if state=present, optional when state=absent, in which case all keys for the host are removed). The key must be in the right format for ssh (see sshd(1), section "SSH_KNOWN_HOSTS FILE FORMAT")</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The host to add or remove (must match a host specified in key)</div></br>
        <div style="font-size: small;">aliases: host<div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>(homedir)+/.ssh/known_hosts</td>
        <td><ul></ul></td>
        <td><div>The known_hosts file to edit</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div><em>present</em> to add the host key, <em>absent</em> to remove it.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example using with_file to set the system known_hosts file
    - name: tell the host about our servers it might want to ssh to
      known_hosts: path='/etc/ssh/ssh_known_hosts'
                   name='foo.com.invalid'
                   key="{{ lookup('file', 'pubkeys/foo.com.invalid') }}"




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

