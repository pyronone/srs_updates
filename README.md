# From Tedious to Effortless


<!-- ... -->

## Streamlined Data Updates with Python

------------------------------------------------------------------------

When I first joined, processing day-to-day data updates for the Sears
plan was a painfully manual process.

Every month, we’d comb through tickets in Harmony (our internal ticket
system) one by one, copy-pasting details into a sprawling Excel
‘database’ and manually cross-referencing and updating a separate
‘maintenance file’ — a critical file sent monthly to CIBC Mellon to
update and sync their systems.

The process was so tedious it led to skipped steps and one of my first
tasks when I joined was actually untangling incongruent data between the
internal and external databases.

Enter `srs_updates`.

Now, the entire workflow is streamlined and runs like clockwork: Harmony
tickets are scraped automatically and exported into a spreadsheet for
quick review and formatting, the database is updated quickly and
accurately via scripts and macros, and the maintenance files are
generated automatically with only minor revisions needed at the end.

What once took hours of manual work now runs automatically in minutes
with near-perfect accuracy.

New features and quality of life improvements are constantly being
added, with rigorous testing and comprehensive documentation.

And the real beauty is that this solution can easily be adapted for
other plans.

------------------------------------------------------------------------

## Key Features

- **Automated Ticket Scraping**

  The [Harmony Automation](./11_harmony_automation.ipynb) module
  streamlines data collection by automatically scraping all comments and
  notes from tickets in our internal system — no more manual
  copy-pasting or tedious browser navigation.

- **Structured for Easy Processing**

  Scraped ticket data is automatically exported to a spreadsheet for
  some minor editing to allow the `core` module to extract structured
  data from the note.

  For example, the following would be used to update the address, email,
  and phone number:

  ![Example](./images/example_ticket_note.png)

- **Integrated Data Enrichment**

  The spreadsheet pulls in additional supplementary data from various
  sources using Power Query, including reports from CIBC Mellon (the
  plan custodian) and our internal databases, to support a comprehensive
  set of features.

  For example, if a member dies, a note will be generated advising of
  any further entitlements owed. This note would then be added when
  re-assigning the tickets to the colleague that handles those
  processes.

- **Automated Data Updates in Seconds**

  Transforms raw spreadsheets into standardized Excel files — ready to
  update internal databases and external systems. Minimizes manual
  reformatting and reduces processing time from hours to minutes, all
  while maintaining flawless data consistency.

  For updates to the internal database, the
  [update_xl](./08_update_xl.ipynb) module also generates detailed,
  human-readable changelogs showing exactly what changes were made and
  when.

- **Automated Ticket Closing / Re-assigning**

  The [Harmony Automation](./11_harmony_automation.ipynb) module
  contains functions to automate the closing and re-assigning of
  tickets, which means no more manually closing and re-assigning tickets
  and tedious browser navigation/actions.

  This is particularly useful during periods of higher ticket volumes,
  such as after sending out communications, option forms, etc.
