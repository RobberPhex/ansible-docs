.. _user:


user - Manage user accounts
+++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage user accounts and user attributes.


Requirements (on host that executes module)
-------------------------------------------

  * useradd
  * userdel
  * usermod


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
    <td>append<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>yes</code>, will only add groups, not set them to just the list in <em>groups</em>.</div></td></tr>
            <tr>
    <td>comment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Optionally sets the description (aka <em>GECOS</em>) of user account.</div></td></tr>
            <tr>
    <td>createhome<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Unless set to <code>no</code>, a home directory will be made for the user when the account is created or if the home directory does not exist.</div></td></tr>
            <tr>
    <td>expires<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>An expiry time for the user in epoch, it will be ignored on platforms that do not support this. Currently supported on Linux and FreeBSD.</div></td></tr>
            <tr>
    <td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When used with <code>state=absent</code>, behavior is as with <code>userdel --force</code>.</div></td></tr>
            <tr>
    <td>generate_ssh_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether to generate a SSH key for the user in question. This will <b>not</b> overwrite an existing SSH key.</div></td></tr>
            <tr>
    <td>group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Optionally sets the user's primary group (takes a group name).</div></td></tr>
            <tr>
    <td>groups<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Puts the user in this comma-delimited list of groups. When set to the empty string ('groups='), the user is removed from all groups except the primary group.</div></td></tr>
            <tr>
    <td>home<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Optionally set the user's home directory.</div></td></tr>
            <tr>
    <td>login_class<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Optionally sets the user's login class for FreeBSD, OpenBSD and NetBSD systems.</div></td></tr>
            <tr>
    <td>move_home<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If set to <code>yes</code> when used with <code>home=</code>, attempt to move the user's home directory to the specified directory if it isn't there already.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the user to create, remove or modify.</div></br>
        <div style="font-size: small;">aliases: user<div></td></tr>
            <tr>
    <td>non_unique<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Optionally when used with the -u option, this option allows to change the user ID to a non-unique value.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Optionally set the user's password to this crypted value.  See the user example in the github examples directory for what this looks like in a playbook. See <a href='http://docs.ansible.com/ansible/faq.html#how-do-i-generate-crypted-passwords-for-the-user-module'>http://docs.ansible.com/ansible/faq.html#how-do-i-generate-crypted-passwords-for-the-user-module</a> for details on various ways to generate these password values. Note on Darwin system, this value has to be cleartext. Beware of security issues.</div></td></tr>
            <tr>
    <td>remove<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When used with <code>state=absent</code>, behavior is as with <code>userdel --remove</code>.</div></td></tr>
            <tr>
    <td>seuser<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Optionally sets the seuser type (user_u) on selinux enabled systems.</div></td></tr>
            <tr>
    <td>shell<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Optionally set the user's shell.</div></td></tr>
            <tr>
    <td>skeleton<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Optionally set a home skeleton directory. Requires createhome option!</div></td></tr>
            <tr>
    <td>ssh_key_bits<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>default set by ssh-keygen</td>
        <td><ul></ul></td>
        <td><div>Optionally specify number of bits in SSH key to create.</div></td></tr>
            <tr>
    <td>ssh_key_comment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ansible-generated on $HOSTNAME</td>
        <td><ul></ul></td>
        <td><div>Optionally define the comment for the SSH key.</div></td></tr>
            <tr>
    <td>ssh_key_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>.ssh/id_rsa</td>
        <td><ul></ul></td>
        <td><div>Optionally specify the SSH key filename. If this is a relative filename then it will be relative to the user's home directory.</div></td></tr>
            <tr>
    <td>ssh_key_passphrase<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Set a passphrase for the SSH key.  If no passphrase is provided, the SSH key will default to having no passphrase.</div></td></tr>
            <tr>
    <td>ssh_key_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>rsa</td>
        <td><ul></ul></td>
        <td><div>Optionally specify the type of SSH key to generate. Available SSH key types will depend on implementation present on target host.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the account should exist or not, taking action if the state is different from what is stated.</div></td></tr>
            <tr>
    <td>system<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When creating an account, setting this to <code>yes</code> makes the user a system account.  This setting cannot be changed on existing users.</div></td></tr>
            <tr>
    <td>uid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Optionally sets the <em>UID</em> of the user.</div></td></tr>
            <tr>
    <td>update_password<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td>always</td>
        <td><ul><li>always</li><li>on_create</li></ul></td>
        <td><div><code>always</code> will update passwords if they differ.  <code>on_create</code> will only set the password for newly created users.</div></td></tr>
        </table>
    </br>



Examples
--------

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

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

