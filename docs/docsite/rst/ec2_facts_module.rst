.. _ec2_facts:


ec2_facts - Gathers facts about remote hosts within ec2 (aws)
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module fetches data from the metadata servers in ec2 (aws) as per http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-metadata.html. The module must be called from within the EC2 instance itself.




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
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 1.5.1)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Conditional example
    - name: Gather facts
      ec2_facts:
    
    - name: Conditional
      debug:
        msg: "This instance is a t1.micro"
      when: ansible_ec2_instance_type == "t1.micro"


Notes
-----

.. note::
    - Parameters to filter on ec2_facts may be added later.



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is supported mainly by the community and is curated by core committers.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
