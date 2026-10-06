# Module 01 — Introduction to Splunk

## Objective

Build a foundation for the rest of the roadmap by understanding what Splunk is, what a SIEM does, how Splunk is structured, and how to move around the Splunk Web interface.

## What is Splunk?

Splunk is a platform that collects machine data (logs) from many sources, indexes it, and makes it searchable in seconds. Almost every system produces logs: servers, laptops, firewalls, applications. On their own these logs are scattered and hard to read. Splunk brings them into one place so they can be searched, visualized, and acted on.

## What is a SIEM?

SIEM stands for Security Information and Event Management. It is the use of a platform like Splunk for security work. Logs from many systems are collected centrally so analysts can detect attacks, investigate incidents, and raise alerts.

Example: an attacker is guessing passwords on a server, and each attempt creates a failed login log. Checking that server by hand makes the pattern easy to miss. In a SIEM, a single search can show hundreds of failed logins from one IP address in a couple of minutes.

## Why Organizations Use SIEM Platforms

- Centralized visibility: logs from servers, endpoints, firewalls, and applications are searchable in one place instead of logging into each system.
- Faster detection: attacks often appear as patterns across many logs, and a SIEM can alert on those patterns quickly.
- Investigation: analysts can trace what happened, when it happened, and where it came from.
- Compliance: many standards require organizations to collect and retain logs and show that they monitor them.
- Incident response: a searchable record of events gives responders the evidence they need to scope and contain an incident.

## Splunk Architecture and Components

Splunk has three main components:

- Forwarder: runs on the machine producing the logs and sends the data to Splunk.
- Indexer: receives the data, parses it, and stores it in indexes so it can be searched quickly.
- Search Head: the web interface where searches are run and dashboards and alerts are built.

In a company these are usually separate machines. In my lab, all three run together in one standalone installation on a single computer, which is enough for learning.

## Exploring the Splunk Interface

I opened Splunk Web in the browser at localhost on port 8000 and signed in with the admin account created during installation.

Home page: the Apps sidebar on the left lists the installed apps, and the main panel shows the home dashboard.

Search and Reporting app: the top navigation bar contains these menus:

- Search: where searches are written and run.
- Analytics: a point-and-click way to build searches and charts.
- Datasets: the data tables and lookups available to search.
- Reports: saved searches that can be rerun.
- Alerts: searches that run on a schedule and trigger when a condition is met.
- Dashboards: panels of saved searches and charts.

Settings menu: the Knowledge section holds saved searches, data models, and tags, which make data easier to search and organize. The Data section holds data inputs, forwarding and receiving, and indexes, which are used when bringing data into Splunk.

## Hands-On: First Search

I ran a first search against Splunk's own internal logs, which always contain events and are safe to explore. The search was index equals _internal, with the time range set to the last 15 minutes.

Result: 3,116 events found.

What I observed:

- Events: each row is a single log entry. Splunk breaks raw data into events.
- Timeline: the bar above the results shows how many events occurred over time. Spikes can point to unusual activity, which matters in security work.
- Default fields: host, source, and sourcetype appear in the fields sidebar. Host is the machine that produced the event, source is the file or input it came from, and sourcetype is the format of the data. Every event carries all three.

## Key Takeaways

- Splunk collects, indexes, and searches machine data.
- A SIEM applies that idea to security: centralize logs, detect threats, investigate incidents.
- Forwarders send data, indexers store it, and the search head is where analysts work.
- Every event has host, source, and sourcetype, which are explored properly in the next module.

## Next Module

Module 02 — Understanding Splunk Data: events, fields, timestamps, hosts, sources, sourcetypes, indexes, and event metadata.
