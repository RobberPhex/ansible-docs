.. _pam_limits:


pam_limits - Modify Linux PAM limits
++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* The ``pam_limits`` module modify PAM limits, default in /etc/security/limits.conf. For the full documentation, see man limits.conf(5).




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
                <tr><td>backup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Create a backup file including the timestamp information so you can get the original file back if you somehow clobbered it incorrectly.</div>        </td></tr>
                <tr><td>comment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Comment associated with the limit.</div>        </td></tr>
                <tr><td>dest<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/etc/security/limits.conf</td>
        <td></td>
        <td><div>Modify the limits.conf path.</div>        </td></tr>
                <tr><td>domain<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>A username, @groupname, wildcard, uid/gid range.</div>        </td></tr>
                <tr><td>limit_item<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>core</li><li>data</li><li>fsize</li><li>memlock</li><li>nofile</li><li>rss</li><li>stack</li><li>cpu</li><li>nproc</li><li>as</li><li>maxlogins</li><li>maxsyslogins</li><li>priority</li><li>locks</li><li>sigpending</li><li>msgqueue</li><li>nice</li><li>rtprio</li><li>chroot</li></ul></td>
        <td><div>The limit to be set</div>        </td></tr>
                <tr><td>limit_type<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>hard</li><li>soft</li><li>-</li></ul></td>
        <td><div>Limit type, see <code>man limits</code> for an explanation</div>        </td></tr>
                <tr><td>use_max<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If set to <code>yes</code>, the maximal value will be used or conserved. If the specified value is superior to the value in the file, file content is replaced with the new value, else content is not modified.</div>        </td></tr>
                <tr><td>use_min<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If set to <code>yes</code>, the minimal value will be used or conserved. If the specified value is inferior to the value in the file, file content is replaced with the new value, else content is not modified.</div>        </td></tr>
                <tr><td>value<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The value of the limit.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Add or modify nofile soft limit for the user joe
    - pam_limits:
        domain: joe
        limit_type: soft
        limit_item: nofile
        value: 64000
    
    # Add or modify fsize hard limit for the user smith. Keep or set the maximal value.
    - pam_limits:
        domain: smith
        limit_type: hard
        limit_item: fsize
        value: 1000000
        use_max: yes
    
    # Add or modify memlock, both soft and hard, limit for the user james with a comment.
    - pam_limits:
        domain: james
        limit_type: '-'
        limit_item: memlock
        value: unlimited
        comment: unlimited memory lock for james





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
