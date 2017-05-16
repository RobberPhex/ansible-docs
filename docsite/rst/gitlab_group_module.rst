.. _gitlab_group:


gitlab_group - Creates/updates/deletes Gitlab Groups
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

When the group does not exists in Gitlab, it will be created.
When the group does exists and state=absent, the group will be deleted.


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
        <td><div>Name of the group you want to create.</div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The path of the group you want to create, this will be server_url/group_path</div><div>If not supplied, the group_name will be used.</div></td></tr>
            <tr>
    <td>server_url<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Url of Gitlab server, with protocol (http or https).</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>create or delete group.</div><div>Possible values are present and absent.</div></td></tr>
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

    - name: "Delete Gitlab Group"
      local_action: gitlab_group
                    server_url="http://gitlab.dj-wasabi.local"
                    validate_certs=false
                    login_token="WnUzDsxjy8230-Dy_k"
                    name=my_first_group
                    state=absent
    
    - name: "Create Gitlab Group"
      local_action: gitlab_group
                    server_url="https://gitlab.dj-wasabi.local"
                    validate_certs=true
                    login_user=dj-wasabi
                    login_password="MySecretPassword"
                    name=my_first_group
                    path=my_first_group
                    state=present




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

