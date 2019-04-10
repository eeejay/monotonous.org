---
id: 409
title: My Perfect Data Backup Solution
date: 2010-08-23T12:33:37+00:00
author: Eitan
layout: post
guid: http://monotonous.org/?p=409
permalink: /2010/08/23/my-perfect-data-backup-solution/
original_post_id:
  - "409"
categories:
  - Software
  - Technology
---
This might already exist, and I might just be uninformed. When I look for a backup tool that will do what I need, usually I get a scoff in the form of &#8220;rsync, dummy&#8221;. My computing equipment typically consists of a laptop that I use everywhere, and sometimes even at home, a headless computer at home that I use mostly for music and movies (with a projector), and several external hard drives with varying capacities.  
These are my requirements for an awesome backup solution:

  * When I connect to my home wireless network I want it to automatically start syncing and backing up data to the headless computer.
  * I don&#8217;t want it to saturate the network or be too taxing on disk I/O, so that regular computing tasks could be resumed unhindered.
  * I want it to be resumable, so if I leave the house while it was syncing some huge file, it will just continue where it left off when I get back home.
  * A visual status indication of whether a sync is taking place. A way to pause it.
  * I want it to have 3 different kinds of backup modes for 3 different types of data:
Home folder
:   Snapshot based backups, that allows me to easily roll back and view previous revisions of my home directory.

Media
:   Accumulative backup. See what new music, photos or videos I have on my laptop, and copy them to the backup storage. This mode never deletes media that existed in previous syncs. I should be able to download or create new media, and have it stored on the high capacity storage at home, and only carry with me the media that I am currently consuming (I really don&#8217;t want to clutter my laptop disk with The Godfather trilogy, but I might want to take it with me on a flight).

Virtual machines
:   I usually have a small collection of virtual machines on my laptop. They are by far the largest single type of data I have on my machine. Since they support virtual disk snapshots natively, I don&#8217;t really care for revisioning like the home folder, virtual machine disks could clobber older versions of themselves on the backup storage.

There are countless backup solutions (read: rsync wrappers) out there. Do any of them answer those needs in a user-friendly way?