# Narrative CLI

## Introduction and Setup

This is a simple Bash script that allows you to list, download, and
delete photos and videos from your [Narrative](http://getnarrative.com)
[timeline](https://narrativeapp.com/timeline/).

All you need is the `narrative` script.  Just put it somewhere in your
`$PATH`.  To get started, do the following:

1. Log into your timeline (https://narrativeapp.com/timeline/) with
   your browser.  You want to have the *Web Inspector* up so that you
   can see the network traffic.
2. Filter the network requests to show XHR request.
3. Click on one of the requests, then examine the *Request Headers*.

You should see an *Authorization* header that looks something like
this:

**Header** | **Value**
---- | ----
`Authorization` | Bearer *TOKEN*

Copy the *TOKEN* value and save it in a file in your `$HOME` directory
called `.narrativerc`.  You want to make sure there are no extra lines
or any leading or trailing whitespace.

## Basic Command Usage

Run the command with `-h` or `--help` to get instructions:

    $ ./narrative --help

./narrative, Version 0.1.0, 20160530

	Usage: This script will list or delete moments|photos|videos
		   or get (download) photos|videos from the Narrative
		   server.

		   When getting photos|videos, they will be stored
		   in the current directory into a new folder
		   with the following name: 'yyyy-mm-dd (Day)'.
		   Example: '2016-05-29 (Sunday)'.

	Arguments:

	  -d|--date   <date> - filter operations to 
				  moments|photos|videos on the specified date.
				  The default is 'today'.  <date>, if specified, 
				  must be of the following format: 'yyyy-mm-dd'.
	  -f|--from   <from-time> - filter operations 
				  to moments|photos|videos taken on/after the 
				  specified time. If not specified,
				  defaults to the selected date at '00:00:00'.
				  If specified, must be of the form 'hh:mm:ss'
	  -t|--to     <to-time> - filter operations
				  to moments|photos|videos taken on/before the
				  specified time. If not specified,
				  defaults to the selected date at '23:59:59'.
				  If specified, must be of the form 'hh:mm:ss'.
	  -g|--get    Get (download) photos|videos from
				  Narrative server
	  -d|--delete Delete moments|photos|videos from Narrative server
	  -l|--list   List moments|photos|videos on the Narrative server
				  This is the default operation.
	  -i|--items  <item-list> moments,photos,videos (default=moments)
				  what to list|get|delete
				  Can be a comma-separated list. Note: 'moments' can
				  only be listed or deleted.
	  -m|--moment <moment-id> - When getting, listing, or 
				  deleting photos, this filters by all
				  photos contained in the specified moment.
				  Valid only with '--items photos'.
				  When deleting moments, this specifies the moment
				  to delete.

## What's Working

Not all of the command options are currently implemented.  You can do
the following:

* List *moments*, *photos*, and *videos*
* Get (download) *photos* and *videos*
* Delete (from the cloud) *photos* and *videos*

Currently none of the other filtering operations work.  Right now all
of the listing, getting, and deleting operations work on *all*
entities of the specified type or types, so use at your own risk.

Listing and getting (downloading) are safe operations and do not
remove anything from the cloud.  Photos and videos that are downloaded
are stored in your current directory, in a folder whose name is based
on the locale time that your photos/videos were taken/started.  The
name of the local folder that is created is `yyyy-mm-dd (day)`; for
example, `2016-05-30 (Monday)`. No grouping by *moments* is done.

I wrote this script for my own personal use so that I could download
all of my info from the Narrative server first thing in the morning
after letting my *Narrative Clip 2* charge and upload content
overnight.  I will update this document as additional changes are made.


