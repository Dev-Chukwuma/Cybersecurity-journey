# Module 08 — Time-Based Analysis

## Objective

Learn to analyze activity across time using timechart, bin, earliest, and latest. The practice dataset is the lab file I created in the previous module, auth_lab.csv. It has 20 authentication events with timestamp, user, src_ip, action, and host fields, and it is a simulated dataset, not data from a real incident.

## Why Time Matters

In security work, when something happened is often as important as what happened. Eleven failed logins spread across a day look harmless. The same eleven inside a few seconds look like an attack. Time-based commands turn a list of events into a shape, and spikes are the shape detections are built on.

## timechart

The timechart command counts events over time and produces one row per time bucket. It handles the bucketing automatically, and it can split the counts by a field, so each value gets its own column. It is the quickest way to see a spike. Because the result is a table, it also appears in the Visualization tab as a chart.

Hands-on: I ran timechart over the lab data with a span of one hour, split by action. Failed and success events appeared as separate columns, one row per hour.

## bin

The bin command places each event's time into a bucket of a chosen size, such as one hour, without producing the final table itself. Stats can then count per bucket. This is the manual version of what timechart does automatically, and it is useful when the counts need to be combined with other statistics commands.

Hands-on: I filtered the lab data to failed events, binned the time into one-hour buckets, and counted per bucket.

Results:

- 9 AM hour: 7 failed logins. This is the spike.
- 10 AM hour: 1
- 11 AM hour: 2
- 3 PM hour: 1
- Every other hour: 0
- Total failed logins: 11

The 7 failures in the 9 AM hour are the same activity from a single source address that the statistics module identified. All seven fall between 9:15:02 and 9:15:20, which is a burst of 18 seconds. Seen on a timeline, it is one tall bar in an otherwise flat day.

## earliest and latest

The earliest and latest options set the time window inside the search itself. They override the time picker, so the window is written down with the query and the results are repeatable. This matters for documentation, because a picker setting is invisible when someone else reads the search.

There are two styles:

- Relative: a negative number with a unit, such as 24 hours ago, with latest set to now.
- Exact: a date and time in month, day, year, hour, minute, second format.

Security example: an alert fired at 9:15, so the analyst searches only 9:00 to 10:00 instead of scrolling through a whole day.

Results on the lab dataset:

- Searching the exact window from 9:00 to 10:00 on the day of the events returned 8 events: the 7 failed logins plus a successful admin login at 9:16:02.
- Counting only failed events in the same window returned 7.
- A relative window of the last 24 hours returned 0, because the lab events are older than that.

The successful admin login one minute after the burst of failures is worth noticing. A burst of failures followed by a success is the pattern an account-compromise investigation looks for, and it is covered in a later module.

## Key Takeaways

- Timechart counts events per time bucket and makes spikes visible.
- Bin buckets timestamps by hand so other statistics commands can use them.
- Earliest and latest write the time window into the query and override the time picker.
- A spread-out count can look harmless while the same count in a short window is an attack.
- Always write the time window into searches that will be documented or reused.

## Next Module

Module 09 — Data Transformation: eval, rename, fields, table, and sort.
