# Instructions for fixing OCR text output

## How to edit

1. Navigate to http://www.iuropa.pol.gu.se/CJEU-database/CJEU-text-corpus/text-editor
2. Sign in with your credentials
3. Search for an ECLI number to start editing
4. Check text against page image and if necessary edit text
5. Click "Code as correct" when the check is complete
6. Click "Next" in the top right to navigate to the next page to edit

## Coding decisions

The **primary objective** is to ensure that paragraphs in the text flow in the correct order. The OCR engine does not always recognize the paragraph blocks in the right order, especially on pages with columns.

**Paragraphs must be separated by an empty new line (pressing Enter).**

Additionally, you may also implement the following fixes:
- if you see an obvious typo, you can correct it
- concatenate lines when a sentence spans several lines
- concatenate hyphenated words at the end of a line
- delete the running header on top of the page
- remove the page number from the bottom of the page
- remove any weird characters that obviously are not part of the original text
- delete text that obviously does not belong to the ECLI page you are editing (e.g. when a different document ends or begins on the same page)

We will in any case do an automated clean up after all pages are re-assembled.
