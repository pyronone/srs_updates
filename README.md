# srs_updates


## Overview

- As I am responsible for the day-to-day data updates for Sears, there
  can upwards of 100+ tickets assigned to me on on a bi-weekly basis. To
  make the process less tedious and more efficient, I created several
  scripts to streamline the process.
- What started as relatively simple scripts quickly evolved into full
  packages designed with maintainability and modularity in mind, along
  with thorough testing and documentation. This results in:
  - Easier accommodation for adding new features and/or changing
    requirements.
  - Greater confidence in functionality and higher consistency,
    reliability, and quality of results.
  - Early detection of potential bugs when refactoring.
  - Thorough documentation for reference and knowledge sharing purposes.
- This package works in conjunction with some of my [other
  packages](https://github.com/pyronone/) to automate/streamline the
  data update process. Many features can also be used in other plans,
  especially ones where CIBC Mellon is also the custodian.

## Process

1.  **Scrape tickets**: Instead of manually visiting each ticket in the
    browser, all tickets assigned to me in Harmony are scraped using the
    [Scraper
    bot](https://pyronone.github.io/harmony_automation/bots.html#scraper)
    from my
    [harmony_automation](https://pyronone.github.io/harmony_automation/index.html)
    package.
    - The scraper gets all comments/notes from the ticket and
      cleans/formats them in chronological order.
    - Tickets where the information is stored in attachments still need
      to be reviewed manually.
2.  **Format notes**: The scraped notes are added to a tracker
    spreadsheet where they are manually formatted to fit certain
    patterns/‘codes’.
    - By formatting the notes in a particular way, the `srs_updates`
      package can automatically extract all the relevant data from the
      notes to generate files needed for the data updates.
    - See the `ref/Codes` page for a full list of such ‘codes’.  
    - Steps 1-2 are repeated every couple days until the number of
      pending updates reaches 100 or so.
3.  **Run update**: To run an update, a script calls the
    `export.process_notes` function to generate all files needed for
    internal and external data updates. This is typically done every two
    weeks.
    - The address file is updated using the `update_xl` module, copied
      over from my
      [update_xl](https://pyronone.github.io/update_xl/index.html)
      package. A changelog is also generated, showing exactly what was
      updated and when.
    - The maintenance file is reviewed manually and saved for later. It
      will later be concatenated with files from subsequent updates and
      finalized a few days before the monthly deadline.
4.  **Close/re-assign tickets**: Tickets in Harmony are automatically
    closed/re-assigned using the main
    [Bot](https://pyronone.github.io/harmony_automation/bots.html#bot)
    from my
    [harmony_automation](https://pyronone.github.io/harmony_automation/index.html)
    package.
    - This eliminates the need to manually close/re-assign up to 100+
      tickets after each update.

## Changelog

### 0.3.3

- No longer need to manually specify if a name update also needs to be
  added to maintenance file - will be automatically detected.
- No longer needed to manually specify if a spouse DOD update is a
  pre-deceased spouse case - will be automatically detected.
