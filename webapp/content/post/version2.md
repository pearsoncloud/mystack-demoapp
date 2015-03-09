+++
Categories = ["Development", "GoLang"]
Description = ""
Tags = ["Development", "golang"]
date = "2015-03-09T14:36:28+02:00"
menu = "main"
title = "Version 2"

+++

# Overview

This demo site is hosted on myStack. All the VMs were built and deployed with the application stack in about
5 minutes, using the marketplace Golang code, and Ansible. 

## Servers

This application is actually 2 web servers, hidden behind an HAProxy load balancer, a DB Server and a 
monitoring Nagios server.

## Requirements

To create these servers, you need just a very few things:
1 - The golang marketplace code
2 - A yaml (Yet Another Markup Language) file to define your VMs. It looks something like this:

vapps:
  - name: 'whatever-dude'
    vms:
      - name: 'webserver1'
        catalog_item: 'RHEL'
        hardware_config:
          memory: 2048
          cpu: 2
          disks:
            - size: 10240
              description: 'Extra disk 1'
        network:
          type: 'FE'       
        bootstrap:
          scriptname: bootstrap         
        metadata:
          role: webservers
 
3 - Another yaml file to define your firewall rules, and any pools of VMs and VIPs.
4 - An Ansible playbook, that layers on your application stack, and pulls down the software
from a VCS.

That's all folks.

