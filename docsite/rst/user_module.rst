.. _user:


user - Manage user accounts
+++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Manage user accounts and user attributes.

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
    <td>append</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>yes</code>, will only add groups, not set them to just the list in <em>groups</em>.</td>
    </tr>
            <tr>
    <td>comment</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Optionally sets the description (aka <em>GECOS</em>) of user account.</td>
    </tr>
            <tr>
    <td>createhome</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Unless set to <code>no</code>, a home directory will be made for the user when the account is created or if the home directory does not exist.</td>
    </tr>
            <tr>
    <td>expires</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>An expiry time for the user in epoch, it will be ignored on platforms that do not support this. Currently supported on Linux and FreeBSD. (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>force</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>When used with <code>state=absent</code>, behavior is as with <code>userdel --force</code>.</td>
    </tr>
            <tr>
    <td>generate_ssh_key</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Whether to generate a SSH key for the user in question. This will <b>not</b> overwrite an existing SSH key. (added in Ansible 0.9)</td>
    </tr>
            <tr>
    <td>group</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Optionally sets the user's primary group (takes a group name).</td>
    </tr>
            <tr>
    <td>groups</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Puts the user in this comma-delimited list of groups. When set to the empty string ('groups='), the user is removed from all groups except the primary group.</td>
    </tr>
            <tr>
    <td>home</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Optionally set the user's home directory.</td>
    </tr>
            <tr>
    <td>login_class</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Optionally sets the user's login class for FreeBSD, OpenBSD and NetBSD systems.</td>
    </tr>
            <tr>
    <td>move_home</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If set to <code>yes</code> when used with <code>home=</code>, attempt to move the user's home directory to the specified directory if it isn't there already.</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of the user to create, remove or modify.</td>
    </tr>
            <tr>
    <td>non_unique</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Optionally when used with the -u option, this option allows to change the user ID to a non-unique value. (added in Ansible 1.1)</td>
    </tr>
            <tr>
    <td>password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Optionally set the user's password to this crypted value.  See the user example in the github examples directory for what this looks like in a playbook. See <a href='http://docs.ansible.com/ansible/faq.html#how-do-i-generate-crypted-passwords-for-the-user-module'>http://docs.ansible.com/ansible/faq.html#how-do-i-generate-crypted-passwords-for-the-user-module</a> for details on various ways to generate these password values. Note on Darwin system, this value has to be cleartext. Beware of security issues.</td>
    </tr>
            <tr>
    <td>remove</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>When used with <code>state=absent</code>, behavior is as with <code>userdel --remove</code>.</td>
    </tr>
            <tr>
    <td>shell</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Optionally set the user's shell.</td>
    </tr>
            <tr>
    <td>skeleton</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Optionally set a home skeleton directory. Requires createhome option! (added in Ansible 2.0)</td>
    </tr>
            <tr>
    <td>ssh_key_bits</td>
    <td>no</td>
    <td>2048</td>
        <td><ul></ul></td>
        <td>Optionally specify number of bits in SSH key to create. (added in Ansible 0.9)</td>
    </tr>
            <tr>
    <td>ssh_key_comment</td>
    <td>no</td>
    <td>ansible-generated on $HOSTNAME</td>
        <td><ul></ul></td>
        <td>Optionally define the comment for the SSH key. (added in Ansible 0.9)</td>
    </tr>
            <tr>
    <td>ssh_key_file</td>
    <td>no</td>
    <td>.ssh/id_rsa</td>
        <td><ul></ul></td>
        <td>Optionally specify the SSH key filename. If this is a relative filename then it will be relative to the user's home directory. (added in Ansible 0.9)</td>
    </tr>
            <tr>
    <td>ssh_key_passphrase</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Set a passphrase for the SSH key.  If no passphrase is provided, the SSH key will default to having no passphrase. (added in Ansible 0.9)</td>
    </tr>
            <tr>
    <td>ssh_key_type</td>
    <td>no</td>
    <td>rsa</td>
        <td><ul></ul></td>
        <td>Optionally specify the type of SSH key to generate. Available SSH key types will depend on implementation present on target host. (added in Ansible 0.9)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Whether the account should exist or not, taking action if the state is different from what is stated.</td>
    </tr>
            <tr>
    <td>system</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>When creating an account, setting this to <code>yes</code> makes the user a system account.  This setting cannot be changed on existing users.</td>
    </tr>
            <tr>
    <td>uid</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Optionally sets the <em>UID</em> of the user.</td>
    </tr>
            <tr>
    <td>update_password</td>
    <td>no</td>
    <td>always</td>
        <td><ul><li>always</li><li>on_create</li></ul></td>
        <td><code>always</code> will update passwords if they differ.  <code>on_create</code> will only set the password for newly created users. (added in Ansible 1.3)</td>
    </tr>
        </table>


.. note:: Requires useradd


.. note:: Requires userdel


.. note:: Requires usermod


Examples
--------

.. raw:: html

    <br/>


::

    # Add the user 'johnd' with a specific uid and a primary group of 'admin'
    - user: name=johnd comment="John Doe" uid=1040 group=admin
    
    # Add the user 'james' with a bash shell, appending the group 'admins' and 'developers' to the user's groups
    - user: name=james shell=/bin/bash groups=admins,developers append=yes
    
    # Remove the user 'johnd'
    - user: name=johnd state=absent remove=yes
    
    # Create a 2048-bit SSH key for user jsmith in ~jsmith/.ssh/id_rsa
    - user: name=jsmith generate_ssh_key=yes ssh_key_bits=2048 ssh_key_file=.ssh/id_rsa
    
    # added a consultant whose account you want to expire
    - user: name=james18 shell=/bin/zsh groups=developers expires=1422403387



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

