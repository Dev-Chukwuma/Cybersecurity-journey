# Module 04 — Searching in Splunk

## Objective

Learn how to ask Splunk questions and get reliable answers. This module covers basic searches, keywords, field-based searches, time ranges, search results, and saving searches. All practice was done on a sample SSH-style authentication log with 6 events, uploaded in Module 03.

## Basic Searches

A search is a question asked of the indexed data. The simplest form is a word or two typed into the search bar, and Splunk returns matching events, newest first. A search can also limit where it looks. I used the source of my sample file with a wildcard in front of the file name, so it works without typing the full file path.

Security example: after a suspected break-in, an analyst's first move is often to type a username or IP address into the search bar and see every event that mentions it.

## Troubleshooting: Why Every Search Returned Zero

My first searches returned zero events, even though the same data had been found earlier. I ruled out typing errors, the index, and the data itself. The cause was the time picker, which said All time (real-time) instead of plain All time.

A real-time search only shows events that arrive while it is running. My events were timestamped two days earlier, so they could never appear. The giveaway was in the browser address bar, where the earliest value was set to rt.

Fix: choose the plain All time preset, not the entry in the Real-time column.

Lesson: a wrong time range can make evidence look like it does not exist. Checking the time picker is the first thing to do when a search that should return results returns none.

## Keywords

Keywords match anywhere in the raw text of an event. They are not case-sensitive, and several keywords in one search mean AND, so an event must contain all of them.

Results on my sample log:

- The word failed returned 4 events out of 6.
- Failed with admin returned 3 events: two from one internal IP and one from an external IP.
- Failed with root returned 1 event.

## Field-Based Searches

A field search looks at one specific field, written as the field name, an equals sign, and a value. It is more precise than a keyword, because it only matches events whose field holds that value, not events that merely mention it in the text. Field names are case-sensitive, and field searches can be combined with keywords.

Results on my sample log:

- Searching by the sourcetype I created returned all 6 events.
- Adding the keyword accepted returned 2 events.
- Adding a host value I had assumed returned 0 events.

The zero was a useful mistake. The events carried a different host value than I assumed, and a field search only matches the exact value. I clicked the host field in the sidebar to see the real value, searched again with it, and got all 6 events.

Lesson: check a field's real values before filtering on it.

## Time Ranges

Every search only looks inside a time window. The options are:

- Presets such as Last 15 minutes or Last 7 days. These are relative, so the window moves with the clock.
- Date range: exact start and end dates, which gives repeatable results and is the right choice for documenting an incident.
- Real-time: only shows events arriving right now, and should be avoided for investigating past activity.
- A narrower window searches less data and returns faster.

Results for my sample log, whose events are from October 7, searched on October 9:

- Last 24 hours returned 0 events, because the events fall outside the window.
- Last 7 days returned 6 events.
- A date range of October 7 only returned 6 events.

## Search Results

The results area offers several views of the same search:

- Events tab: the raw events, newest first.
- Patterns tab: groups similar events together.
- Statistics tab: results as a table. It stays empty until a search produces a table, which commands introduced in the next module do.
- Visualization tab: charts of that table.
- Timeline: shows how many events occurred over time, and clicking a bar narrows the results to that period.
- Fields sidebar: shows each field's values and counts, and clicking a value adds it to the search.

Hands-on: after I clicked Top values on the source field, Splunk ran a small report, and the Statistics and Visualization tabs became active because the search now produced a table.

## Saving Searches

A search that will be repeated can be saved instead of retyped, using Save As at the top right of the search page. The two options used most are:

- Report: a saved search that can be rerun any time from the Reports menu.
- Alert: a saved search that runs on a schedule and triggers when a condition is met. Alerts are covered in Module 22.

Security example: a SOC analyst saves a search for failed logins in the last 24 hours as a report and opens it every morning instead of rebuilding it.

Hands-on: I searched my sample log for failed events over all time, saved it as a report titled Failed Logins - auth_sample, and confirmed it appeared in the Reports list.

## Key Takeaways

- Always check the time range first. A wrong or real-time range can hide evidence that exists.
- Keywords search the whole raw text, and field searches match one field exactly.
- Check a field's real values in the sidebar before filtering on it.
- Use a fixed date range when results need to be repeatable.
- The Statistics and Visualization tabs need a search that produces a table.
- Save searches you will repeat as reports.

## Next Module

Module 05 — SPL Fundamentals: the search, table, fields, sort, dedup, and stats commands.
