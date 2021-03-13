# How to write this wiki

## Table of contents

* [How to write this wiki](#how-to-write-this-wiki)
  * [Table of contents](#table-of-contents)
  * [Guidelines and Rules](#guidelines-and-rules)
  * [Validation and Syntax](#validation-and-syntax)

## Guidelines and Rules

* Avoid Pictures unless required - why?
  * Pictures generally aren't TTS compatible and cannot be copy-pasted in some text inputs.
  * I don't know how to host them in a github repository and reference them in .md as a relative link to a specific file
* use `` to `contrast` main points and provide `visual cues` for the  the `reader`
* Segment the content based on headings using `#`
* `Fenced code-blocks` should be `copy-paste-able` directly without any user editing.
* Whenever `optional data` is presented that could cause the reader to `scroll` or break the flow of reading `hide it` with:
<!-- #region collapsed region example -->
<details open>
<summary>collapsible region example:</summary>

```markdown
<!-- #region(collapsed) region name-->
<details open>
<summary>summary</summary>
collapsible text
</details>
<!-- #endregion -->
```

</details>
<!-- #endregion -->

* always create table of contents (use markdown all in one)
* always write the text to be Text2Speech compatible with copy paste

## Validation and Syntax

This markdown syntax is featuring few main vscode extensions.

* `yzhang.markdown-all-in-one` - snippets, shortcuts, self-updating table of contents
* `davidanson.vscode-markdownlint` - provide linting rules and errors
* `maptz.regionfolder` - region folding for unfoldable html tags
