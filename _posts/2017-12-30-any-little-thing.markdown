---
layout: post
title:  "Idea sketch of the project Any Little Thing"
date:   2017-12-30 14:05:00 +0900
---

### Goal
* Record any types of log easily and quickly
* Check patterns of logs

### Keys to meet the goal
* Basically, text-based input interaction with auto completion at the mobile device
* Open to adapt logs from any kinds of sources and event
* Flexible representation of types and category
* Pattern analysis based on log and category patterns and associations
* Visualization tools with various filters to see periodic patterns
* Easy access to the logs from web

### Scenario
* When the baby goes to sleep and be awaken
* When the baby eat and how much

### Data basic
A log has
 * (M) name
 * (M) start time
 * (O) duration
 * (O) quantity
 * (O) quantity unit

A tag has
 * (M) name

A log has zero or more tags
A tag has zero or more logs
