# Module 06 — Filtering Events

## Objective

Learn how to narrow Splunk results precisely using AND, OR, NOT, wildcards, exact matches, and field filtering. All practice was done on a sample SSH-style authentication log with 6 events, uploaded in Module 03.

## AND

AND keeps only events that match both conditions. A space between two terms already means AND, so searching for failed admin and failed AND admin are identical. An analyst uses it to find failed logins for one account, where the event must contain both the word failed and the account name.

Results on my sample log:

- Failed AND admin returned 3 events.
- Accepted AND admin returned 1 event.
- Failed AND accepted returned 0 events, because every line is either a failed login or an accepted one, never both.

Important rule: AND, OR, and NOT must be written in capital letters.

## OR

OR keeps events that match either condition, or both. Where AND narrows results, OR widens them. An analyst checking whether an attacker touched privileged accounts can search for admin OR root to see activity on either account.

Parentheses group conditions and make the meaning explicit. Without them, mixing OR with other terms can give surprising results, because Splunk evaluates the OR first.

Results on my sample log:

- Failed OR accepted returned 6 events.
- Root OR divine returned 2 events.
- Failed admin grouped with accepted divine, joined by OR and wrapped in parentheses, returned 4 events: three failed admin lines and one accepted divine line.

## Troubleshooting: Lowercase Operators

My first attempt at the grouped search returned 0 events. The cause was that I had typed the operator in lowercase. In lowercase, or is not an operator, so Splunk searched for events containing the literal word or, and no event had it. With a capital OR the search returned 4.

Lesson: always capitalize AND, OR, and NOT. A wrong-looking zero can come from the search being silently interpreted as something different from what was intended.

## NOT

NOT removes events that match a condition, which is how noise is cut out of results. An analyst hunting for suspicious logins can exclude a known test account so that only real activity is left.

Results on my sample log:

- NOT failed returned 2 events, the two accepted logins.
- Failed NOT admin returned 1 event, the failed root line.
- NOT admin returned 2 events, the failed root line and the accepted divine line.

## Wildcards

The wildcard character stands for any characters, so partial words can be matched. A search for fail followed by a wildcard matches failed, failure, and fails. It also works in field values. A wildcard at the start of a term makes Splunk check far more data and is slower on large searches, so wildcards are best placed at the end.

Results on my sample log:

- Fail with a wildcard returned 4 events.
- Acc with a wildcard returned 2 events.
- Fail with a wildcard, combined with NOT and adm with a wildcard, returned 1 event.

## Exact Matches

Putting words in quotes searches for an exact phrase, with the words side by side in that order. Without quotes, two words mean both must appear somewhere in the event, in any position. Quotes are also required when a field value contains spaces. An analyst searching for an exact error message avoids matching unrelated events that merely contain the same words somewhere.

Results on my sample log:

- The phrase Failed password for admin returned 3 events.
- The phrase password for admin returned 4 events, since it also matches the accepted admin login.
- The phrase admin password returned 0 events, because those words never appear in that order.

## Field Filtering

Field filters combine with keywords and with AND, OR, and NOT. There are three forms, and they behave differently:

- A field equals a value keeps events where the field has that value.
- A field not equal to a value keeps only events where the field exists and has a different value.
- NOT with a field equals a value removes events with that value, and keeps events that do not have the field at all.

My sample log has no field called user, which made it a good test.

Results:

- Searching the sourcetype with the source and the keyword failed returned 4 events.
- Filtering with user not equal to admin returned 0 events, because no event has a user field, so nothing can match a different value.
- Excluding with NOT user equals admin returned all 6 events, because none of them has that field at all.

Why this matters in security work: if some log sources lack a username field, the not-equal form silently drops their events. That could hide real evidence, so the NOT form is safer when the field may be missing.

## A Note on Unexpected Results

Several searches in this module gave an unexpected number on the first try, and each had a simple cause such as a typing slip or a lowercase operator. Rerunning the exact search and checking capitalization, quotes, and the time range resolved every one. When a count looks wrong, compare it with what the data should give before trusting it.

## Key Takeaways

- AND narrows, OR widens, and NOT removes. Write them in capital letters.
- Use parentheses to make grouped conditions explicit.
- Wildcards catch variations of a word, and are best placed at the end of a term.
- Quotes search for an exact phrase in order.
- A field not equal to a value only matches events that have the field. NOT also keeps events that lack it.
- A surprising zero is worth investigating before concluding that nothing happened.

## Next Module

Module 07 — Statistics and Aggregation: stats count, stats count by, stats values, and stats dc.
