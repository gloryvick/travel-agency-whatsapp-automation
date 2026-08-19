# Travel Agency WhatsApp Automation

An n8n workflow that sends automated WhatsApp messages to clients of a fictional travel agency, Travel Beta, before departure and after return. Built as a portfolio project.

## What it does

Pulls client and trip details from Google Sheets and uses the Green API to send two messages automatically:

1. A pre departure reminder before the client's flight
2. A welcome back message after the client returns

## Tools used

- n8n for the workflow
- Google Sheets as the data source
- Green API for WhatsApp delivery

## How it works

A scheduled trigger checks the Google Sheet for upcoming or completed trips, reads the client's details, and branches to send the correct message depending on the trip stage. Message content is built dynamically from the sheet data, then sent through Green API.

See the n8n full canvas for the full workflow canvas.

## Challenges and what I learned

- 403 errors from Green API: fixed by correcting how credentials and the instance ID were passed in the request headers
- Google Sheets range errors: the range specified in the node did not match the actual sheet structure, fixed by matching it exactly to the sheet name and column boundaries
- Row number scoping: a row_number variable was not carrying its value correctly between nodes, fixed by tracing node outputs and referencing them explicitly instead of assuming they'd carry over
- JSON body formatting: malformed request bodies caused silent failures, fixed by making sure dynamic values were inserted as valid JSON

This project taught me a lot about how data actually flows between n8n nodes, and the importance of verifying assumptions instead of guessing.

## Notes

Uses fictional client data. All API keys and credentials have been removed from the exported workflow file. Add your own Google Sheets connection and Green API credentials to reuse it.
