# Raspberry Pi Kubernetes Cluster

## Overview

Ansible roles/playbooks to setup and configure a Raspberry Pi based Kubernetes cluster.

## Tech Stack

### Hardware

- Four Raspberry Pi 4B 8 GB boards
- Pimoroni Heatsinks
- Four 32 GB Class 10 SD Cards
- Cloudlet cluster case
- Netgear 8 port gigabit switch
- 250 GB SSD w/ Sata to USB cable

### Software

- Ubuntu 20.04.1 LTS Server, ARM64
- Kubernetes
- Jenkins

## Setup

### Initial Setup and Physical Assembly 

1. Download Ubuntu server image and flash SD cards using [balenaEtcher](https://www.balena.io/etcher/)
2. Install SD cards and assemble the cluster.
3. Connect cluster switch to router. Alternatively you can setup wifi at this stage.
4. Boot Pi's one at a time for initial setup:
  - Provide ubuntu user password.
  - Change hostname in /etc/hostname.
  - Reboot and confirm hostname changed

## Server Naming Convention

pdl-kube-01
pdl-jenkins-01

[v|p] - virtual | physical
[d|q|u|p] - dev | qa | uat | prod
[l|w|m] - linux | windows | macOS
[function name] - short functional description of device
[##] - node number

## Ansible Notes
Shutting down cluster:

    ansible all -m shell -a "sleep 3s; shutdown -h now" -b -B 60 -P 0 -u ubuntu

