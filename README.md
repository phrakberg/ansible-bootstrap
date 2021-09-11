# Goofing off with Ansible

## Summary

For a work project I had to pick up Ansible.  I'm definitley a learn by doing (or breaing if you ask my wife), so this was just me learning the basic ideas behind the tool. I quickly decided to use this for easy user management of my Pi's and VM's.  This is a basic ansible setup I use with my pi4 to quickly add my user and some apps that I like to have.  It is not a comprehensive setup.

This does currently require you to already have a user with sudo and your SSH key to work properly

## WARNING!

The users playbook creates an `admins` group and then adds a rule so users in the group can use sudo without a password.  I'm fine with this setup as the pi isn't exposed to the internet.

***USE AT YOUR OWN RISK***

## Configuration

### Hosts File

The hosts file contains my basic inventory.  I have them categorized by the type of system.

### Ansible.cfg

This is a basic configuration file where you can set variables for both default and specific groups

## Playbooks

### Main.yml

This is just a simple playbook that imports my 2 main playbooks.  it easlily allows me to run them both with one command.

### App.yml

This playbook updates the system and installs a few apps I like to have as a baseline. I run this app first so the docker group is available when I add my user later.  It is currently only setup for my pi as most of my VM's are CentOS7 at the moment.  I will be updating this in the future.

### Users.yml

This playbook creates an admin group and sudo rules, and my primary user account and ssh public keys.