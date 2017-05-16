.. _apt_repository:


apt_repository - Add and remove APT repositories
++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Add or remove an APT repositories in Ubuntu and Debian.


Requirements
------------

  * python-apt


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
    <td>mode<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td>420</td>
        <td><ul></ul></td>
        <td><div>The octal mode for newly created files in sources.list.d</div></td></tr>
            <tr>
    <td>repo<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>none</td>
        <td><ul></ul></td>
        <td><div>A source string for the repository.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>A source string state.</div></td></tr>
            <tr>
    <td>update_cache<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Run the equivalent of <code>apt-get update</code> when a change occurs.  Cache updates are run after making changes.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates for the target repo will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Add specified repository into sources list.
    apt_repository: repo='deb http://archive.canonical.com/ubuntu hardy partner' state=present
    
    # Add source repository into sources list.
    apt_repository: repo='deb-src http://archive.canonical.com/ubuntu hardy partner' state=present
    
    # Remove specified repository from sources list.
    apt_repository: repo='deb http://archive.canonical.com/ubuntu hardy partner' state=absent
    
    # On Ubuntu target: add nginx stable repository from PPA and install its signing key.
    # On Debian target: adding PPA is not available, so it will fail immediately.
    apt_repository: repo='ppa:nginx/stable'


Notes
-----

.. note:: This module works on Debian and Ubuntu and requires ``python-apt``.
.. note:: This module supports Debian Squeeze (version 6) as well as its successors.
.. note:: This module treats Debian and Ubuntu distributions separately. So PPA could be installed only on Ubuntu machines.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

