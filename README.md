# Hand-Marked Paper Ballot Creator

This is a tool to create/view/edit hand-marked paper ballots. Once ballots have been proofed, the ballots and election config can be exported as an "election ballot package" which will be imported into the [Mail Ballot Manager](https://github.com/votingworks/mail-ballot-manager)

## Workflow

1. Admin uploads a config file (or possibly a previously created election ballot package).
   - PDF ballots are generated from config
2. Admin previews ballots by precinct/style.
   - Admin may edit the election config at any time. 
   - Saving changes to the election config triggers re-generation of PDF ballots.
3. Admin exports an election ballot package.

   Election Ballot Package contains:
     - `election.json` - VotingWorks data format for election data: contests, canidates,ballot styles, precincts, etc.
     - approved official ballots in pdf format:
       - one for each combination of ballot style and precinct
       - file name pattern: `ballot-style-7-precinct-8.pdf`

## App Screens
- Upload Election Config
  - file upload form
- Edit Election Config
  - Form:
    - Textarea
    - Save button
    - Cancel button (with warning modal, if config has been changed)
    - Remove config (with warning modal)
- List Ballot Styles
  - Rows:
    - precinct
    - style
    - contest count
    - view ballot link
  - Filters:
    - precinct
    - style
- View Ballot
  - Rendered ballot
  - View PDF ballot (in iframe under html ballot or click to open in new window)
  - Previous and Next Ballot Style links

## Navigation

Displayed When config exists.

- Ballot Styles
- Edit Config
- Export Election Ballot Package

## Future Features
- Edit Contest section
  - List Contests screen
  - Edit Contest Screen with live preview

## Open Questions
- Do we implement anything to ensure that ballots are not edited after package is created? 
  - possibly a `ballots.json` with PDF ballot file hashes?
