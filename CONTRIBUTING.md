# General notes

Everyone is welcome to contrubute. Maintainers, contributors and users alike are expected to behave in a professional and civil manner.

# Coding guidelines

If this is your first contribution, browse around the code to acquaint yourself with the coding style. We aim to follow common sense and 
functional programming principles. In addition, since you are working on a minimalistic library, code must be bloat-free and
not obviously non-performant.

Bugfixes and new features must come with tests.

New features / APIs should come with javadoc, [examples](sane-dbc-examples) and an entry in the [tutorial](README.md).

**Avoid ad-hoc abstractions**. The aim of the project is to bring principled RDBMS interaction to the Java programming language. 
This type of work has been long present in other languages - Haskell, Scala and others. Look for inspiration there. Aim for new APIs
to be canonical and follow established mathematical structure and laws.

If in doubt what the above means, act optimistically and send us a pull request, and we will sort out any issues as comments in the PR.

# Running the tests
* `./gradlew clean check` - clean build / test
* `./gradlew clean check -Dci` - to also run findbugs (slower, therefore hidden behind commandline option)

Tests and findbugs are automatically run via [Travis](https://travis-ci.org/novarto-oss/sane-dbc).

# Publishing

## To local repo
- `./gradlew publishToMavenLocal`

## To artifactory / bintray

### Prerequisites

You need to set the system properties `PUBLISH_USER` and `PUBLISH_KEY` to a valid value in the console

### Snapshot publish

Travis is set up to publish snapshots automatically, via the `maybePublish` gradle task. This happens if the version is snapshot, the branch is master, and the build is non-PR, i.e. it was triggerred because the master branch was pushed to.

If you want to manually publish snapshots, this can be done via

`./gradlew clean artifactoryPublish`

### Release publish
`./gradlew clean bintrayUpload`
