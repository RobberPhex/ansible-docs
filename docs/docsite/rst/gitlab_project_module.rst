.. _gitlab_project:


gitlab_project - Creates/updates/deletes Gitlab Projects
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* When the project does not exists in Gitlab, it will be created.
* When the project does exists and state=absent, the project will be deleted.
* When changes are made to the project, the project will be updated.


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
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>An description for the project.</div>        </td></tr>
                <tr><td>group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The name of the group of which this projects belongs to.</div><div>When not provided, project will belong to user which is configured in 'login_user' or 'login_token'</div><div>When provided with username, project will be created for this user. 'login_user' or 'login_token' needs admin rights.</div>        </td></tr>
                <tr><td>import_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Git repository which will me imported into gitlab.</div><div>Gitlab server needs read access to this git repository.</div>        </td></tr>
                <tr><td>issues_enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Whether you want to create issues or not.</div><div>Possible values are true and false.</div>        </td></tr>
                <tr><td>login_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Gitlab password for login_user</div>        </td></tr>
                <tr><td>login_token<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Gitlab token for logging in.</div>        </td></tr>
                <tr><td>login_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Gitlab user name.</div>        </td></tr>
                <tr><td>merge_requests_enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>If merge requests can be made or not.</div><div>Possible values are true and false.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the project</div>        </td></tr>
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The path of the project you want to create, this will be server_url/&lt;group&gt;/path</div><div>If not supplied, name will be used.</div>        </td></tr>
                <tr><td>public<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If the project is public available or not.</div><div>Setting this to true is same as setting visibility_level to 20.</div><div>Possible values are true and false.</div>        </td></tr>
                <tr><td>server_url<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Url of Gitlab server, with protocol (http or https).</div>        </td></tr>
                <tr><td>snippets_enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>If creating snippets should be available or not.</div><div>Possible values are true and false.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>create or delete project.</div><div>Possible values are present and absent.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>When using https if SSL certificate needs to be verified.</div></br>
    <div style="font-size: small;">aliases: verify_ssl<div>        </td></tr>
                <tr><td>visibility_level<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Private. visibility_level is 0. Project access must be granted explicitly for each user.</div><div>Internal. visibility_level is 10. The project can be cloned by any logged in user.</div><div>Public. visibility_level is 20. The project can be cloned without any authentication.</div><div>Possible values are 0, 10 and 20.</div>        </td></tr>
                <tr><td>wiki_enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>If an wiki for this project should be available or not.</div><div>Possible values are true and false.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Delete Gitlab Project
      gitlab_project:
        server_url: http://gitlab.example.com
        validate_certs: False
        login_token: WnUzDsxjy8230-Dy_k
        name: my_first_project
        state: absent
      delegate_to: localhost
    
    - name: Create Gitlab Project in group Ansible
      gitlab_project:
        server_url: https://gitlab.example.com
        validate_certs: True
        login_user: dj-wasabi
        login_password: MySecretPassword
        name: my_first_project
        group: ansible
        issues_enabled: False
        wiki_enabled: True
        snippets_enabled: True
        import_url: http://git.example.com/example/lab.git
        state: present
      delegate_to: localhost





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
