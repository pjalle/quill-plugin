# Quill for Claude

Build Quill models, forms, rules and documents by talking it through with your AI assistant. Connects to your Quill organisation by browser sign-in.

Quill is a document platform. You model your data, build forms and templates,
fill records, generate documents and get them signed. This plugin lets you do
the building by conversation: ask for a form, a validation rule or a generated
document, and your assistant works through it one small step at a time. Every
change lands in the Quill admin app, where you can see it.

## Add it

In Claude Code, add this repository as a plugin marketplace and install the
plugin:

```
/plugin marketplace add pjalle/quill-plugin
/plugin install quill@quill-plugin
```

In claude.ai or ChatGPT, add Quill as a custom connector with the address
https://api.quilltasks.com/mcp. There each change shows on a card in the chat before it is made;
publishing, sending and deleting need your tap.

## Sign in

The first time the assistant uses a Quill tool, a browser window opens and you
sign in to your Quill organisation. There is no key to copy and the plugin never
asks for a password. It connects to https://api.quilltasks.com/mcp and acts only inside the
organisation you sign in to, with your permissions.

## What you can ask

- Help me build a form for new client intake with Quill.
- Add a validation rule to my Quill form so the end date is after the start date.
- Generate a document from a record in my Quill organisation.

## Support

Questions or problems: https://quilltasks.com/contact/ or hello@quilltasks.com.
Privacy policy: https://quilltasks.com/privacy/. Terms: https://quilltasks.com/terms/.

## Licence

MIT. See LICENSE.
