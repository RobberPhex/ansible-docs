.. _layman:


layman - Manage Gentoo overlays
+++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Uses Layman to manage an additional repositories for the Portage package manager on Gentoo Linux. Please note that Layman must be installed on a managed node prior using this module.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * layman python module


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
                <tr><td>list_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>An URL of the alternative overlays list that defines the overlay to install. This list will be fetched and saved under <code>${overlay_defs}</code>/${name}.xml), where <code>overlay_defs</code> is readed from the Layman's configuration.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The overlay id to install, synchronize, or uninstall. Use 'ALL' to sync all of the installed overlays (can be used only when <code>state=updated</code>).</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>updated</li></ul></td>
        <td><div>Whether to install (<code>present</code>), sync (<code>updated</code>), or uninstall (<code>absent</code>) the overlay.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 1.9.3)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be set to <code>no</code> when no other option exists.  Prior to 1.9.3 the code defaulted to <code>no</code>.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Install the overlay 'mozilla' which is on the central overlays list.
    - layman:
        name: mozilla
    
    # Install the overlay 'cvut' from the specified alternative list.
    - layman:
        name: cvut
        list_url: 'http://raw.github.com/cvut/gentoo-overlay/master/overlay.xml'
    
    # Update (sync) the overlay 'cvut', or install if not installed yet.
    - layman:
        name: cvut
        list_url: 'http://raw.github.com/cvut/gentoo-overlay/master/overlay.xml'
        state: updated
    
    # Update (sync) all of the installed overlays.
    - layman:
        name: ALL
        state: updated
    
    # Uninstall the overlay 'cvut'.
    - layman:
        name: cvut
        state: absent





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
