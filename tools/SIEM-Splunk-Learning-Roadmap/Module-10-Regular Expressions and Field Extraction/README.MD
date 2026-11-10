# Module 10 — Regular Expressions and Field Extraction

## Objective

Learn to extract fields from raw log text using the rex command. The practice data is a small SSH-style authentication log file I created, auth_sample.log, with 6 lines. It is a lab file, not data from a real system, and it has no header row, so Splunk did not extract a username or a source IP from it automatically.

## Why Extraction Matters

Not every log arrives with neat fields. A CSV file with a header row gets its columns as fields automatically. A plain text log does not. The information is in the raw text, but without a field it cannot be counted, sorted, or filtered on. Extraction turns text into fields, and once a field exists, every command from the earlier modules works on it.

This also closes a gap from the filtering module, where a search on a username field returned nothing because that field did not exist in this file.

## How rex Works

The rex command takes a regular expression, which is a pattern that describes the shape of text. Part of the pattern is wrapped in a named capture, and whatever matches inside it becomes a new field with that name. Extraction happens at search time, so the stored data is never changed. A wrong pattern costs nothing to fix, and the search can simply be edited and rerun.

The building blocks used in this module:

- Literal text, such as the word from, which anchors the pattern to a known spot in each line.
- A named capture, written as an opening parenthesis, a question mark, the field name in angle brackets, the pattern, and a closing parenthesis. Whatever the pattern matches becomes the field.
- \d matches a single digit, and a plus sign after it means one or more digits.
- \. matches a literal dot. A dot without the backslash would match any character, which is a common mistake.
- \w+ matches a run of letters, digits, or underscores, which suits a username.
- A vertical bar inside brackets means either one option or the other.

## Step 1 — Extract the Source IP

Pattern: from followed by a named capture called src_ip, made of four groups of digits separated by escaped dots.

I displayed the time and src_ip as a table. The result was 6 rows with the following source addresses in time order: 192.168.1.50 for the first three events, 192.168.1.20, 203.0.113.9, and 192.168.1.50 again.

## Step 2 — Extract the User and Source IP Together

Pattern: the word for followed by a named capture called user made of word characters, then the word from followed by the same src_ip capture.

The table of time, user, and src_ip showed 6 rows. The users in time order were admin, admin, root, divine, admin, and admin, each paired with the address from step 1.

## Step 3 — Capture the Result and Count

Pattern: a capture called result that matches either the word Failed or the word Accepted, followed by the words password for, then the user and src_ip captures.

I then counted events by result and src_ip. The table had four rows:

- Accepted from 192.168.1.20: 1
- Accepted from 192.168.1.50: 1
- Failed from 192.168.1.50: 3
- Failed from 203.0.113.9: 1

This table could not have been built from the raw lines, and it took one search once the fields existed.

## Key Takeaways

- Fields that do not exist cannot be counted, sorted, or filtered. Extraction creates them.
- A named capture turns part of the raw text into a field.
- Escape dots with a backslash, because an unescaped dot matches any character.
- Build the pattern up in steps and check the table after each step.
- Extraction happens at search time, so the raw data is never changed and mistakes are cheap.
- Once fields exist, the statistics and transformation commands from earlier modules work on them.

## Next Module

Module 11 — Advanced SPL: combining multiple commands into more powerful investigations, following the pattern search, eval, stats, sort, table.
