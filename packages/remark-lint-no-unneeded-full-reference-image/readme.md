<!--This file is generated-->

# remark-lint-no-unneeded-full-reference-image

[![Build][build-badge]][build]
[![Coverage][coverage-badge]][coverage]
[![Downloads][downloads-badge]][downloads]
[![Size][size-badge]][size]
[![Sponsors][sponsors-badge]][collective]
[![Backers][backers-badge]][collective]
[![Chat][chat-badge]][chat]

Warn when full reference images are used that could be collapsed.

Full references (such as `[Remark][remark]`) can also be written as a
collapsed reference (`[Remark][]`) if normalising the reference text yields
the label.

## Presets

This rule is not included in any default preset

## Example

##### `ok.md`

###### In

```markdown
![alpha][]
![Bravo][]
![Charlie][delta]

[alpha]: a
[bravo]: b
[delta]: d
```

###### Out

No messages.

##### `not-ok.md`

###### In

```markdown
![alpha][alpha]
![Bravo][bravo]
![charlie][Charlie]

[alpha]: a
[bravo]: b
[charlie]: c
```

###### Out

```text
1:1-1:16: Remove the image label as it matches the reference text
2:1-2:16: Remove the image label as it matches the reference text
3:1-3:20: Remove the image label as it matches the reference text
```

## Install

This package is [ESM only][esm]:
Node 12+ is needed to use it and it must be `imported`ed instead of `required`d.

[npm][]:

```sh
npm install remark-lint-no-unneeded-full-reference-image
```

This package exports no identifiers.
The default export is `remarkLintNoUnneededFullReferenceImage`.

## Use

You probably want to use it on the CLI through a config file:

```diff
 …
 "remarkConfig": {
   "plugins": [
     …
     "lint",
+    "lint-no-unneeded-full-reference-image",
     …
   ]
 }
 …
```

Or use it on the CLI directly

```sh
remark -u lint -u lint-no-unneeded-full-reference-image readme.md
```

Or use this on the API:

```diff
 import {remark} from 'remark'
 import {reporter} from 'vfile-reporter'
 import remarkLint from 'remark-lint'
 import remarkLintNoUnneededFullReferenceImage from 'remark-lint-no-unneeded-full-reference-image'

 remark()
   .use(remarkLint)
+  .use(remarkLintNoUnneededFullReferenceImage)
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

[downloads-badge]: https://img.shields.io/npm/dm/remark-lint-no-unneeded-full-reference-image.svg

[downloads]: https://www.npmjs.com/package/remark-lint-no-unneeded-full-reference-image

[size-badge]: https://img.shields.io/bundlephobia/minzip/remark-lint-no-unneeded-full-reference-image.svg

[size]: https://bundlephobia.com/result?p=remark-lint-no-unneeded-full-reference-image

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
