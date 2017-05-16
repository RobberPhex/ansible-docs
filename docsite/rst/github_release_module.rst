.. _github_release:


github_release - Interact with GitHub Releases
++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Fetch metadata about Github Releases


Requirements (on host that executes module)
-------------------------------------------

  * github3.py >= 1.0.0a3


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
    <td>action<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>latest_release</li></ul></td>
        <td><div>Action to perform</div></td></tr>
            <tr>
    <td>repo<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Repository name</div></td></tr>
            <tr>
    <td>token<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Github Personal Access Token for authenticating</div></td></tr>
            <tr>
    <td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The GitHub account that owns the repository</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Get latest release of test/test
      github:
        token: tokenabc1234567890
        user: testuser
        repo: testrepo
        action: latest_release

Return Values
-------------

Common return values are documented here :doc:`common_return_values`, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> latest_release </td>
        <td> Version of the latest release </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 1.1.0 </td>
    </tr>
        
    </table>
    </br></br>



    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

