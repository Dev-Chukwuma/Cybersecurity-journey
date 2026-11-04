# Module 09 — Data Transformation

## Objective

Learn to create useful fields and organize investigation results using eval, rename, fields, table, and sort. The practice dataset is the lab file I created earlier, auth_lab.csv. It has 20 authentication events with timestamp, user, src_ip, action, and host fields, and it is a simulated dataset, not data from a real incident.

## Why Transformation Matters

Raw logs rarely contain exactly the field an investigation needs, and raw output is often hard for another person to read. Transformation commands solve both problems. They let an analyst create new fields from existing ones, and present results in a clear, ordered, well-named form.

## eval

The eval command creates a new field from a calculation or a condition. It does not change the stored data, only the results of the current search. The pattern is eval, then the new field name, an equals sign, and an expression.

Hands-on: the lab log only has raw IP addresses. To find out whether each login came from inside or outside the network, I used eval with an if condition and a like function. The like function checks whether the address starts with the private prefix 192.168, using a percent sign as the wildcard. If it matches, the event is labeled internal, otherwise external. I then counted events by the new network field and by action.

Results on the lab dataset:

- External failed logins: 10
- External successful logins: 1
- Internal failed logins: 1
- Internal successful logins: 8

What this shows: 10 of the 11 failed logins came from outside the network. The single external success is also worth noticing. It comes from the same address that failed seven times earlier, and a burst of failures followed by a success from the same outside address is the pattern an account-compromise investigation looks for. That pattern was only visible because I created a field the raw data did not have.

Limitation: this label only checks one private address range. Real networks use several, so a production version would need a fuller check.

## rename

The rename command changes a field's name in the results, using the old name, the keyword AS, and the new name. Names with spaces go in quotes. It does not alter the underlying data. It is mainly for readability, so that tables and dashboards make sense to someone who did not write the search.

Hands-on: I filtered the lab data to failed events, counted them by source IP, and renamed the columns to Source IP and Failed Logins. I then sorted by the Failed Logins column in descending order.

Results: three rows, with 203.0.113.9 on top at 7 failures, then 198.51.100.7 at 3, then 192.168.1.31 at 1.

## fields, table, and sort

These three commands were introduced in the SPL fundamentals module and are part of every transformation pipeline:

- The fields command keeps or removes fields without turning the results into a table.
- The table command chooses which fields to display as columns.
- The sort command orders results, with a minus sign for descending order.

In this module, sort was used again to put the biggest group first after renaming. Used together with eval and rename, these commands turn raw events into an ordered, readable investigation table.

## Key Takeaways

- Eval creates fields the raw data does not have, which can reveal patterns that were invisible before.
- Rename makes tables readable for other people, without changing the data.
- Fields trims what is carried forward, table shapes what is displayed, and sort sets the order.
- A burst of failures followed by a success from the same outside address is a pattern worth investigating.
- Simple labels need limits noted. An internal check on one address range is not a complete network definition.

## Next Module

Module 10 — Regular Expressions and Field Extraction: the rex command.
