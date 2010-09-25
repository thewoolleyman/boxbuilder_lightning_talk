BOXBUILDER LIGHTNING TALK
=========================

WHY
---

* code must run on boxes (computers, systems, etc.)
* boxes must be built
* Your environment will rot, especially if you don't lock down versions.  Takes a lot of knowledge and *ongoing* time to *properly* provision and update boxes.
* heroku is great, until you want something they don't do (yet)
* Chef from Opscode is a Ruby DSL to declaratively define the desired state of a box - using "cookbooks", "recipes", "roles", etc.
* It is powerful and useful, but you need Ruby to run it
* But Ruby isn't preinstalled on most barebones distros (and if it is, it isn't the version you want)
* Boxbuilder uses RVM.  RVM is the best way to install Ruby

WHAT
----
* Boxbuilder automatically bootstraps a barebones OS with RVM and Chef, then runs your Chef cookbooks
* Single command line invocation
* Opinionated yet flexible, minimal configuration required (builds an 'example' box if no custom Chef cookbook is defined)
* Everything controlled with environment variables
* It is written in Bash
* Why Bash?!? Zero dependencies, cross platform, runs on any workstation with a shell, shuts up language bigots
* Lets the definitions for your systems live in source control and be completely repeatable (as long as you lock down versions of everything, packages, RVM, Chef itself)
* Simple "autoupdate" approach, automatically pulls all latest chef repos and configs when 'boxbuilder' executable is run again.
* It has tests!
* It has Continuous Integration!

* It can build:
  * A local box
  * A remote box
  * An Amazon EC2 AMI image from your Chef cookbooks (locally or remotely as well)

WOW
---
* Pie in the sky ideas:
  * Continuous Integration can include invoke Boxbuilder to automatically build an entire test environment, and test deployment of your green tag
  * Green tag of your entire environment
  * Minimize nasty surprises during deployment
  * Automatically create Amazon EC2 AMI images of your server roles, so they are instantly bootable
  * Everything is in source control, versioned, tagged, holistically consistent, completely repeatable...