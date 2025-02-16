=====================
Webex Teams Archiver
=====================

*Simple utility to archive Webex Teams rooms*

.. image:: https://static.production.devnetcloud.com/codeexchange/assets/images/devnet-published.svg
    :target: https://developer.cisco.com/codeexchange/github/repo/CiscoDevNet/webex-teams-archiver
.. image:: https://img.shields.io/badge/license-MIT-blue.svg
    :target: https://github.com/CiscoDevNet/webex-teams-archiver/blob/master/LICENSE
.. image:: https://img.shields.io/pypi/v/webexteamsarchiver.svg
    :target: https://pypi.python.org/pypi/webexteamsarchiver

-------------------------------------------------------------------------------

Webex Teams Archiver extracts the messages and files out of a Webex Teams room and saves them in text, HTML, and JSON formats.

Example
-------

.. code-block:: python

    from webexteamsarchiver import WebexTeamsArchiver

    personal_token = "mytoken"
    archiver = WebexTeamsArchiver(personal_token)
    
    # room id from https://developer.webex.com/endpoint-rooms-get.html 
    room_id = "Y2lzY29zcGFyazovL3VzL1JPT00vd2ViZXh0ZWFtc2FyY2hpdmVy"
    archiver.archive_room(room_id)
    
Produces the following files:

.. code-block:: bash

    $ ls 
    Title_Timestamp_Y2lzY29zcGFyazovL3VzL1JPT00vd2ViZXh0ZWFtc2FyY2hpdmVy.tgz
    Title_Timestamp_Y2lzY29zcGFyazovL3VzL1JPT00vd2ViZXh0ZWFtc2FyY2hpdmVy

    $ ls Title_Timestamp_Y2lzY29zcGFyazovL3VzL1JPT00vd2ViZXh0ZWFtc2FyY2hpdmVy/
    Title_Timestamp_Y2lzY29zcGFyazovL3VzL1JPT00vd2ViZXh0ZWFtc2FyY2hpdmVy.html
    Title_Timestamp_Y2lzY29zcGFyazovL3VzL1JPT00vd2ViZXh0ZWFtc2FyY2hpdmVy.json
    Title_Timestamp_Y2lzY29zcGFyazovL3VzL1JPT00vd2ViZXh0ZWFtc2FyY2hpdmVy.txt
    attachments/
    avatars/
    space_details.json

Below is an example of a simple room that got archived.

.. image:: https://raw.githubusercontent.com/CiscoDevNet/webex-teams-archiver/master/sample.png
   :scale: 40 %


Note 1: The HTML version of the archive requires Internet connectivity because of the CSS, which is not packaged with the archive because of licensing conflicts.

Note 2: Some older spaces were affected by the Webex Teams 2018 outage which may cause the archiver to crash. This is pending a workaround_ from the SDK.

Note 3: Please note that use of the Webex Teams Archiver may violate the retention policy, if any, applicable to your use of Webex Teams.

Installation
------------

Installing and upgrading is easy:

**Install via PIP**

.. code-block:: bash

    $ pip install webexteamsarchiver

**Upgrading to the latest Version**

.. code-block:: bash

    $ pip install webexteamsarchiver --upgrade

Options
-------

The `archive_room` method exposes the following options:

+----------------------+-------------------+---------------------------------------------------+ 
| Argument             | Default Value     | Description                                       | 
+======================+===================+===================================================+
| text_format          | True              | Create a text version of the archive              |
+----------------------+-------------------+---------------------------------------------------+
| html_format          | True              | Create an HTML version of the archive             |
+----------------------+-------------------+---------------------------------------------------+
| json_format          | True              | Create a JSON version of the archive              |
+----------------------+-------------------+---------------------------------------------------+


In addition, the `options` kwargs supports the following additional options today:

+----------------------+-------------------+---------------------------------------------------+ 
| Argument             | Default Value     | Description                                       | 
+======================+===================+===================================================+
| overwrite_folder     | True              | Overwrite the archive folder if it already exists |
+----------------------+-------------------+---------------------------------------------------+
| delete_folder        | False             | Delete the archive folder when done               |
+----------------------+-------------------+---------------------------------------------------+
| reverse_order        | True              | Order messages by most recent on the bottom       |
+----------------------+-------------------+---------------------------------------------------+
| download_attachments | True              | Download attachments sent to the room             |
+----------------------+-------------------+---------------------------------------------------+
| download_avatars     | True              | Download avatar images                            |
+----------------------+-------------------+---------------------------------------------------+
| download_workers     | 15                | Number of download workers for downloading files  |
+----------------------+-------------------+---------------------------------------------------+
| timestamp_format     | %Y-%m-%dT%H:%M:%S | Timestamp strftime format                         |
+----------------------+-------------------+---------------------------------------------------+

Questions, Support & Discussion
-------------------------------

webexteamsarchiver_ is a *community developed* and *community supported* project. Feedback, thoughts, questions, issues can be submitted using the issues_ page.

Contribution
------------

webexteamsarchiver_ is a *community developed* project. Code contributions are welcome via PRs!

*Copyright (c) 2018-2019 Cisco and/or its affiliates.*


.. _webexteamsarchiver: https://github.com/CiscoDevNet/webex-teams-archiver
.. _issues: https://github.com/CiscoDevNet/webex-teams-archiver/issues
.. _workaround: https://github.com/CiscoDevNet/webexteamssdk/issues/70
