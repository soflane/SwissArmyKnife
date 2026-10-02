# Contributing

Thanks for helping keep SwissArmyKnife practical and easy to scan. The
repository uses English for published documentation, file names, headings, and
descriptions.

## Capture first, classify later

If an item has not been reviewed, add it to [INBOX.md](INBOX.md) with a link,
a short reason for saving it, and one or two suggested tags. A reviewed
application must live in exactly one functional section of
[the tool catalog](tools/README.md) or a dedicated domain catalog, such as
[AI tools](ai/README.md) or [self-hosted projects](self-hosted/README.md).
Platform pages link to these sections and must not duplicate application
descriptions.

The content flow is:

```text
INBOX.md -> tools/README.md or a domain guide -> archive/README.md
```

## Add a tool

Use a compact, outcome-focused entry:

```markdown
- **[Tool name](https://example.com)** — One sentence explaining the problem
  it solves and when to use it.  
  `Windows` `Network` `GUI` `Free`
```

- Link to the official website or repository whenever possible.
- Start the description with the practical use, not a marketing claim.
- Include at least one platform or domain tag.
- Choose the functional section from the application's main use, not from its
  operating system.
- List every supported platform as a tag, especially for cross-platform tools.
- Avoid duplicating an entry across platform or domain pages; link to its
  canonical functional section when another page needs to mention it.
- Prefer explicit labels such as `Open source`, `Free`, or `Commercial` only
  when the licensing model has been checked.

## Add a procedure

Published procedures use this lightweight structure:

```markdown
# Outcome-oriented title

> One-sentence description of the expected result.

## Prerequisites
## Steps
## Verify
## References
```

Add a warning directly before a risky operation. Use fenced code blocks with a
language such as `bash`, `powershell`, `yaml`, or `text`. Never publish real
passwords, tokens, hostnames, public IP addresses, or other private values.

## Names and assets

- Use lowercase kebab-case for files and directories, except for standard
  GitHub files such as `README.md` and `CONTRIBUTING.md`.
- Put reusable screenshots in `assets/images/` and use relative links.
- Write meaningful image alt text that explains what the screenshot shows.
- Keep unfinished material in `drafts/`; drafts are not linked from the public
  navigation.

## Archive an entry

Move an obsolete or rejected tool to [archive/README.md](archive/README.md).
Record its previous category, why it was archived, and a recommended
replacement when one exists. Do not silently delete useful history.

## Before submitting

- Check that an application exists in one functional section only.
- Open every new relative link and image path.
- Run the Markdown and link checks, or confirm that the GitHub Actions checks
  pass on the pull request.
