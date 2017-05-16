.. _win_say:


win_say - Text to speech module for Windows to speak messages and optionally play sounds
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Uses .NET libraries to convert text to speech and optionally play .wav sounds.  Audio Service needs to be running and some kind of speakers or headphones need to be attached to the windows target(s) for the speech to be audible.




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
                <tr><td>end_sound_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Full path to a <code>.wav</code> file containing a sound to play after the text has been spoken.  Useful on conference calls to alert other speakers that ansible has finished speaking.</div>        </td></tr>
                <tr><td>msg<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td></td>
        <td><div>The text to be spoken.  Use either msg or msg_file.  Optional so that you can use this module just to play sounds.</div>        </td></tr>
                <tr><td>msg_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td></td>
        <td><div>Full path to a windows format text file containing the text to be spokend.  Use either msg or msg_file.  Optional so that you can use this module just to play sounds.</div>        </td></tr>
                <tr><td>speech_speed<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>How fast or slow to speak the text.  Must be an integer value in the range -10 to 10.  -10 is slowest, 10 is fastest.</div>        </td></tr>
                <tr><td>start_sound_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Full path to a <code>.wav</code> file containing a sound to play before the text is spoken.  Useful on conference calls to alert other speakers that ansible has something to say.</div>        </td></tr>
                <tr><td>voice<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>system default voice</td>
        <td></td>
        <td><div>Which voice to use. See notes for how to discover installed voices.  If the requested voice is not available the default voice will be used. Example voice names from Windows 10 are 'Microsoft Zira Desktop' and 'Microsoft Hazel Desktop'.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

      # Warn of impending deployment
    - win_say:
        msg: Warning, deployment commencing in 5 minutes, please log out.
      # Using a different voice and a start sound
    - win_say:
        start_sound_path: C:\Windows\Media\ding.wav
        msg: Warning, deployment commencing in 5 minutes, please log out.
        voice: Microsoft Hazel Desktop
      # example with start and end sound
    - win_say:
        start_sound_path: C:\Windows\Media\Windows Balloon.wav
        msg: New software installed
        end_sound_path: C:\Windows\Media\chimes.wav
      # text from file example
    - win_say:
        start_sound_path: C:\Windows\Media\Windows Balloon.wav
        msg_file: AppData\Local\Temp\morning_report.txt
        end_sound_path: C:\Windows\Media\chimes.wav

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
        <td> message_text </td>
        <td> the text that the module attempted to speak </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Warning, deployment commencing in 5 minutes. </td>
    </tr>
            <tr>
        <td> voice </td>
        <td> the voice used to speak the text. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Microsoft Hazel Desktop </td>
    </tr>
            <tr>
        <td> voice_info </td>
        <td> the voice used to speak the text. </td>
        <td align=center> when requested voice could not be loaded </td>
        <td align=center> string </td>
        <td align=center> Could not load voice TestVoice, using system default voice </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Needs speakers or headphones to do anything useful.
    - To find which voices are installed, run the following powershell Add-Type -AssemblyName System.Speech $speech = New-Object -TypeName System.Speech.Synthesis.SpeechSynthesizer $speech.GetInstalledVoices() | ForEach-Object { $_.VoiceInfo } $speech.Dispose()
    - Speech can be surprisingly slow, so its best to keep message text short.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
