.. _jira:


jira - create and modify issues in a JIRA instance
++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

Create and modify issues in a JIRA instance.

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
    <td>assignee</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Sets the assignee on create or transition operations. Note not all transitions will allow this.</td>
    </tr>
            <tr>
    <td>comment</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The comment text to add.</td>
    </tr>
            <tr>
    <td>description</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The issue description, where appropriate.</td>
    </tr>
            <tr>
    <td>fields</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>This is a free-form data structure that can contain arbitrary data. This is passed directly to the JIRA REST API (possibly after merging with other required data, as when passed to create). See examples for more information, and the JIRA REST API for the structure required for various fields.</td>
    </tr>
            <tr>
    <td>issue</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>An existing issue key to operate on.</td>
    </tr>
            <tr>
    <td>issuetype</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The issue type, for issue creation.</td>
    </tr>
            <tr>
    <td>operation</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>create</li><li>comment</li><li>edit</li><li>fetch</li><li>transition</li></ul></td>
        <td>The operation to perform.</td>
    </tr>
            <tr>
    <td>password</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The password to log-in with.</td>
    </tr>
            <tr>
    <td>project</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The project for this operation. Required for issue creation.</td>
    </tr>
            <tr>
    <td>status</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The desired status; only relevant for the transition operation.</td>
    </tr>
            <tr>
    <td>summary</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The issue summary, where appropriate.</td>
    </tr>
            <tr>
    <td>uri</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Base URI for the JIRA instance</td>
    </tr>
            <tr>
    <td>username</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The username to log-in with.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Create a new issue and add a comment to it:
    - name: Create an issue
      jira: uri={{server}} username={{user}} password={{pass}}
            project=ANS operation=create
            summary="Example Issue" description="Created using Ansible" issuetype=Task
      register: issue
    
    - name: Comment on issue
      jira: uri={{server}} username={{user}} password={{pass}}
            issue={{issue.meta.key}} operation=comment 
            comment="A comment added by Ansible"
    
    # Assign an existing issue using edit
    - name: Assign an issue using free-form fields
      jira: uri={{server}} username={{user}} password={{pass}}
            issue={{issue.meta.key}} operation=edit
            assignee=ssmith
    
    # Create an issue with an existing assignee
    - name: Create an assigned issue
      jira: uri={{server}} username={{user}} password={{pass}}
            project=ANS operation=create
            summary="Assigned issue" description="Created and assigned using Ansible" 
            issuetype=Task assignee=ssmith
    
    # Edit an issue using free-form fields
    - name: Set the labels on an issue using free-form fields
      jira: uri={{server}} username={{user}} password={{pass}}
            issue={{issue.meta.key}} operation=edit 
      args: { fields: {labels: ["autocreated", "ansible"]}}
    
    - name: Set the labels on an issue, YAML version
      jira: uri={{server}} username={{user}} password={{pass}}
            issue={{issue.meta.key}} operation=edit 
      args: 
        fields: 
          labels:
            - "autocreated"
            - "ansible"
            - "yaml"
    
    # Retrieve metadata for an issue and use it to create an account
    - name: Get an issue
      jira: uri={{server}} username={{user}} password={{pass}}
            project=ANS operation=fetch issue="ANS-63"
      register: issue
    
    - name: Create a unix account for the reporter
      sudo: true
      user: name="{{issue.meta.fields.creator.name}}" comment="{{issue.meta.fields.creator.displayName}}"
    
    # Transition an issue by target status
    - name: Close the issue
      jira: uri={{server}} username={{user}} password={{pass}}
            issue={{issue.meta.key}} operation=transition status="Done"

.. note:: Currently this only works with basic-auth.


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

