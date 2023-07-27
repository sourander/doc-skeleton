# Extensions How-To

This file lacks translation(s) on purpose to demonstrate the default-language functionality. English versions is 
always shown, as it is the only existing language.

Below, you can see a demonstration of all extensions that have been activated in the default `mkdocs.yml` file.

## Syntax highlighting

The code block also demonstrates the copy code and the annotation functionality.

```python
import os

a = os.name + '-' + 'cat' # (1)
print(a)
```

1.  :cat: I'm a code annotation! I can contain `code`, __formatted
    text__, images, ... basically anything that can be written in Markdown.

# Emoji

:bulb: The list of Unicode emoji shortnames can be found at [Emojipedia](https://emojipedia.org/twitter/)

Prefer these standard usages for emojis:

| Visual        | Code            | Usage      |
|---------------|-----------------|------------|
| :bulb:        | `:bulb:`        | Useful tip |
| :pushpin:     | `:pushpin:`     | Exercise   |
| :exclamation: | `:exclamation:` | Important  |
| :book:        | `:book:`        | Read more  |

# Mermaid Graphs

``` mermaid
flowchart LR
    Markdown-->Git-->|magic|Success
```

:book: Check more at [Mermaid Tutorials](https://mermaid.js.org/config/Tutorials.html)