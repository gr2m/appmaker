NudgePad
========

NudgePad let's you build websites in your browser. We are actively developing
NudgePad and are breaking things a little too much. For that we apologize, but
we want to get it right for version 1.0. A release date for version 1.0
has not yet been finalized, but will be sometime in 2013.

Try it
======

Try it now at http://nudgepad.com


What Can I Build with NudgePad?
===============================

- Clickable Prototypes
- Blogs
- CMS Sites
- Single Page Websites
- Personal Homepages
- White Boards
- Small Business Websites
- Mobile Sites
- FirefoxOS Apps
- Presentations
- Infographics
- Todo Lists
- AB Tests
- APIs
- eCards
- Forms
- Visualizations
- Experiments
- Simple Games
- Surveys
- eCommerce Stores
- MindMaps
- Memes

Who is NudgePad for?
====================

- Creatives who have lots of ideas for websites
- Designers who want to design in the browser
- Developers who want to collaborate with designers and users
- Novices who want to be able to make changes to their sites
- Students who want to build, share, and learn online
- Teachers who want an easy tool for creating lessons
- Organization leaders who want to enable more collaboration and sharing among their members
- Sys admins who want a better shared hosting tool

Live NudgePad Powered Sites
===========================

- Blog: http://breckyunits.com/
- Small Business Site: http://octaviachambliss.com/
- Book Site: http://generationatheistbook.com/
- Personal Homepage: http://benzulauf.com/

Requirements
============

Nudgepad currently works (occasionally) on Mac OS X and Ubuntu.

NudgePad requires node v0.8.23 (does NOT currently work reliably with
node v0.10.x due to some proxy/websocket issues).

It also requires mon, which can easily be installed like so:

    cd ~
    git clone https://github.com/visionmedia/mon.git
    cd mon
    sudo make install

Occasionally you'll need to update your environment's PATH variable to make
sure that the node_modules/.bin folder is included. For example, you may need
to add this to your .bash_profile or .bashrc:

    PATH=$PATH:~/node_modules/.bin

NudgePad consists of a control panel Express app running on port 3000, user
sites which run on ports 3001 - 8000, and an http-proxy app which sits in front
of all of those on port 80. You can access the control panel app by going to
http://localhost/, or if it's running on a production server by going to
http://YOURHOSTNAME/. The panel app let's you instantly create more sites
that have a domain name like *.localhost on localhost, or *.YOURHOSTNAME on a
production server. If you are not running on localhost, be sure to update the
hostname of your machine to match the machine's DNS name, and you'll want
to create a CNAME or A Record in your DNS to point *.YOURHOSTNAME to the
machine's IP or DNS.

Installing
==========

If you'd like to host Nudgepad on your owner server or development machine,
follow the steps below.

    npm install nudgepad
    np start
    # Go to http://YOUR_MACHINE_HOSTNAME

All the code for Nudgepad will be stored in the node_modules/nudgepad folder.
All user, temp, and log data will be written to /nudgepad/.

Installing Development Version
==============================

If you'd like to contribute to NudgePad development, follow these steps:

    cd ~
    git clone git@github.com:nudgepad/nudgepad.git
    cd nudgepad
    ./install.sh
    npd start
    # Go to http://localhost

Uninstalling
============

The following will remove the npm version:

    npm uninstall nudgepad

To remove the development version (and ALL user data) run:

    npd uninstall

Contributing
============

We encourage you to use NudgePad, create issues for bugs or ideas, contribute templates, and
of course contribute code!

NudgePad is moving to a completely modular architecture consisting of many high quality
open source modules and packages elegantly and reliably integrated together.

The three main components of NudgePad:

client
------

The frontend to NudgePad. This code does pretty much one thing: creates the /nudgepad single
page app which contains the whole interface of NudgePad. We have a lot of cleanup to do here.

We use libraries here such as jQuery, underscore, scraps, and Space, and a whole lot of
specific packages for UI and other components. If you think we could benefit from using
an open source package you wrote or know of, please let us know so we can add it (and
even better delete something from our codebase!).

To create something new for client from scratch, your code should:

- Be its own standalone repo
- Be usable outside of NudgePad
- Have a live website (a NudgePad site works great) where someone can play with it
- Have unit tests
- Be 1 JS file
- Be CamelCased
- Be Concise
- Be MIT licensed
- Expose 1 global object that begins with a Capital Letter.

server
------

Each NudgePad site is a Node.js process powered by Express. We are in the process
of cleaning up our files here to be more modular and offer a more consistent
API.

To create something new for client from scratch, your code should:

- Be its own standalone repo
- Be usable outside of NudgePad
- Have a live website (a NudgePad site works great) where someone can play with it
- Have unit tests
- Be 1 JS file
- Be CamelCased
- Be Concise
- Be MIT licensed
- Extend the NudgePad site in a conventional way

system
------

The code in system is responsible for creating new sites on the machine, load
balancing, proxying requests to sites, and offering tools to sysadmins for
managing a NudgePad server.

It's currently written mostly in BASH, but node scripts are welcome as well.


Build Status
============

[![Build Status](https://travis-ci.org/nudgepad/nudgepad.png?branch=master)](https://travis-ci.org/nudgepad/nudgepad)
