.. _win_acl_inheritance:


win_acl_inheritance - Change ACL inheritance
++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Change ACL (Access Control List) inheritance and optionally copy inherited ACE's (Access Control Entry) to dedicated ACE's or vice versa.




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
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Path to be used for changing inheritance</div>        </td></tr>
                <tr><td>reorganize<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>False</li><li>True</li></ul></td>
        <td><div>For P(state) = <em>absent</em>, indicates if the inherited ACE's should be copied from the parent directory. This is necessary (in combination with removal) for a simple ACL instead of using multiple ACE deny entries.</div><div>For P(state) = <em>present</em>, indicates if the inherited ACE's should be deduplicated compared to the parent directory. This removes complexity of the ACL structure.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>absent</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Specify whether to enable <em>present</em> or disable <em>absent</em> ACL inheritance</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Disable inherited ACE's
      win_acl_inheritance:
        path: C:\apache
        state: absent
    
    - name: Disable and copy inherited ACE's
      win_acl_inheritance:
        path: C:\apache
        state: absent
        reorganize: True
    
    - name: Enable and remove dedicated ACE's
      win_acl_inheritance:
        path: C:\apache
        state: present
        reorganize: True





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
