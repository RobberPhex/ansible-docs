.. _apt_repository:


apt_repository - Add and remove APT repositories
++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Add or remove an APT repositories in Ubuntu and Debian.


Requirements (on host that executes module)
-------------------------------------------

  * python-apt (python 2)
  * python3-apt (python 3)


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
                <tr><td>codename<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Override the distribution codename to use for PPA repositories. Should usually only be set when working with a PPA on a non-Ubuntu target (e.g. Debian or Mint)</div>        </td></tr>
                <tr><td>filename<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Sets the name of the source list file in sources.list.d. Defaults to a file name based on the repository source url. The .list extension will be automatically added.</div>        </td></tr>
                <tr><td>mode<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td>420</td>
        <td></td>
        <td><div>The octal mode for newly created files in sources.list.d</div>        </td></tr>
                <tr><td>repo<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>none</td>
        <td></td>
        <td><div>A source string for the repository.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>A source string state.</div>        </td></tr>
                <tr><td>update_cache<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Run the equivalent of <code>apt-get update</code> when a change occurs.  Cache updates are run after making changes.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates for the target repo will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Add specified repository into sources list.
    - apt_repository:
        repo: deb http://archive.canonical.com/ubuntu hardy partner
        state: present
    
    # Add specified repository into sources list using specified filename.
    - apt_repository:
        repo: deb http://dl.google.com/linux/chrome/deb/ stable main
        state: present
        filename: 'google-chrome'
    
    # Add source repository into sources list.
    - apt_repository:
        repo: deb-src http://archive.canonical.com/ubuntu hardy partner
        state: present
    
    # Remove specified repository from sources list.
    - apt_repository:
        repo: deb http://archive.canonical.com/ubuntu hardy partner
        state: absent
    
    # Add nginx stable repository from PPA and install its signing key.
    # On Ubuntu target:
    - apt_repository:
        repo: 'ppa:nginx/stable'
    
    # On Debian target
    - apt_repository:
        repo: 'ppa:nginx/stable'
        codename: 'trusty'


Notes
-----

.. note::
    - This module works on Debian, Ubuntu and their derivatives.
    - This module supports Debian Squeeze (version 6) as well as its successors.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
