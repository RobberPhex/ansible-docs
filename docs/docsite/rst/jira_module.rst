.. _jira:


jira - create and modify issues in a JIRA instance
++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create and modify issues in a JIRA instance.




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
                <tr><td>assignee<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Sets the assignee on create or transition operations. Note not all transitions will allow this.</div>        </td></tr>
                <tr><td>comment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The comment text to add.</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The issue description, where appropriate.</div>        </td></tr>
                <tr><td>fields<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>This is a free-form data structure that can contain arbitrary data. This is passed directly to the JIRA REST API (possibly after merging with other required data, as when passed to create). See examples for more information, and the JIRA REST API for the structure required for various fields.</div>        </td></tr>
                <tr><td>inwardissue<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Set issue from which link will be created.</div>        </td></tr>
                <tr><td>issue<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>An existing issue key to operate on.</div>        </td></tr>
                <tr><td>issuetype<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The issue type, for issue creation.</div>        </td></tr>
                <tr><td>linktype<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Set type of link, when action 'link' selected.</div>        </td></tr>
                <tr><td>operation<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>create</li><li>comment</li><li>edit</li><li>fetch</li><li>transition</li></ul></td>
        <td><div>The operation to perform.</div></br>
    <div style="font-size: small;">aliases: command<div>        </td></tr>
                <tr><td>outwardissue<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Set issue to which link will be created.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The password to log-in with.</div>        </td></tr>
                <tr><td>project<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The project for this operation. Required for issue creation.</div></br>
    <div style="font-size: small;">aliases: prj<div>        </td></tr>
                <tr><td>status<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The desired status; only relevant for the transition operation.</div>        </td></tr>
                <tr><td>summary<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The issue summary, where appropriate.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>Set timeout, in seconds, on requests to JIRA API.</div>        </td></tr>
                <tr><td>uri<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Base URI for the JIRA instance.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The username to log-in with.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a new issue and add a comment to it:
    - name: Create an issue
      jira:
        uri: '{{ server }}'
        username: '{{ user }}'
        password: '{{ pass }}'
        project: ANS
        operation: create
        summary: Example Issue
        description: Created using Ansible
        issuetype: Task
      register: issue
    
    - name: Comment on issue
      jira:
        uri: '{{ server }}'
        username: '{{ user }}'
        password: '{{ pass }}'
        issue: '{{ issue.meta.key }}'
        operation: comment
        comment: A comment added by Ansible
    
    # Assign an existing issue using edit
    - name: Assign an issue using free-form fields
      jira:
        uri: '{{ server }}'
        username: '{{ user }}'
        password: '{{ pass }}'
        issue: '{{ issue.meta.key}}'
        operation: edit
        assignee: ssmith
    
    # Create an issue with an existing assignee
    - name: Create an assigned issue
      jira:
        uri: '{{ server }}'
        username: '{{ user }}'
        password: '{{ pass }}'
        project: ANS
        operation: create
        summary: Assigned issue
        description: Created and assigned using Ansible
        issuetype: Task
        assignee: ssmith
    
    # Edit an issue
    - name: Set the labels on an issue using free-form fields
      jira:
        uri: '{{ server }}'
        username: '{{ user }}'
        password: '{{ pass }}'
        issue: '{{ issue.meta.key }}'
        operation: edit
      args:
        fields:
            labels:
              - autocreated
              - ansible
    
    # Retrieve metadata for an issue and use it to create an account
    - name: Get an issue
      jira:
        uri: '{{ server }}'
        username: '{{ user }}'
        password: '{{ pass }}'
        project: ANS
        operation: fetch
        issue: ANS-63
      register: issue
    
    - name: Create a unix account for the reporter
      become: true
      user:
        name: '{{ issue.meta.fields.creator.name }}'
        comment: '{{ issue.meta.fields.creator.displayName }}'
    
    - name: Create link from HSP-1 to MKY-1
      jira:
        uri: '{{ server }}'
        username: '{{ user }}'
        password: '{{ pass }}'
        operation: link
        linktype: Relate
        inwardissue: HSP-1
        outwardissue: MKY-1
    
    # Transition an issue by target status
    - name: Close the issue
      jira:
        uri: '{{ server }}'
        username: '{{ user }}'
        password: '{{ pass }}'
        issue: '{{ issue.meta.key }}'
        operation: transition
        status: Done


Notes
-----

.. note::
    - Currently this only works with basic-auth.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
