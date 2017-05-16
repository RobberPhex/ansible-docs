.. _homebrew_tap:


homebrew_tap - Tap a Homebrew repository.
+++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Tap external Homebrew repositories.


Requirements (on host that executes module)
-------------------------------------------

  * homebrew


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
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The GitHub user/organization repository to tap.</div></br>
        <div style="font-size: small;">aliases: tap<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>state of the repository.</div></td></tr>
            <tr>
    <td>url<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The optional git URL of the repository to tap. The URL is not assumed to be on GitHub, and the protocol doesn't have to be HTTP. Any location and protocol that git can handle is fine.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    homebrew_tap: name=homebrew/dupes
    homebrew_tap: name=homebrew/dupes state=absent
    homebrew_tap: name=homebrew/dupes,homebrew/science state=present
    homebrew_tap: name=telemachus/brew url=https://bitbucket.org/telemachus/brew




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

