.. _taiga_issue:


taiga_issue - Creates/deletes an issue in a Taiga Project Management Platform
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 2.0

Creates/deletes an issue in a Taiga Project Management Platform (https://taiga.io).
An issue is identified by the combination of project, issue subject and issue type.
This module implements the creation or deletion of issues (not the update).

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
    <td>attachment</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>Path to a file to be attached to the issue.</td>
    </tr>
            <tr>
    <td>attachment_description</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A string describing the file to be attached to the issue.</td>
    </tr>
            <tr>
    <td>description</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The issue description.</td>
    </tr>
            <tr>
    <td>issue_type</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The issue type. Must exist previously.</td>
    </tr>
            <tr>
    <td>priority</td>
    <td>no</td>
    <td>Normal</td>
        <td><ul></ul></td>
        <td>The issue priority. Must exist previously.</td>
    </tr>
            <tr>
    <td>project</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of the project containing the issue. Must exist previously.</td>
    </tr>
            <tr>
    <td>severity</td>
    <td>no</td>
    <td>Normal</td>
        <td><ul></ul></td>
        <td>The issue severity. Must exist previously.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Whether the issue should be present or not.</td>
    </tr>
            <tr>
    <td>status</td>
    <td>no</td>
    <td>New</td>
        <td><ul></ul></td>
        <td>The issue status. Must exist previously.</td>
    </tr>
            <tr>
    <td>subject</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The issue subject.</td>
    </tr>
            <tr>
    <td>tags</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A lists of tags to be assigned to the issue.</td>
    </tr>
            <tr>
    <td>taiga_host</td>
    <td>no</td>
    <td>https://api.taiga.io</td>
        <td><ul></ul></td>
        <td>The hostname of the Taiga instance.</td>
    </tr>
        </table>


.. note:: Requires python-taiga


Examples
--------

.. raw:: html

    <br/>


::

    # Create an issue in the my hosted Taiga environment and attach an error log
    - taiga_issue:
        taiga_host: https://mytaigahost.example.com
        project: myproject
        subject: An error has been found
        issue_type: Bug
        priority: High
        status: New
        severity: Important
        description: An error has been found. Please check the attached error log for details.
        attachment: /path/to/error.log
        attachment_description: Error log file
        tags:
          - Error
          - Needs manual check
        state: present
    
    # Deletes the previously created issue
    - taiga_issue:
        taiga_host: https://mytaigahost.example.com
        project: myproject
        subject: An error has been found
        issue_type: Bug
        state: absent

.. note:: The authentication is achieved either by the environment variable TAIGA_TOKEN or by the pair of environment variables TAIGA_USERNAME and TAIGA_PASSWORD


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

