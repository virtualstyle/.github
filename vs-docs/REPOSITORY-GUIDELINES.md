# Repository Guidelines

**This is the single controlling file for agent behavior**

## Project Structure & Module Organization

- All config files belong in the the repo root,in the .config directory, unless this is not possible.
- All package code lives in `src/` directories under the named project directories in the app or lib directories.
- Functionality requiring multiple files should be placed in directories named according to their primary function.
- All verification/testing lives in project `test/` directories, where each module has a matching `*.test.js` for unit tests. If/when it makes sense, integration and/or end to end tests will have integration and/or end2end directories created to house their respective tests.

## Build, Test & Development Commands

Moonrepo is the taskrunner, with common tasks inherited across multiple projects (located in `.moon/tasks.yml` and `.moon/tasks/*`), and project-specific tasks (located in `.moon.yml` files in project root directories).

Information about projects and tasks can be obtained witht the following commands:

- `moon query projects <optional_filtering_criteria>` will provide info about projects in the workspace
- `moon p <project_alias>` will provide details about a specific project
- `moon t <project_alias>:<task_name>` will provide details about a specific project's task

There are numerous other commands, such as project-graph, task-graph, and query, which provide even more information, but they aren't documented here.

Project tasks can be run as follows (note that `moonx` is shorthand for `moon run`):

- `moonx <project_alias>:<task_name>` to run on a single project
- `moonx <task_name>` to run on the closest project
- `moonx <project_alias>:<task_name> <project_alias>:<task_name>...` to run on a setof projects
- `moonx :<task_name>` to run across all projects with the task
- `moonx #<tag>:<task_name>` torun on allprojects with a specific tag
- `moonx --query "<query_criteria_parameters>"`

## Coding Style & Naming Conventions

### Coding Standards

#### Linting & Formatting

Code is linted by ESLint (Standard + SonarJS + security rules) and formatted with Prettier. The core editorconfig settings should be enforced: 2-space indentation, 80-character `max-len`, `singleQuote: true`, and `semi: false`. Run `moonx <project_alias>:code` before pushing.

#### Commenting

Comments should be limited to JSDoc annotations, unless code is extremely obscure, or notes are required explaining why the code was written a certain way. Comments should always exist on their own line(s) - never on the same line as code.

### Naming Conventions

#### Object & Variable Naming

Keep classes and exported singletons in PascalCase, internal helpers in lowerCamelCase.

#### File Naming

Files & directories should be named in kebab-case, except for class files, which should be Pacla/Studly case, thgesame as the class name.

## Testing Guidelines

Vitest operates in the Node environment with globals enabled. Place specs beside the unit type in `test/` using the `<module>.test.js` suffix to ensure coverage inclusion (`vitest.config.js` only collects `src/**/*.js`). Tests must keep coverage at 100% (lines/functions/branches/statements); add targeted fixtures instead of loosening the threshold.

## Commit & Pull Request Guidelines

Git history follows Conventional Commits (`chore: initial commit`), so stick to `<type>: <imperative summary>` with types like `feat`, `fix`, `chore`, or `test`. Each pull request should include: a short problem statement, a summary of changes, explicit test evidence (`pnpm test` output, lint checks), and links to related issues or design notes. Add screenshots or terminal captures when a formatter or demo view changes. Avoid mixing refactors with behavior changes—open separate PRs if necessary.

## Security & Configuration Tips

Do not loosen the ESLint security rules or SonarJS warnings without discussion; most serve as guardrails for console formatting. Do not add dependencies - suggest them to the user and the user will install them. Do not add env vars, or files, or any secrets - if needed, bring itup with the user and they will handle it.
