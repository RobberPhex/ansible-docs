.. _gitlab_user:


gitlab_user - Creates/updates/deletes Gitlab Users
++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

When the user does not exists in Gitlab, it will be created.
When the user does exists and state=absent, the user will be deleted.
When changes are made to user, the user will be updated.


Requirements (on host that executes module)
-------------------------------------------

  * pyapi-gitlab python module


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
    <td>access_level<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The access level to the group. One of the following can be used.</div><div>guest</div><div>reporter</div><div>developer</div><div>master</div><div>owner</div></td></tr>
            <tr>
    <td>email<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The email that belongs to the user.</div></td></tr>
            <tr>
    <td>group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Add user as an member to this group.</div></td></tr>
            <tr>
    <td>login_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Gitlab password for login_user</div></td></tr>
            <tr>
    <td>login_token<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Gitlab token for logging in.</div></td></tr>
            <tr>
    <td>login_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Gitlab user name.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the user you want to create</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password of the user.</div></td></tr>
            <tr>
    <td>server_url<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Url of Gitlab server, with protocol (http or https).</div></td></tr>
            <tr>
    <td>sshkey_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The ssh key itself.</div></td></tr>
            <tr>
    <td>sshkey_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the sshkey</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>create or delete group.</div><div>Possible values are present and absent.</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The username of the user.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>When using https if SSL certificate needs to be verified.</div></br>
        <div style="font-size: small;">aliases: verify_ssl<div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: "Delete Gitlab User"
      local_action: gitlab_user
                    server_url="http://gitlab.dj-wasabi.local"
                    validate_certs=false
                    login_token="WnUzDsxjy8230-Dy_k"
                    username=myusername
                    state=absent
    
    - name: "Create Gitlab User"
      local_action: gitlab_user
                    server_url="https://gitlab.dj-wasabi.local"
                    validate_certs=true
                    login_user=dj-wasabi
                    login_password="MySecretPassword"
                    name=My Name
                    username=myusername
                    password=mysecretpassword
                    email=me@home.com
                    sshkey_name=MySSH
                    sshkey_file=ssh-rsa AAAAB3NzaC1yc...
                    state=present




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

