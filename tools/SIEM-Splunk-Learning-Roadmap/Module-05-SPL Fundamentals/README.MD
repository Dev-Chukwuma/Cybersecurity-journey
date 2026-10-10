# Module 05 — SPL Fundamentals

## Objective

Learn the foundations of Splunk's Search Processing Language (SPL): the search, table, fields, sort, dedup, and stats commands. All practice was done on a sample SSH-style authentication log with 6 events, uploaded in Module 03.

## How SPL Works

An SPL query is a chain of commands joined by the pipe symbol. Each command takes the results of the one before it and changes them, like an assembly line. A query can read as: find events, pick columns, then sort them. This pipeline idea is the foundation for every advanced query later in the roadmap.

## search

A search that starts with plain terms already has a search command at the front, even when it is not written. The command can also be used again after a pipe, to filter the results of an earlier step. These two searches do the same thing: searching the sourcetype with the keyword failed, and searching the sourcetype and then piping to search failed.

Results on my sample log:

- Searching for failed returned 4 events.
- Adding a second search command for admin returned 3 events, because each search filters the results of the step before it.

## table

The table command chooses which fields to show and displays them as columns, like a spreadsheet. Raw events are long and hard to scan, while a clean grid of time, host, and the raw line is easier to read. The pattern is the word table followed by field names separated by spaces.

Result: displaying the time, host, and raw fields produced 6 rows, and Splunk switched to the Statistics tab because the search now produced a table.

## fields

The fields command decides which fields to keep or remove, but it does not turn the results into a table. The search stays on the Events tab and the results are still shown as events. Keeping fields is done by listing them, and removing fields is done by putting a minus sign before the list.

The difference from table: table shapes what you see, while fields trims what is carried forward. Security logs can have dozens of fields, so dropping the ones you do not need keeps searches lighter and results easier to read.

Result: combining fields with table produced a clean 6-row table with only the host and source columns.

## sort

The sort command puts results in order. Splunk lists newest events first by default. Sorting by a field goes from smallest to largest, and putting a minus sign before the field reverses it. Sorting by time with the oldest first is how an investigator reads an incident as a story, from the first failed login to the final successful one.

Results on my sample log:

- Sorting oldest first put 9:15:02, the first failed login, at the top and 9:18:10 at the bottom.
- Sorting newest first flipped the order, with 9:18:10 at the top.
- Sort only changes the order of results and never removes any.

## dedup

The dedup command removes duplicates. For the field named, it keeps only the first event for each distinct value and drops the rest. Because Splunk lists newest events first by default, the event kept is the newest one. Security example: a log with thousands of events from only a few dozen IP addresses can be reduced to the unique addresses to review.

Results on my sample log:

- Deduplicating on host returned 1 row, because all 6 events share a single host.
- Deduplicating on the raw text and then counting returned 6, because every line differs by timestamp and port number, so there are no duplicates to remove.

A note on a confusing result: during the lesson I read the result of the raw-text dedup search as 2 rows, which did not match what the data should give. I could not reproduce that reading, and a counting query confirmed 6. The takeaway is to verify a surprising result with a counting query before trusting what the screen seems to show.

## stats

The stats command does math on events, such as counting, summing, and averaging. Instead of listing events, it gives a summary number, which is how an analyst answers how many. Using stats count counts all events, and adding a by clause counts separately for each value of a field. Security example: instead of reading thousands of login events, one counting query grouped by source IP can show that a single address has most of the failures.

Results on my sample log:

- Counting all events returned 6.
- Counting events containing failed returned 4.
- Counting by host returned 6 in a single row, since there is one host.
- Counting failed events by source returned 4.

The count appears in the Statistics tab, in a single-row table. A count query always returns one row when there is no by clause, so the row count is not the same as the count value.

## Key Takeaways

- SPL is a pipeline: each command works on the results of the one before it.
- Search filters, table shapes the display, and fields trims what is carried forward.
- Sort changes order only, and dedup removes duplicates based on a field.
- Stats turns events into numbers, and it is the starting point for detection work.
- When a result looks wrong, verify it with a counting query before trusting it.

## Next Module

Module 06 — Filtering Events: AND, OR, NOT, wildcards, exact matches, and field filtering.
