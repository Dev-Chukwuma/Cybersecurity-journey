# Module 03 — Getting Data into Splunk

## Objective

Move from searching Splunk's own internal logs to bringing in my own data. This module covers adding data, data inputs, uploading log files, monitoring files, how ingestion works, and how to verify that ingested events are correct.

## Adding Data

Adding data means getting logs into Splunk so they can be searched and analyzed. Splunk offers several ways to do this: uploading a file, monitoring a file or folder, and receiving data from forwarders or network inputs. This module focuses on uploading and monitoring.

## Data Inputs

A data input tells Splunk where to get data and how to read it. I explored them under Settings, then Data, then Data inputs. The types I saw included:

- Local Event Log Collection: reads the Windows Event Logs on the local machine. Useful later for Windows security log analysis.
- Remote Event Log Collection: the same, but pulling logs from other Windows machines on a network.
- Files and Directories: Splunk watches a file or folder and reads new lines as they are written. The page showed 19 existing monitors. These are Splunk's own log files, which is where the internal data I searched in earlier modules came from.

Other common input types are TCP and UDP network inputs, which receive data such as syslog from firewalls and routers, the HTTP Event Collector, where applications send events over HTTP, and scripts, which Splunk runs on a schedule and indexes the output of.

## Uploading Log Files

Uploading is the simplest way to get data in. Splunk reads the file once and indexes it. It is best for one-off analysis, such as a log file handed over after an incident. It does not watch the file for new lines.

Hands-on: I created a small SSH-style authentication log called auth_sample.log with 6 lines. It contains repeated failed logins for the admin and root accounts from one internal IP, a successful login for a normal user, a failed login from an external IP, and a successful admin login from the first IP. This is the kind of pattern that detections are built on later in the roadmap, so the file will be reused.

Steps I followed:

- Opened the Add Data page and chose Upload.
- Selected auth_sample.log and moved to the Set Source Type page.
- Set the source type, saved it under a new name, and left the host and index settings on their defaults.
- Reviewed and submitted, then searched for the file's source over all time.

## What Went Wrong, and What I Learned

My first attempt used the linux_secure source type, and the preview went blank. The cause was a timestamp mismatch. That source type expects timestamps like Oct 7 09:15:02, while my file used 2026-10-07 09:15:02. Splunk could not parse the events, so nothing displayed.

The fix was to save the format as a new custom source type called auth_sample and upload again. After that, all 6 events were indexed with correct timestamps.

Lesson: the sourcetype controls how Splunk parses data. A wrong sourcetype produces wrong event boundaries or wrong timestamps, and wrong timestamps are especially dangerous in security work because they put events in the wrong order during an investigation.

## Monitoring Files

Monitoring tells Splunk to watch a file or folder and index new lines as they are written, without repeated uploads. It is how real log collection works, because systems such as web servers and firewalls keep writing logs continuously. It is configured under Settings, Data, Data inputs, Files and Directories. I reviewed this input type but did not create a monitor on my sample file, because that could create duplicate events.

## Understanding Ingestion

Every event takes the same path into Splunk:

- Input: Splunk reads the raw data from an upload, a monitored file, or a network port.
- Parsing: Splunk splits the data into events, finds the timestamp in each one, and applies the sourcetype.
- Indexing: the events are stored in an index, where they become searchable.

## Verifying Ingested Events

After ingesting any data, I check three things: the event count, the timestamps, and the metadata.

I searched for the uploaded file's source over all time and displayed a table of the time, host, source, sourcetype, and index fields. Results:

- Event count: 6, matching the 6 lines in the file.
- Timestamps: matched the times written in the file.
- Metadata: the host, source, sourcetype, and index fields were all populated correctly.

## Key Takeaways

- Uploading is for one-off files, and monitoring is for continuously written logs.
- Data inputs define where Splunk gets data and how it reads it.
- Ingestion is input, then parsing, then indexing.
- The sourcetype controls parsing, so choosing it correctly matters.
- Always verify count, timestamps, and metadata after ingesting data.

## Next Module

Module 04 — Searching in Splunk: basic searches, keywords, field-based searches, time ranges, search results, and saving searches.
