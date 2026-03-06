---
name: referendum-italy
description: Fetches and processes information for Italian constitutional referendums. Use this skill to retrieve the full text of a law from Gazzetta Ufficiale, fetch original constitutional articles from Senato, translate them to English, and apply the proposed changes to create a "post-referendum" version of the Constitution.
---

# Referendum Italy

This skill automates the retrieval and processing of Italian constitutional referendum data.

## Workflow

1.  **Date Selection**: Ask the user for the referendum date (YYYY-MM-DD).
2.  **Directory Setup**: Create a directory named after the date. Inside, create `it/` and `en/` subdirectories.
3.  **Gazzetta Ufficiale Fetch**: Search for the original full text of the law as published on the "Gazzetta Ufficiale". Save it as `legge.md` in the date-named folder. Do not use summaries.
4.  **Original Articles**: For each constitutional article modified by the law in `legge.md`:
    -   Fetch the current text from [Senato della Repubblica](https://www.senato.it/istituzione/la-costituzione).
    -   Save the Italian version as `it/articolo-${number_4_digits}.md` with the title `# Articolo ${number_4_digits}` (where number_4_digits is zero-padded to 4 digits, e.g., 0102), the original text (preserving links), and a source link.
    -   Translate the text to English and save as `en/article-${number_4_digits}.md`.
5.  **Initial Commit**: Commit all files with the message: "feat(${date-named-folder}): starting point of the law under voting".
6.  **Apply Changes**: Analyze `legge.md` and apply the specified modifications to the articles in both `it/` and `en/` folders.
7.  **Final Commit**: Commit the updated articles with the message: "feat(${date-named-folder}): version if the referendum would be approved".

## Guidelines

-   Always use the original text from official sources (Gazzetta Ufficiale, Senato).
-   Maintain all Markdown formatting and links in the constitutional articles.
-   Ensure translations are accurate and professional.
-   Perform surgical edits when applying changes from the law to the articles.
