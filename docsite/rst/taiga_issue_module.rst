.. _taiga_issue:


taiga_issue - Creates/deletes an issue in a Taiga Project Management Platform
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Creates/deletes an issue in a Taiga Project Management Platform (https://taiga.io).
An issue is identified by the combination of project, issue subject and issue type.
This module implements the creation or deletion of issues (not the update).


Requirements (on host that executes module)
-------------------------------------------

  * python-taiga


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
    <td>attachment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Path to a file to be attached to the issue.</div></td></tr>
            <tr>
    <td>attachment_description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A string describing the file to be attached to the issue.</div></td></tr>
            <tr>
    <td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The issue description.</div></td></tr>
            <tr>
    <td>issue_type<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The issue type. Must exist previously.</div></td></tr>
            <tr>
    <td>priority<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Normal</td>
        <td><ul></ul></td>
        <td><div>The issue priority. Must exist previously.</div></td></tr>
            <tr>
    <td>project<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the project containing the issue. Must exist previously.</div></td></tr>
            <tr>
    <td>severity<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Normal</td>
        <td><ul></ul></td>
        <td><div>The issue severity. Must exist previously.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the issue should be present or not.</div></td></tr>
            <tr>
    <td>status<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>New</td>
        <td><ul></ul></td>
        <td><div>The issue status. Must exist previously.</div></td></tr>
            <tr>
    <td>subject<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The issue subject.</div></td></tr>
            <tr>
    <td>tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A lists of tags to be assigned to the issue.</div></td></tr>
            <tr>
    <td>taiga_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>https://api.taiga.io</td>
        <td><ul></ul></td>
        <td><div>The hostname of the Taiga instance.</div></td></tr>
        </table>
    </br>



Examples
--------

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


Notes
-----

.. note:: The authentication is achieved either by the environment variable TAIGA_TOKEN or by the pair of environment variables TAIGA_USERNAME and TAIGA_PASSWORD


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

