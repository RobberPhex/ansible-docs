.. _win_msg:


win_msg - Sends a message to logged in users on Windows hosts.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Wraps the msg.exe command in order to send messages to Windows hosts.




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
                <tr><td>display_seconds<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>How long to wait for receiver to acknowledge message, in seconds.</div>        </td></tr>
                <tr><td>msg<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Hello world!</td>
        <td></td>
        <td><div>The text of the message to be displayed.</div>        </td></tr>
                <tr><td>to<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>*</td>
        <td></td>
        <td><div>Who to send the message to. Can be a username, sessionname or sessionid.</div>        </td></tr>
                <tr><td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Whether to wait for users to respond.  Module will only wait for the number of seconds specified in display_seconds or 10 seconds if not specified. However, if <em>wait</em> is true, the message is sent to each logged on user in turn, waiting for the user to either press 'ok' or for the timeout to elapse before moving on to the next user.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

      # Warn logged in users of impending upgrade
      win_msg:
        display_seconds: 60
        msg: "Automated upgrade about to start.  Please save your work and log off before {{ deployment_start_time  }}"

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
        <td> Test of the message that was sent. </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> Automated upgrade about to start.  Please save your work and log off before 22 July 2016 18:00:00 </td>
    </tr>
            <tr>
        <td> wait </td>
        <td> Value of wait module parameter. </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> display_seconds </td>
        <td> Value of display_seconds module parameter. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 10 </td>
    </tr>
            <tr>
        <td> runtime_seconds </td>
        <td> How long the module took to run on the remote windows host. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 22 July 2016 17:45:51 </td>
    </tr>
            <tr>
        <td> sent_localtime </td>
        <td> local time from windows host when the message was sent. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 22 July 2016 17:45:51 </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - This module must run on a windows host, so ensure your play targets windows hosts, or delegates to a windows host.
    - Messages are only sent to the local host where the module is run.
    - The module does not support sending to users listed in a file.
    - Setting wait to true can result in long run times on systems with many logged in users.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
