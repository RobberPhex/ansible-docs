.. _locale_gen:


locale_gen - Creates or removes locales.
++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages locales by editing /etc/locale.gen and invoking locale-gen.




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
        <td><div>Name and encoding of the locale, such as "en_GB.UTF-8".</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the locale shall be present.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Ensure a locale exists.
    - locale_gen: name=de_CH.UTF-8 state=present




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

