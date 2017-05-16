.. _set_stats:


set_stats - Set stats for the current ansible run
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module allows setting/accumulating stats on the current ansible run, either per host of for all hosts in the run.




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
    <td>aggregate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>boolean that indicates if the provided value is aggregated to the existing stat <code>yes</code> or will replace it <code>no</code></div></td></tr>
            <tr>
    <td>data<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A dictionary of which each key represents a stat (or variable) you want to keep track of</div></td></tr>
            <tr>
    <td>per_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>boolean that indicates if the stats is per host or for all hosts in the run.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Aggregating packages_installed stat per host
    - set_stats:
        data:
          packages_installed: 31
    
    # Aggregating random stats for all hosts using complex arguments
    - set_stats:
        data:
          one_stat: 11
          other_stat: "{{ local_var * 2 }}"
          another_stat: "{{ some_registered_var.results | map(attribute='ansible_facts.some_fact') | list }}"
        per_host: no
    
    
    # setting stats (not aggregating)
    - set_stats:
        data:
          the_answer: 42
        aggregate: no




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

