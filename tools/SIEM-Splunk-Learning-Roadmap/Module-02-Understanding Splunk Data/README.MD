# Module 02 — Understanding Splunk Data

## Objective

Understand how Splunk organizes data, so that later searches, detections, and investigations make sense. This module covers events, fields, timestamps, hosts, sources, sourcetypes, indexes, and event metadata.

## Events

An event is a single record of something that happened, stored as one row in Splunk. Usually it is one line from a log file: a failed login, a web request, or a service restart. Splunk keeps the original raw text of every event unchanged. Fields and timestamps are extracted from, or attached to, that raw text.

Hands-on: I searched Splunk's own internal logs for the last 15 minutes and expanded an event to see its raw text and the fields listed under it.

## Fields

A field is a name and value pair that describes part of an event, such as method equals GET or host equals my machine name. Fields allow precise searching, for example showing only events where the method is POST.

There are two kinds:

- Default fields: attached to every event when it is indexed. Host, source, and sourcetype are the main ones.
- Extracted fields: pulled out of the event content. Examples I saw were bytes, clientip, method, file, and referrer. Different log types produce different extracted fields.

Security example: in a failed login log, useful fields would be the username, the source IP, and the result. With those as fields, failed logins can be counted per IP instead of reading raw lines.

## Timestamps

Every event has a timestamp stored in the _time field. It powers the timeline and the time range picker. In security work, investigations are mostly about order: failed logins, then a successful login, then a suspicious command. If timestamps are wrong, the story falls apart.

Hands-on: I compared the time inside the raw event text with the _time field. They represent the same moment and differ only in format and time zone display. A difference of several hours would point to a time zone setting issue, which is worth catching because it can put events in the wrong order.

## Hosts

The host field identifies which machine an event came from. In a company with hundreds of computers sending logs, host is how you filter down to one machine, or find which machine is behaving strangely. If an alert fires for repeated failed logins, host shows which server is being attacked.

Hands-on: in my lab, host has a single value, my own computer, because everything runs on one machine.

## Sources

The source field identifies where the data came from, usually a file path or input name. Host answers which machine, and source answers which file or input on that machine.

Hands-on: the source field showed 14 values. The top three were metrics.log at about 63.7 percent, health.log at about 13.4 percent, and a postgres stdout log at about 5.8 percent. They are different files on the same host.

## Sourcetypes

The sourcetype field tells Splunk what format the data is in. It is how Splunk knows how to find the timestamp, split data into events, and extract fields. Many sources can share one sourcetype.

Hands-on: splunkd made up about 80 percent of internal events, and splunkd_ui_access made up about 5 percent. Filtering with sourcetype equals splunkd_ui_access cut the results from thousands of events down to a few hundred, and the field sidebar then showed a single sourcetype value. New fields appeared that were specific to web requests, including clientip, method, and bytes. The clientip was the loopback address, because I was the one using Splunk Web.

Two things I learned along the way:

- Quotes around a value do not change the result. Searching sourcetype equals splunkd_ui_access gives the same events as the quoted version. Quotes only matter when a value contains spaces or special characters.
- A search over the last 15 minutes uses a moving window, so rerunning it later can return a higher count. Every page opened in Splunk Web creates a new event. Using a fixed time range gives repeatable counts.

## Indexes

An index is where Splunk stores data. It works like a folder, so different kinds of data can be kept separate and searched separately. A company might keep firewall logs in one index and Windows logs in another, so a search on the Windows index only looks at Windows data.

Hands-on: under Settings, then Data, then Indexes, I found built-in indexes including audit and config tracker. The audit index records activity inside Splunk, and the config tracker index records configuration changes. Indexes whose names start with an underscore, such as _internal, are Splunk's own.

## Event Metadata

Event metadata is information about an event, as opposed to the event content. It includes host, source, sourcetype, index, _time, and _raw, which holds the original unchanged log text. Fields starting with an underscore are Splunk's internal fields. Metadata helps answer which machine, which log file, and when, before the event itself is even read.

Hands-on: I searched the internal index for one event of the web access sourcetype and expanded it. The index was _internal, the linecount was 1, and _time was 2026-10-07 21:29:02.695 with a plus one hour offset.

## Key Takeaways

- Events are the raw records, and fields make them searchable.
- Host, source, and sourcetype describe where an event came from and what format it is in.
- Narrowing a search by sourcetype is one of the fastest ways to cut noise.
- Timestamps decide the order of events, so time zones matter.
- Indexes keep different data separate.

## Next Module

Module 03 — Getting Data into Splunk: adding data, uploading log files, monitoring files, data inputs, understanding ingestion, and verifying ingested events.
