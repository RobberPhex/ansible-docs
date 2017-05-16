.. _nclu:


nclu - Configure network interfaces using NCLU
++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Interface to the Network Command Line Utility, developed to make it easier to configure operating systems running ifupdown2 and Quagga, such as Cumulus Linux. Command documentation is available at https://docs.cumulusnetworks.com/display/DOCS/Network+Command+Line+Utility




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
                <tr><td>abort<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Boolean. When true, perform a 'net abort' before the block. This cleans out any uncommitted changes in the buffer. Mutually exclusive with <em>atomic</em>.</div>        </td></tr>
                <tr><td>atomic<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>When true, equivalent to both <em>commit</em> and <em>abort</em> being true. Mutually exclusive with <em>commit</em> and <em>atomic</em>.</div>        </td></tr>
                <tr><td>commands<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A list of strings containing the net commands to run. Mutually exclusive with <em>template</em>.</div>        </td></tr>
                <tr><td>commit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>When true, performs a 'net commit' at the end of the block. Mutually exclusive with <em>atomic</em>.</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Ansible-originated commit</td>
        <td></td>
        <td><div>Commit description that will be recorded to the commit log if <em>commit</em> or <em>atomic</em> are true.</div>        </td></tr>
                <tr><td>template<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A single, multi-line string with jinja2 formatting. This string will be broken by lines, and each line will be run through net. Mutually exclusive with <em>commands</em>.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    - name: Add two interfaces without committing any changes
      nclu:
        commands:
            - add int swp1
            - add int swp2
    
    - name: Add 48 interfaces and commit the change.
      nclu:
        template: |
            {% for iface in range(1,49) %}
            add int swp{{i}}
            {% endfor %}
        commit: true
        description: "Ansible - add swps1-48"
    
    - name: Atomically add an interface
      nclu:
        commands:
            - add int swp1
        atomic: true
        description: "Ansible - add swp1"

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
        <td> msg </td>
        <td> human-readable report of success or failure </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> interface bond0 config updated </td>
    </tr>
            <tr>
        <td> changed </td>
        <td> whether the interface was changed </td>
        <td align=center> changed </td>
        <td align=center> bool </td>
        <td align=center> True </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
