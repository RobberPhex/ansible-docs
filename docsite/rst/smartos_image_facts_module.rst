.. _smartos_image_facts:


smartos_image_facts - Get SmartOS image details.
++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Retrieve facts about all installed images on SmartOS. Facts will be inserted to the ansible_facts key.




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
    <td>filters<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Criteria for selecting image. Can be any value from image manifest and 'published_date', 'published', 'source', 'clones', and 'size'. More informaton can be found at <a href='https://smartos.org/man/1m/imgadm'>https://smartos.org/man/1m/imgadm</a> under 'imgadm list'.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Return facts about all installed images.
    smartos_image_facts:
    
    # Return all private active Linux images.
    smartos_image_facts: filters="os=linux state=active public=false"
    
    # Show, how many clones does every image have.
    smartos_image_facts:
    
    debug: msg="{{ smartos_images[item]['name'] }}-{{smartos_images[item]['version'] }}
                has {{ smartos_images[item]['clones'] }} VM(s)"
    with_items: smartos_images.keys()




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

