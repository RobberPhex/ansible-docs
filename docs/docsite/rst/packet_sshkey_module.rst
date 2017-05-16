.. _packet_sshkey:


packet_sshkey - Create/delete an SSH key in Packet host.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create/delete an SSH key in Packet host.
* API is documented at https://www.packet.net/help/api/#page:ssh-keys,header:ssh-keys-ssh-keys-post.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * packet-python


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
                <tr><td>auth_token<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Packet api token. You can also supply it in env var <code>PACKET_API_TOKEN</code>.</div>        </td></tr>
                <tr><td>fingerprint<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Fingerprint of the key which you want to remove.</div>        </td></tr>
                <tr><td>id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>UUID of the key which you want to remove.</div>        </td></tr>
                <tr><td>key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Public Key string ({type} {base64 encoded key} {description}).</div>        </td></tr>
                <tr><td>key_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>File with the public key.</div>        </td></tr>
                <tr><td>label<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Label for the key. If you keep it empty, it will be read from key string.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the target.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # All the examples assume that you have your Packet API token in env var PACKET_API_TOKEN.
    # You can also pass the api token in module param auth_token.
    
    - name: create sshkey from string
      hosts: localhost
      tasks:
        packet_sshkey:
          key: ssh-dss AAAAB3NzaC1kc3MAAACBAIfNT5S0ncP4BBJBYNhNPxFF9lqVhfPeu6SM1LoCocxqDc1AT3zFRi8hjIf6TLZ2AA4FYbcAWxLMhiBxZRVldT9GdBXile78kAK5z3bKTwq152DCqpxwwbaTIggLFhsU8wrfBsPWnDuAxZ0h7mmrCjoLIE3CNLDA/NmV3iB8xMThAAAAFQCStcesSgR1adPORzBxTr7hug92LwAAAIBOProm3Gk+HWedLyE8IfofLaOeRnbBRHAOL4z0SexKkVOnQ/LGN/uDIIPGGBDYTvXgKZT+jbHeulRJ2jKgfSpGKN4JxFQ8uzVH492jEiiUJtT72Ss1dCV4PmyERVIw+f54itihV3z/t25dWgowhb0int8iC/OY3cGodlmYb3wdcQAAAIBuLbB45djZXzUkOTzzcRDIRfhaxo5WipbtEM2B1fuBt2gyrvksPpH/LK6xTjdIIb0CxPu4OCxwJG0aOz5kJoRnOWIXQGhH7VowrJhsqhIc8gN9ErbO5ea8b1L76MNcAotmBDeTUiPw01IJ8MdDxfmcsCslJKgoRKSmQpCwXQtN2g== tomk@hp2
    
    - name: create sshkey from file
      hosts: localhost
      tasks:
        packet_sshkey:
          label: key from file
          key_file: ~/ff.pub
    
    - name: remove sshkey by id
      hosts: localhost
      tasks:
        packet_sshkey:
          state: absent
          id: eef49903-7a09-4ca1-af67-4087c29ab5b6

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
        <td> changed </td>
        <td> True if a sshkey was created or removed. </td>
        <td align=center> always </td>
        <td align=center> bool </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> sshkeys </td>
        <td> Information about sshkeys that were createe/removed. </td>
        <td align=center> always </td>
        <td align=center> array </td>
        <td align=center> [{'fingerprint': '5c:93:74:7c:ed:07:17:62:28:75:79:23:d6:08:93:46', 'id': '41d61bd8-3342-428b-a09c-e67bdd18a9b7', 'key': 'ssh-dss AAAAB3NzaC1kc3MAAACBAIfNT5S0ncP4BBJBYNhNPxFF9lqVhfPeu6SM1LoCocxqDc1AT3zFRi8hjIf6TLZ2AA4FYbcAWxLMhiBxZRVldT9GdBXile78kAK5z3bKTwq152DCqpxwwbaTIggLFhsU8wrfBsPWnDuAxZ0h7mmrCjoLIE3CNLDA/NmV3iB8xMThAAAAFQCStcesSgR1adPORzBxTr7hug92LwAAAIBOProm3Gk+HWedLyE8IfofLaOeRnbBRHAOL4z0SexKkVOnQ/LGN/uDIIPGGBDYTvXgKZT+jbHeulRJ2jKgfSpGKN4JxFQ8uzVH492jEiiUJtT72Ss1dCV4PmyERVIw+f54itihV3z/t25dWgowhb0int8iC/OY3cGodlmYb3wdcQAAAIBuLbB45djZXzUkOTzzcRDIRfhaxo5WipbtEM2B1fuBt2gyrvksPpH/LK6xTjdIIb0CxPu4OCxwJG0aOz5kJoRnOWIXQGhH7VowrJhsqhIc8gN9ErbO5ea8b1L76MNcAotmBDeTUiPw01IJ8MdDxfmcsCslJKgoRKSmQpCwXQtN2g== tomk@hp2', 'label': 'mynewkey33'}] </td>
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
