# RDA TIGER PDFs

This repository stores the PDF support materials for the RDA support material drawer (https://rda.dansdemo.nl). PDF files are served via GitHub Pages, and their corresponding endpoints are maintained in the `config.json` file.

## Managing Files

The repository uses a two-branch workflow to clearly separate development from production:

- **Staging Branch:**  
  All new changes, including additions or updates to PDF files, should be committed to the staging branch. This branch is used for testing and reviewing modifications without impacting the live site.

- **Main Branch:**  
  Only the files in the main branch are publicly accessible through GitHub Pages. Once changes in staging have been fully tested and approved, they should be merged into the main branch.

The `config.json` file maps each PDF file (located in the repository) to its corresponding URL on GitHub Pages. For example, an entry in `config.json` might look like this:

```json
[
  {
    "group": "Guidance and Support",
    "materials": [
      {
        "topic": "FAQ",
        "type": "PDF",
        "url": "https://dans-knaw.github.io/RDA-TIGER-PDFs/3.5.8-3.6.0%20-%20V0.1%20-%20FAQs.pdf"
      }
    ]
  }
]
```

When adding new PDFs, ensure the file name is URL-encoded correctly, and update the config.json file to reflect the new endpoint.

## Integrating with Your Application

To integrate these PDFs into your application, fetch the raw `config.json` file from GitHub. For example, you can use the following JavaScript snippet:

```js
fetch(
  "https://raw.githubusercontent.com/DANS-KNAW/RDA-TIGER-PDFs/refs/heads/main/config.json"
)
  .then((response) => response.json())
  .then((data) => {
    // Process the JSON data to access the PDF endpoints
    console.log(data);
  })
  .catch((error) => console.error("Error fetching config:", error));
```
This method allows your application to dynamically retrieve the latest endpoints for the PDFs without requiring manual updates.