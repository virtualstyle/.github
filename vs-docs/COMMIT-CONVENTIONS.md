# virtualStyle Commit Conventions

All commit messages must follow these specifications, to ensure, as much as possible, compatibility with any automated processes which may consume them.

These specifications are a simplified version of the [Conventional Commits standard](https://www.conventionalcommits.org/). If any deviations from that standard are discovered here, the current Conventional Commits standard should take precedence and the deviation should be noted and reported.

## Structure
**Full Structure Diagram**

```
<type>[optional scope]<colon><space><description>
<blank line required between description and body, if body included>

[optional body paragraph]
<blank line required between body paragraphs>

[optional body paragraph]
<blank line required between the body and any footers, if included>

[optional footer(s)]
<token-in-kebab-case>[<colon><space> OR <space><hash symbol>]
<token-in-kebab-case>[<colon><space> OR <space><hash symbol>]

```

**Minimum Structure**

```
<type><colon><space><description>
```

**Minimal Commit Message Example**

```
fix: fix some bug
```

**Extended Commit Message Example**

```
fix(auth): eliminate login failures

Add try/catch around auth API calls.

Abstract auth code to a function call.

Add handling for failed API calls.

Add error logging and reporting.

BREAKING CHANGE# Dependents of imperative auth must refactor to call new auth functions.
Signed-off-by: Bob <bob@example.com>
```


## Fixed Requirements

1. Commits **MUST** be prefixed with a type from the list in this document.

2. The type `feat` **MUST** be used when a commit adds a new feature to your application or library.

3. The type `fix` **MUST** be used when a commit represents a bug fix for your application.

4. A description (short summary of the code changes) **MUST** immediately follow the colon and space after the type prefix.

5.Description of code changes **MUST** be written in the **imperative** (present tense, not past tense, i.e.: “fix” rather than “fixed”)

4. Breaking changes **MUST** be clearly indicated, either in the type/scope prefix of a commit, or as an entry in the footer.
   A. If included as a footer, a breaking change MUST consist of the **uppercase** text "BREAKING CHANGE," followed by a **colon**, **space**, and **description**, e.g., *BREAKING CHANGE: environment variables now take precedence over config files*.
   B. If included in the type/scope prefix, breaking changes MUST be indicated by a "!" immediately before the ":". If "!" is used, "BREAKING CHANGE:" MAY be omitted from the footer section, and the commit description **SHALL** be used to describe the breaking change.

### Minimal Commit Message Example

`fix: fix some bug`

## Optional Items

1. An optional scope **MAY** be provided after a type. A scope **MUST** consist of a noun describing a section of the codebase surrounded by parenthesis, e.g., "fix(parser):"

2. An optional longer commit body **MAY** be provided after the short description, providing additional contextual information about the code changes. If a body is included, there **MUST** be a blank line between the top description line and the body.

3. A commit body is free-form and **MAY** consist of any number of newline separated paragraphs.

4. One or more optional footers **MAY** be provided after the body. There **MUST** be a blank line between the body and the first of any footers.

  A. Any footer(s) **MUST** consist of a word token, followed by either a ":<space>" or "<space>#" separator, followed by a string value (this is inspired by the [git trailer convention](https://git-scm.com/docs/git-interpret-trailers)). "BREAKING CHANGE" footers **MUST** use ":<space>".

  B. A footer’s token **MUST** be in kebab-case, using `-` in place of whitespace characters, e.g., "Signed-off-by" instead of "Signed off by". (this helps differentiate the footer section from a multi-paragraph body). An exception is made for "BREAKING CHANGE", which MAY also be used as a token.

5. Types other than **feat** and **fix** **MAY** be used, if included in the list in this document (below).

## Commit Types

1. **fix:** a commit of the type **fix** patches a bug in your codebase (this correlates with [PATCH](http://semver.org/#summary) in Semantic Versioning).
2. **feat:** a commit of the type **feat** introduces a new feature to the codebase (this correlates with [MINOR](http://semver.org/#summary) in Semantic Versioning).
3. Allowed types other than **fix** and **feat** are:
   (from [@commitlint/config-conventional](https://github.com/conventional-changelog/commitlint/tree/master/@commitlint/config-conventional))
   1. **build:** Changes that affect the build system or external dependencies.
   2. **chore:** Organizational changes and miscellaneous tasks that don’t fit under the other types.
   3. **ci:** Changes to CI configuration files and scripts.
   4. **docs:** Documentation only changes.
   5. **perf:** Changes to improve performance.
   6. **refactor:** Code changes that alter internal structure without changing external behavior (that don’t add features or fix bugs).
   7. **revert:** If the commit reverts a previous commit, it should begin with “revert: “, followed by the header of the reverted commit. In the body it should say: “This reverts commit <hash>.”, where the hash is the SHA of the commit being reverted.
   8. **style:** Code changes that are purely stylistic and formatting, that do not alter structure or function (they don’t add features, fix bugs, or refactor, such as white-space, formatting, missing semi-colons, etc)
   9. **test:** Changes and additions to the code that tests the functional code.
