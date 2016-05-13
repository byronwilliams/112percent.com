+++
author = ""
date = "2016-02-16T21:51:51Z"
description = ""
tags = []
title = "scaleway security groups"
type = "post"
draft = true
+++

Scaleway are one my favourite hosting providers, once they open up some more datacentres I'll be super impressed. Their
firewall for their security groups is stateless.

This means that if you wish to restrict stateful inbound traffic such as HTTP you'll need to use `iptables` on your
server, rather than the security group.

![Scaleway firewall rules](/pictures/screenshot-cloud.scaleway.com_2016-02-16_21-52-29.png "Scaleway firewall rules")

Rule #7 will break any outbound stateful TCP traffic.

## Why?

https://community.scaleway.com/t/solved-apt-get-and-security-group/920
