# Instructions for fixing OCR text output

## How to edit

1. Navigate to http://www.iuropa.pol.gu.se/CJEU-database/CJEU-text-corpus/text-editor
2. Sign in with your credentials
3. Search for an ECLI number or based on criteria to start editing. **Pages with columns are a priority**
4. Check text against page image and edit the text accordingly
5. Click "Code" when the check is complete to save and proceed to the next edit

Note that if you leave the editing window open but you are inactive for more than 12 hours, you will be signed out. Avoid progress being lost by clicking "Save" which will not mark the page as complete but save your progress.

## Coding decisions

The **primary objective** is to ensure that paragraphs in the text flow in the correct order. The OCR engine does not always recognize the paragraph blocks in the right order, especially on pages with columns.

**Paragraphs must be separated by an empty new line (pressing Enter).** We consider lines such as "In Case 1/54," as separate paragraphs, but the most important thing is to identify and separate *true* paragraphs in the ordinary sense of the word, i.e. blocks of sentences. Assembling the raw text (you may encounter some light preprocessing) into correct paragraph blocks will typically entail merging lines but you may also need to move text around or split wrongly merged text.

Additionally, we implement the following fixes:
- if you see an obvious typo, you can correct it (e.g. commonly "Count" instead of "Court", "Anicle" instead of "Article" etc.)
- watch out for missing short words (e.g. "on", "to", "an", "a", "et")
- if you see the raw text does not contain paragraph numbers (or other characters) found in the scanned document, add them
- concatenate hyphenated words at the end of a line
- delete the running header on top of the page
- where a footnote number is used in text as superscript, enclose the footnote number in parentheses and put a space before and after it to separate it from surrounding text
- fix footnotes as per usual and leave them in their place (usually bottom of page)
- remove the page number from the bottom of the page
- remove any weird characters that obviously are not part of the original text
- delete text that obviously does not belong to the ECLI page you are editing (e.g. when a different document ends or begins on the same page)
- if you encounter a table, you can delete its contents in the text editor and instead include one line that reads: \[table\]
- the OCR engine frequently struggles to format dash-separated clauses or phrases in sentences - make sure there is a space before and after each separating dash (does __not__ apply to hyphens within words like decision-making)
- symbols denoting enumeration in French like "°" (e.g. 1° ... text ...) can be replaced with a "." full stop (e.g. 1. ... text ...), but remain consistent if you do this

We are aware that in some situations you are forced to exercise your judgment to complete the edit. You may encounter, for example:
- line breaks that appear to break the natural flow of what would otherwise be a reasonable paragraph, for example when in older documents a company's address or lawyers are listed on separate lines. In this situation you can break the general rule that each line should be a separate paragraph and concatenate the text
- in the plain text format that we force the documents into we cannot reflect horizontal positioning on the page, such as when sitting judges are listed next to each other at the end of a ruling. In this case the name of each judge can be put on a separate line

## Examples

The following excertps illustrate the desired end results of paragraph editing in line with the instructions:

![image](https://user-images.githubusercontent.com/46047818/153920021-2200ce73-cc10-4a14-afa9-72e37991ab92.png)

![image](https://user-images.githubusercontent.com/46047818/156618347-ab55652a-e6c3-4532-8808-56dcb67af066.png)

In the following example the text of the Advocate-General Opinion below the ruling does not pertain to the ECLI number we are editing and so it is deleted in the text editor (as is the running header on top).

![image](https://user-images.githubusercontent.com/46047818/156821351-aefc549b-13d4-4d22-9ea3-140c6fa93045.png)

In the following example, the raw text did not contain the paragraph number ("7"), so it was added manually. Paragraph numbers are important to retain in the processed text.

![image](https://user-images.githubusercontent.com/46047818/156882436-baac4556-a451-44c3-bf4d-cd94a31d447f.png)

## Contact

In case you encounter any issues or have questions concerning editing, please email me at michal dot ovadek at gu dot se.
