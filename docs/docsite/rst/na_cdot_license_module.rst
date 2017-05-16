.. _na_cdot_license:


na_cdot_license - Manage NetApp cDOT protocol and feature licenses
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Add or remove licenses on NetApp ONTAP.


Requirements (on host that executes module)
-------------------------------------------

  * A physical or virtual clustered Data ONTAP system. The modules were developed with Clustered Data ONTAP 8.3
  * Ansible 2.2
  * netapp-lib (2015.9.25). Install using 'pip install netapp-lib'


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
                <tr><td>hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The hostname or IP address of the ONTAP instance.</div>        </td></tr>
                <tr><td rowspan="2">licenses<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td><td></td>
    <td> <div>List of licenses to add or remove.</div><div>Please note that trying to remove a non-existent license will throw an error.</div>    </tr>
    <tr>
    <td colspan="5">
    <table border=1 cellpadding=4>
    <caption><b>Dictionary object licenses</b></caption>
    <tr>
    <th class="head">parameter</th>
    <th class="head">required</th>
    <th class="head">default</th>
    <th class="head">choices</th>
    <th class="head">comments</th>
    </tr>
                    <tr><td>fcp<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>F</div><div>C</div><div>P</div><div> </div><div>L</div><div>i</div><div>c</div><div>e</div><div>n</div><div>s</div><div>e</div>        </td></tr>
                    <tr><td>snaplock<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>S</div><div>n</div><div>a</div><div>p</div><div>L</div><div>o</div><div>c</div><div>k</div><div> </div><div>L</div><div>i</div><div>c</div><div>e</div><div>n</div><div>s</div><div>e</div>        </td></tr>
                    <tr><td>v_storageattach<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>V</div><div>i</div><div>r</div><div>t</div><div>u</div><div>a</div><div>l</div><div> </div><div>A</div><div>t</div><div>t</div><div>a</div><div>c</div><div>h</div><div>e</div><div>d</div><div> </div><div>S</div><div>t</div><div>o</div><div>r</div><div>a</div><div>g</div><div>e</div><div> </div><div>L</div><div>i</div><div>c</div><div>e</div><div>n</div><div>s</div><div>e</div>        </td></tr>
                    <tr><td>cifs<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>C</div><div>I</div><div>F</div><div>S</div><div> </div><div>L</div><div>i</div><div>c</div><div>e</div><div>n</div><div>s</div><div>e</div>        </td></tr>
                    <tr><td>iscsi<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>i</div><div>S</div><div>C</div><div>S</div><div>I</div><div> </div><div>L</div><div>i</div><div>c</div><div>e</div><div>n</div><div>s</div><div>e</div>        </td></tr>
                    <tr><td>flexclone<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>F</div><div>l</div><div>e</div><div>x</div><div>C</div><div>l</div><div>o</div><div>n</div><div>e</div><div> </div><div>L</div><div>i</div><div>c</div><div>e</div><div>n</div><div>s</div><div>e</div>        </td></tr>
                    <tr><td>cdmi<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>C</div><div>D</div><div>M</div><div>I</div><div> </div><div>L</div><div>i</div><div>c</div><div>e</div><div>n</div><div>s</div><div>e</div>        </td></tr>
                    <tr><td>snaprestore<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>S</div><div>n</div><div>a</div><div>p</div><div>R</div><div>e</div><div>s</div><div>t</div><div>o</div><div>r</div><div>e</div><div> </div><div>L</div><div>i</div><div>c</div><div>e</div><div>n</div><div>s</div><div>e</div>        </td></tr>
                    <tr><td>snapprotectapps<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>S</div><div>n</div><div>a</div><div>p</div><div>P</div><div>r</div><div>o</div><div>t</div><div>e</div><div>c</div><div>t</div><div>A</div><div>p</div><div>p</div><div> </div><div>L</div><div>i</div><div>c</div><div>e</div><div>n</div><div>s</div><div>e</div>        </td></tr>
                    <tr><td>base<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>C</div><div>l</div><div>u</div><div>s</div><div>t</div><div>e</div><div>r</div><div> </div><div>B</div><div>a</div><div>s</div><div>e</div><div> </div><div>L</div><div>i</div><div>c</div><div>e</div><div>n</div><div>s</div><div>e</div>        </td></tr>
                    <tr><td>nfs<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>N</div><div>F</div><div>S</div><div> </div><div>L</div><div>i</div><div>c</div><div>e</div><div>n</div><div>s</div><div>e</div>        </td></tr>
                    <tr><td>snapmirror<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>S</div><div>n</div><div>a</div><div>p</div><div>M</div><div>i</div><div>r</div><div>r</div><div>o</div><div>r</div><div> </div><div>L</div><div>i</div><div>c</div><div>e</div><div>n</div><div>s</div><div>e</div>        </td></tr>
                    <tr><td>snapvault<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>S</div><div>n</div><div>a</div><div>p</div><div>V</div><div>a</div><div>u</div><div>l</div><div>t</div><div> </div><div>L</div><div>i</div><div>c</div><div>e</div><div>n</div><div>s</div><div>e</div>        </td></tr>
                    <tr><td>snapmanagersuite<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>S</div><div>n</div><div>a</div><div>p</div><div>M</div><div>a</div><div>n</div><div>a</div><div>g</div><div>e</div><div>r</div><div>S</div><div>u</div><div>i</div><div>t</div><div>e</div><div> </div><div>L</div><div>i</div><div>c</div><div>e</div><div>n</div><div>s</div><div>e</div>        </td></tr>
        </table>
    </td>
    </tr>
        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Password for the specified user.</div>        </td></tr>
                <tr><td>remove_expired<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Remove licenses that have expired in the cluster.</div>        </td></tr>
                <tr><td>remove_unused<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Remove licenses that have no controller affiliation in the cluster.</div>        </td></tr>
                <tr><td>serial_number<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Serial number of the node associated with the license.</div><div>This parameter is used primarily when removing license for a specific service.</div><div>If this parameter is not provided, the cluster serial number is used by default.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>This can be a Cluster-scoped or SVM-scoped account, depending on whether a Cluster-level or SVM-level API is required. For more information, please read the documentation <a href='https://goo.gl/BRu78Z'>https://goo.gl/BRu78Z</a>.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Add licenses
      na_cdot_license:
        hostname: "{{ netapp_hostname }}"
        username: "{{ netapp_username }}"
        password: "{{ netapp_password }}"
        serial_number: #################
        licenses:
          nfs: #################
          cifs: #################
          iscsi: #################
          fcp: #################
          snaprestore: #################
          flexclone: #################
    
    - name: Remove licenses
      na_cdot_license:
        hostname: "{{ netapp_hostname }}"
        username: "{{ netapp_username }}"
        password: "{{ netapp_password }}"
        remove_unused: false
        remove_expired: true
        serial_number: #################
        licenses:
          nfs: remove


Notes
-----

.. note::
    - The modules prefixed with ``netapp\_cdot`` are built to support the ONTAP storage platform.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
