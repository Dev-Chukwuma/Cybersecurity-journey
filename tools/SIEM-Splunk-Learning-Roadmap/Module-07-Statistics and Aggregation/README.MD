# Module 07 — Statistics and Aggregation

## Objective

Learn to use SPL statistics to identify patterns in security data: stats count, stats count by, stats values, and stats dc. The practice dataset is a lab file I created myself, auth_lab.csv. It has 20 authentication events with timestamp, user, src_ip, action, and host fields, and it is a simulated dataset, not data from a real incident.

## Why Statistics Matter

Reading logs line by line does not scale. Statistics turns many events into a few rows that show where to look. One number such as 11 failed logins means little by itself. Knowing that most of them came from a single address is what makes it useful.

## Setting Up the Lab Dataset

I wrote a small CSV file and uploaded it through Add Data. Splunk detected the csv source type automatically and extracted the column names as searchable fields, which is why this file supports field-based statistics that the earlier plain-text sample could not. A count over the file's source returned 20 events, matching the file.

## stats count

The stats count command returns the number of events as a single number. The result column can be renamed with the AS keyword, which makes tables easier to read. For example, a daily report might need a column called failed_logins instead of count.

Results on my first sample log:

- Counting failed events and naming the column failed_logins returned 4.
- Counting all events and naming the column total_events returned 6.

## stats count by

Adding a by clause counts events separately for each value of a field, giving one row per value. This is how patterns appear. Adding a sort in descending order on the count puts the biggest group first.

Results on the lab dataset:

- Counting by action returned two rows, with 11 failed events.
- Counting failed events by source IP and sorting by count returned three rows. The top row was 203.0.113.9 with 7 failures, which is 7 of the 11 failed logins from a single address.

## stats values

The values function lists the distinct values of a field, grouped however the by clause says. Count says how many, and values says which ones. The address with 7 failures raises an obvious question, which is which accounts it was trying, and values answers it in one cell.

Result: listing the users for failed events by source IP showed that 203.0.113.9 tried the accounts admin, root, and test.

## stats dc

The dc function means distinct count. It counts how many different values a field has, where count counts events. It answers the same question as values, but as a number.

Why this matters in security: one address failing seven times against a single account might be a forgotten password, while one address failing against several different accounts looks like password guessing. Count alone cannot tell the two apart. Distinct count can.

Result: counting failures and distinct users by source IP showed 7 failures across 3 distinct accounts for 203.0.113.9, which matches the list from the values search.

## A Note on Verifying Results

During the lesson I read some results back from the screen as row counts instead of values. For example, a count query always returns a single row, so the number of rows is not the same as the count value. When documenting results, always read the actual values in the Statistics tab.

## Key Takeaways

- Stats count answers how many, and stats count by splits it per value.
- Sorting descending on count puts the biggest group first, which is where a pattern shows.
- Values lists which distinct values exist, and dc says how many.
- Combining count and dc separates a forgotten password from a password-guessing pattern.
- Lab datasets are a legitimate way to practice, and should be labeled as simulated data.

## Next Module

Module 08 — Time-Based Analysis: timechart, bin, earliest, and latest.
