# Puppet module: apt_dater

[![Puppet Forge](http://img.shields.io/puppetforge/v/gnubilafrance/apt_dater.svg)](https://forge.puppetlabs.com/gnubilafrance/apt_dater)
[![Build Status](https://travis-ci.org/gnubila-france/puppet-apt_dater.png?branch=master)](https://travis-ci.org/gnubila-france/puppet-apt_dater)

Puppet module to manage apt_dater.

Code extracted from example42/puppet-apt, check it if needed a full apt ecosystem management module.

Originally written by Boian Mihailov - boian.mihailov@gmail.com
Added features by Marco Bonetti
Adapted to Example42 NextGen layout by Alessandro Franceschi
Features removed by Baptiste Grenier.

Yum-based update manager taken from https://github.com/DE-IBH/apt-dater-host/

Licence: Apache2

## DESCRIPTION

This module installs and manages [apt-dater](http://www.ibh.de/apt-dater/)
to manage centrally controlled updates via ssh on deb-based and yum-based
systems.

All the variables used in this module are defined in the apt_dater::params class
(File: $MODULEPATH/apt_dater/manifests/params.pp).

## USAGE

- Configure a host to be controlled by apt-dater

  class { 'apt_dater':
    customer     => 'ACME Corp.',
    ssh_key_type => 'ssh-rsa',
    ssh_key      => template('site/apt-dater.pub.key');
  }

- Configure an apt-dater controller (no self-management) for root

  class { 'apt_dater':
    role            => 'manager',
    manager_ssh_key => template('site/apt-dater.priv.key');
  }
