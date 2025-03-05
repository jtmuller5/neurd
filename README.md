# Neurd 🧠

An adaptable note-taking journal built with AI in mind.

## Quickstart

Clone the Neurd template repo and then copy any of the templates from the `/templates` folder into the corresponding folder in the `/content` folder. For example, to add a new daily journal entry, copy the `daily.md` template into a new file in `/content/daily`.

For an even smoother experience, install the [Neurd VS Code Extension ](https://marketplace.visualstudio.com/items?itemName=codeontherocks.neurd-vs-code) and use any of the following commands to create a new journal entry:

- "Neurd: Create Daily Note"
- "Neurd: Create Weekly Note"
- "Neurd: Create General Note"

By default, these commands will use the templates configured in this project. The extension can also be configured to always use the templates in a specific directory (see the "Neurd: Set Default Journal Location"). This will also make it so that all of your notes are always saved to the same location.

## Usage

Using Neurd Notes is relatively straightforward. Add new files to the `daily`, `weekly`, and `notes` directories and then use an integration or the Neurd tools to interact with your content later.

> [!TIP]
> Toggle [Zen Mode](https://code.visualstudio.com/docs/getstarted/userinterface#_zen-mode) in VS code for a distraction-free note taking experience

## Tools

- [Neurd VS Code Extension](https://marketplace.visualstudio.com/items?itemName=codeontherocks.neurd-vs-code): Commands to quickly create daily, weekly, and one-off note files. Chat participant to chat with content inside VS Code.
- Neurd CLI: CLI for generating new files, searching knowledge base, and chatting with content

## Content Management

### Customization

The Neurd VS Code Extension will use the templates in the `templates` folder. These templates are simply markdown files that you can edit. Any changes to `daily.md`, `weekly.md`, or `note.md` will be used in applied to all future notes. 

You can also create custom templates by adding a new markdown file to the `templates` directory. To use it, run the "Neurd: Create Note from Custom Template" command and select your new template. All templates in the `templates` directory are detected automatically.

### Folder Organization

There is no required folder organization so you can organize your notes however you'd like. Many of the integrations below are also extremely lenient about the structure of your data.

To copy all of the content from a single folder, check out the [Clibbits](https://marketplace.visualstudio.com/items?itemName=CodeontheRocks.clibbits) VS Code extension (right-click a folder and select "Copy for AI")

### Private Notes

The [.gitignore](.gitignore) file included in the template repo is set up to ignore all content in the `/content/private` directory. 

## Integrations

Neurd notes are designed to be used alongside AI tools. Some AI tools enable you to chat with your content while others can help you search it. Below are instructions for integrating with popular AI tools.

### VS Code Copilot Fuzzy Search

You can enable the fuzzy/semantic search feature in VS code by toggling the `github.copilot.chat.search.semanticTextResults` experimental setting.

![Semantic search with copilot](image.png)

With this turned on, a new section called "GitHub Copilot Results" will appear in the search sidebar. This should let you search your entire Neurd journal without needing exact search terms.

### LlamaIndex Integration

LlamaIndex is a framework for building LLM-powered agents over your data. One of the most useful aspects of the framework is the [RAG CLI](https://docs.llamaindex.ai/en/stable/getting_started/starter_tools/rag_cli/) which lets you chat with an LLM about the files you have saved locally on your computer.

1. Install the libraries

```bash
pip install -U llama-index
pip install -U chromadb
```

2. Set your OPENAI_API_KEY

```bash
export OPENAI_API_KEY=<api_key>
```

3. Ingest some files

To chat with all of the notes in your Neurd journal, run the following command at the root of your project:

```bash
llamaindex-cli rag --files "./content"
```

4. Ask a question

Once the index is finished building, ask a question:

```bash
llamaindex-cli rag --question "What is LlamaIndex?"
```