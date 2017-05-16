.. _expect:


expect - Executes a command and responds to prompts
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* The ``expect`` module executes a command and responds to prompts
* The given command will be executed on all selected nodes. It will not be processed through the shell, so variables like ``$HOME`` and operations like ``"<"``, ``">"``, ``"|"``, and ``"&"`` will not work


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * pexpect >= 3.3


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
                <tr><td>chdir<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>cd into this directory before running the command</div>        </td></tr>
                <tr><td>command<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>the command module takes command to run.</div>        </td></tr>
                <tr><td>creates<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>a filename, when it already exists, this step will <b>not</b> be run.</div>        </td></tr>
                <tr><td>echo<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Whether or not to echo out your response strings</div>        </td></tr>
                <tr><td>removes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>a filename, when it does not exist, this step will <b>not</b> be run.</div>        </td></tr>
                <tr><td>responses<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Mapping of expected string/regex and string to respond with. If the response is a list, successive matches return successive responses. List functionality is new in 2.1.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>30</td>
        <td></td>
        <td><div>Amount of time in seconds to wait for the expected strings</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Case insensitve password string match
    - expect:
        command: passwd username
        responses:
          (?i)password: "MySekretPa$$word"
    
    # Generic question with multiple different responses
    - expect:
        command: /path/to/custom/command
        responses:
          Question:
            - response1
            - response2
            - response3


Notes
-----

.. note::
    - If you want to run a command through the shell (say you are using ``<``, ``>``, ``|``, etc), you must specify a shell in the command such as ``/bin/bash -c "/path/to/something | grep else"``
    - The question, or key, under *responses* is a python regex match. Case insensitive searches are indicated with a prefix of ``?i``
    - By default, if a question is encountered multiple times, it's string response will be repeated. If you need different responses for successive question matches, instead of a string response, use a list of strings as the response. The list functionality is new in 2.1



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
