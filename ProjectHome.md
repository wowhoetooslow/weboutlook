Stuck with Microsoft Outlook for work e-mail? Want access to your raw e-mail messages from Outlook? Prefer to use your own e-mail client rather than the clumsy Outlook client? If so, weboutlook is for you.

weboutlook is a Python module that retrieves full, raw e-mails from Microsoft Outlook Web Access by screen scraping. It can do the following:

  * Log into a Microsoft Outlook Web Access account with a given username and password.
  * Retrieve all e-mail IDs from the first page of your Inbox.
  * Retrieve the full, raw source of the e-mail with a given ID.
  * Delete an e-mail with a given ID (technically, move it to the 'Deleted Items' folder).

Documentation / sample usage:

>>> from weboutlook import OutlookWebScraper

# Throws InvalidLogin exception for invalid username/password.
>>> s = OutlookWebScraper('https://webmaildomain.com', 'username', 'invalid password')
>>> s.login()
Traceback (most recent call last):
> ...
scraper.InvalidLogin

>>> s = OutlookWebScraper('https://webmaildomain.com', 'username', 'correct password')
>>> s.login()

# Display IDs of messages in the inbox.
>>> s.inbox()
['/Inbox/Hey%20there.EML', '/Inbox/test-3.EML']

# Display IDs of messages in the 'sent items' folder.
>>> s.get\_folder('sent items')
['/Sent%20Items/test-2.EML']

# Display the raw source of a particular message.
>>> print s.get\_message('/Inbox/Hey%20there.EML')
[...]

# Delete a message.
>>> s.delete\_message('/Inbox/Hey%20there.EML')

UPDATE, August 2010: I no longer am forced to use Microsoft Outlook, so I have no way of testing/improving this library. Greg Albrecht has branched the code here:
http://github.com/ampledata/weboutlook/tree/master/weboutlook/