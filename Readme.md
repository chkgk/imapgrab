# IMAP Grab
## About
This is a fork of the original [IMAP Grab](https://sourceforge.net/p/imapgrab/wiki/Home/) written by [Daniel Roesler (Diafygi)](https://sourceforge.net/u/diafygi/profile/) for Python 2. The fork does not include the GUI but works with Python 3.  

ImapGrab is a cli and gui program (written in Python) that allows you to log into an IMAP server, list mailboxes, and download selected mailboxes to mbox or maildir files. It requires getmail 4.8.2 or higher. 

The basic functions of listing and downloading have been tested.
No further development or maintenance is planned.
The repository includes the cli code of the original 0.1.4 release for Python 2 as well as a version for Python 3 modified by me. I've set the version number to 0.2.0. 

The code has been released under the [GPLv2](http://www.gnu.org/licenses/gpl-2.0.html) license.

The following is copied and adapted from the -now abandoned- [original project](https://sourceforge.net/p/imapgrab/wiki/Home/) on sourceforge

## Description
```imapgrab.py``` is a command line interface (CLI) that allows you to log into an IMAP server and download selected mailboxes (i.e. folders/labels) to mbox files or maildir folders. You can also list the mailboxes on that server. It is basically a wrapper for getmail (a mail downloading program). When done downloading selected mailboxes, you end up with one .mbox file per mailbox or one set of maildir folders per mailbox.

## Features
- GUI for easy listing/downloading
- Download in Mbox or Maildir formats
- SSL connections possible
- multiple select mailboxes may be downloaded in one command
- all available folders may be downloaded
- folders may be excepted when above is enabled
- when mbox file is detected, only new mail is downloaded, but this can be changed (with -a)
- special option to except Google Mail (Gmail) folders from download
- GUI preset for Gmail's server settings

## Dependancies
getmail 4.8.2 or higher (tested with 5.14)
python 3.5 or higher (tested with 3.7.7)

## CLI Usage
```imapgrab [-ldaSv] [-s] SERVER [-P] PORT [-u] USERNAME [-p] PASSWORD [-m] "BOX1,BOX2,..." [-f] DIRECTORY```

## Possible arguments
- ```--list -l```
  - List the mailboxes available for download
- ```--download -d```
  - Download mailboxes to separate mbox files
- ```--mbox -B```
  - Download into [[http://en.wikipedia.org/wiki/Mbox|Mbox]] format (optional, default)
- ```--maildir -M```
  - Download into [[http://en.wikipedia.org/wiki/Maildir|Maildir]] format (optional)
- ```--all -a```
  - Force download all mail in a mailbox (optional)
- ```--ssl -S```
  - Use SSL connection (optional)
- ```--server -s```
  - IP or domain of server (required)
- ```--port -P```
  - Port of server (optional)
- ```--username -u```
  - Username for account (required)
- ```--password -p```
  - Password for account (required)
- ```--mailboxes -m```
  - Comma separated list of mailboxes to download (i.e. "Box1, Box2, Box3") ({,} for non-separating commas) ("_ALL_" for all mailboxes) ("_ALL_, -Box1" to except Box1 from ALL) ("_ALL_, -_Gmail_" to except Gmail* and Google Mail* folders) (required for -d)
- ```--folder -f```
  - Path to folder (optional, creates imapgrab folder in current directory as default)
- ```--localuser -L```
  - User that writes to the mailboxes (use only when involking imapgrab as root)
- ```--quiet -q```
  - Don't display any output
- ```--verbose -v```
  - Verbose output
- ```--debug```
  - Print debug output
- ```--version```
  - Print version
- ```--about```
  - Display detailed info
- ```--help -h```
  - Print help with command options

## CLI Examples
- List available mailboxes
  - ```imapgrab -l -s imap.example.com -u username -p password```
- Download "box1" and "box2" from server imap.example.com (save "box1.mbox" and "box2.mbox")
  - ```imapgrab -d -s imap.example.com -u username -p password -m "box1, box2"```
- Download all mailboxes except "box3"
  - ```imapgrab -d -s imap.example.com -u username -p password -m "_ALL_, -box3"```
- Download all Gmail custom labels and INBOX (none of the Gmail* or Google Mail* mailboxes)
  - ```imapgrab -d -S -s imap.gmail.com -u username -p password -m "_ALL_, -_Gmail_"```
- Download Gmail label "receipts"
  - ```imapgrab -d -S -s imap.gmail.com -u username -p password -m "receipts"```
  