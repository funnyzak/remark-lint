<!--This file is generated-->

# remark-lint-linebreak-style

[![Build][build-badge]][build]
[![Coverage][coverage-badge]][coverage]
[![Downloads][downloads-badge]][downloads]
[![Size][size-badge]][size]
[![Sponsors][sponsors-badge]][collective]
[![Backers][backers-badge]][collective]
[![Chat][chat-badge]][chat]

Warn when linebreaks violate a given or detected style.

Options: either `'unix'` (for `\n`, denoted as `␊`), `'windows'` (for `\r\n`,
denoted as `␍␊`), or `'consistent'` (to detect the first used linebreak in
a file).  Default: `'consistent'`.

## Fix

[`remark-stringify`](https://github.com/remarkjs/remark/tree/HEAD/packages/remark-stringify)
always uses unix linebreaks.

See [Using remark to fix your Markdown](https://github.com/remarkjs/remark-lint#using-remark-to-fix-your-markdown)
on how to automatically fix warnings for this rule.

## Presets

This rule is not included in any default preset

## Example

##### `ok-consistent-as-windows.md`

###### In

Note: `␍␊` represents a carriage return and a line feed.

```markdown
Alpha␍␊
Bravo␍␊
```

###### Out

No messages.

##### `ok-consistent-as-unix.md`

###### In

Note: `␊` represents a line feed.

```markdown
Alpha␊
Bravo␊
```

###### Out

No messages.

##### `not-ok-unix.md`

When configured with `'unix'`.

###### In

Note: `␍␊` represents a carriage return and a line feed.

```markdown
Alpha␍␊
```

###### Out

```text
1:7: Expected linebreaks to be unix (`\n`), not windows (`\r\n`)
```

##### `not-ok-windows.md`

When configured with `'windows'`.

###### In

Note: `␊` represents a line feed.

```markdown
Alpha␊
```

###### Out

```text
1:6: Expected linebreaks to be windows (`\r\n`), not unix (`\n`)
```

## Install

This package is [ESM only][esm]:
Node 12+ is needed to use it and it must be `imported`ed instead of `required`d.

[npm][]:

```sh
npm install remark-lint-linebreak-style
```

This package exports no identifiers.
The default export is `remarkLintLinebreakStyle`.

## Use

You probably want to use it on the CLI through a config file:

```diff
 …
 "remarkConfig": {
   "plugins": [
     …
     "lint",
+    "lint-linebreak-style",
     …
   ]
 }
 …
```

Or use it on the CLI directly

```sh
remark -u lint -u lint-linebreak-style readme.md
```

Or use this on the API:

```diff
 import {remark} from 'remark'
 import {reporter} from 'vfile-reporter'
 import remarkLint from 'remark-lint'
 import remarkLintLinebreakStyle from 'remark-lint-linebreak-style'

 remark()
   .use(remarkLint)
+  .use(remarkLintLinebreakStyle)
   .process('_Emphasis_ and **importance**')
   .then((file) => {
     console.error(reporter(file))
   })
```

## Contribute

See [`contributing.md`][contributing] in [`remarkjs/.github`][health] for ways
to get started.
See [`support.md`][support] for ways to get help.

This project has a [code of conduct][coc].
By interacting with this repository, organization, or community you agree to
abide by its terms.

## License

[MIT][license] © [Titus Wormer][author]

[build-badge]: https://github.com/remarkjs/remark-lint/workflows/main/badge.svg

[build]: https://github.com/remarkjs/remark-lint/actions

[coverage-badge]: https://img.shields.io/codecov/c/github/remarkjs/remark-lint.svg

[coverage]: https://codecov.io/github/remarkjs/remark-lint

[downloads-badge]: https://img.shields.io/npm/dm/remark-lint-linebreak-style.svg

[downloads]: https://www.npmjs.com/package/remark-lint-linebreak-style

[size-badge]: https://img.shields.io/bundlephobia/minzip/remark-lint-linebreak-style.svg

[size]: https://bundlephobia.com/result?p=remark-lint-linebreak-style

[sponsors-badge]: https://opencollective.com/unified/sponsors/badge.svg

[backers-badge]: https://opencollective.com/unified/backers/badge.svg

[collective]: https://opencollective.com/unified

[chat-badge]: https://img.shields.io/badge/chat-discussions-success.svg

[chat]: https://github.com/remarkjs/remark/discussions

[esm]: https://gist.github.com/sindresorhus/a39789f98801d908bbc7ff3ecc99d99c

[npm]: https://docs.npmjs.com/cli/install

[health]: https://github.com/remarkjs/.github

[contributing]: https://github.com/remarkjs/.github/blob/HEAD/contributing.md

[support]: https://github.com/remarkjs/.github/blob/HEAD/support.md

[coc]: https://github.com/remarkjs/.github/blob/HEAD/code-of-conduct.md

[license]: https://github.com/remarkjs/remark-lint/blob/main/license

[author]: https://wooorm.com
