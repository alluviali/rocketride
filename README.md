# rocketride Prompts
### - Development? Done

<img src="site/www/img/inspection.jpg" alt="image of woman" width="600">
<p>© 2025 Alluviali. All rights reserved.</p>

---
## A *growing collection* of ***prompts***, *conversations* and *chats* (sans responses) for developing developer tools that develop full cycle software projects. 

> *Note, the spec is evolving, especially related to frontmatter keys in metadata.md, prompt.md and chat.md files

# Showcase 
> "I modified my UML 2.0 diagram for a text hover on the site... and the *full impact* of the change was tested, and deployed in < 1 minute. It left behinds future recommendations.  What is one to do now? I guess I'll take up nature photography" ~Bjorn Mejersk, CTO of NoCoffee418 Solutions *not real, but...

## Quick and dirty summary
- A repo of versioned prompts, conversations, chats that conforms to:
- A spec for a directory structure, and namespacing that supports multiple repositories
- alluviali/rocketride as a default repo
  - * Note: pull requests
    - Maven central rules
    - dont include LLM responses (strip: `$ 'sed '/^<[^-]/d' chat.md`)
      - or explain why its time-enduring interesting.  Don't expect any to be accepted.
    - contributions to README.md must be mimimal

## Repository Goals'
 - *"for developing developer tools that develop full cycle software projects"*
    - See [repository.md](repository.md) for more information
- The main goal of this project is the [`prompts`](https://github.com/alluviali/rocketride/prompts) 'artifacts' directory

## Details
- ***Prompts*** = main goal ([`./prompts`](prompts/)) 
  - example: ([`./prompts/org.nobodyknows`](prompts/org.nobodyknows/))
  - example: 
    - group (all artifacts) ([`./prompts/org.nobodyknows/`](conversations/org.nobodyknows))
    - artifact (all versions) ([`./prompts/org.nobodyknows/tdd/`](conversations/org.nobodyknows/tdd/)) 
    - artifact+version ([`./prompts/org.nobodyknows/tdd/1.0.0`](conversations/org.nobodyknows/tdd/1.0.0))
    - artifact+version+hash ([`./prompts/org.nobodyknows/tdd/1.0.0/jih39`](conversations/org.nobodyknows/tdd/1.0.0/ jih39))
   
- ***Conversations/Chats*** = formal/informal
  - example: 
    - group (all artifacts) ([`./conversations/org.nobodyknows/`](conversations/org.nobodyknows))
    - artifact (all versions) ([`./conversations/org.nobodyknows/tdd/`](conversations/org.nobodyknows/tdd/)) 
    - artifact+version ([`./conversations/org.nobodyknows/tdd/1.0.0`](conversations/org.nobodyknows/tdd/1.0.0))
    - artifact+version+hash ([`./conversations/org.nobodyknows/tdd/1.0.0/394j5hSD`](conversations/org.nobodyknows/tdd/1.0.0/394j5hSD))

* note versions usually look like standard "1.0.0" [semantic versioning](https://semver.org), but sometimes they will include a modifier to signal non-standard support requirements "-"+modifier.  This commonly for a specific target (e.g. Prompts with certain model requirements, like non-standard function support, non-standard tags, non-standard agent support, etc)

* Note: frontmatter metadata in the `chat.md` and `prompt.md` is evolving.

Versions are maintained with hashes (e.g. `com.it:thechat:10.0.0:39dh8h3h`), allowing for more accute forking required by chat and prompt iteration, and encourage sharing (even when messier than formal versioning)

The main goal of this project is the [`prompts`](https://github.com/alluviali/rocketride/prompts) 'artifacts' directory

While we encourage metadata to specify `model`, actual inclusion of `responses` in the `chats` and `conversations` is frowned upon unless **novel** (or *time-enduring*) for ***many reasons***, but there **won't** be many pull requests merged for `chat.md`'s *with* `<`'s, ok? )

To offer a cleanup to the mess, there are three directories.  chat, conversations and prompts

## Quick example, chats
See [chats/org.nobodyknows/tdd/1.0.0/chat.md](chats/org.nobodyknows/tdd/1.0.0/chat.md) 

## Usage flow

General Usage by flow order, but not necessarily. All have `full coordinate ability` (i.e. dir structure)
- Chats
  - conversations starters, usually never leave versions 1.0.0
- Conversations
  - more formal, forkable conversation flows supported by `hash-versioning` (commonly used more like 'git commit hash' than a -SNAPSHOT, but no rules enforced).  Parent dir has a current pointer file, named `current`
- Prompts
  - output, generated or otherwise 

---

## *chats* (informal, with or w/o responses, messier than conversations)
`./chats` informal chats with optionally *included* responses.  Intended to be mind-forked, and includes some examples.  Please recontribute to this (organized), and to conversations (final products without the LLM responses).

## *conversations* (formal, hint of more longevity/forking value - with or without responses)
`./conversations` releasable conversations that may have optional *included* (partial) responses - which lead to creation of artifacts in `./prompts`  - they are generally intended for creative sharing and to foster iteration. A metadata file is included for citing sources in `metadata.md` which lives at the `artifact`, `version`, and/or `hash` level.  This is for automated doc tree building.  There is also a `summary.md` file that contains priority information (e.g. printed first in doc tree build).  If releasing, include the coordinate of the `chats`, if applicable, in the frontmatter.

## *prompts* (actual code-generating responses - with or without actual responses)
`./prompts` contain releasable prompts for specifically versioned creations. group/artifact/version/hash/ (e.g. com.bytesalot/superbeing/1.0.2/8ffjeu3basdohfsdf/).  If releasing, include the coordinate of the `conversations` and `chats`, if applicable, in the frontmatter.

---

Per directory files:

#### ***summary.md***
it's raw-concatenated by documentation tools

#### ***metadata.md***
it has stipulations (for processing). [see below](#metadata-format).  tl;dr: include model and source if you can!

* [`current`](#pointer-file) is often found in directories as well
---

## Metadata format

`model` ***optionally*** declared
```
model = gpt-4o
```

citations are simply defined as:
```source```

 ```
 source = (rocketride) artifact coordinte
 ```

 lines that do not start with `'alphanum ='` are treated as commentary (optional), followed by further sources, e.g.

 ```
 model: gpt-40

 source = com.pengit:sloppy:1.4.2:38dfhsdfuh3husdfhud

 source = uno.barkday:primemaster:1.0.2:9sdf8sfhsfuhf
 included their ideas about agents

 source = it.gerardo:react:3.5.3:73nsdufhdsfuh
 used some react generator ideas

 ```

## Pointer file
At any level in the coordinate may exist a file named `current` whose the contents (1 line) is the name of a subdirectory

A structure of:
groupId
|-- artifactId
|   |-- version
|   |   |-- hash

like:

org.nobodyknows
|-- tdd
|-- `current`
|   |-- 1.0.0
|   |-- `current`
|   |   |-- 8j4df84w9w
|   |   |-- Df3iseS3ge
|   |-- 1.0.1
|   |-- `current` 
|   |   |-- udg48dg39g
|   |   |-- 03dgDGEEjg

`current` 1 contains "1.0.1"
`current` 2 contains "Df3iseS3ge"
`current` 3 contains "03dgDGEEjg"

## General Structure example

`README.md`
`repositories.csv.md`
|-- conversations
|   |-- org.nobodyknows
|   |   |-- tdd
|   |   |-- `current`
|   |   |-- `summary.md`
|   |   |-- `metadata.md`
|   |   |   |-- 1.0.0
|   |   |   |-- `current`
|   |   |   |   |-- 8j4df84w9w
|   |   |   |   |-- Df3iseS3ge
|   |   |   |-- 1.0.1
|   |   |-- |-- `summary.md`
|   |   |-- |-- `metadata.md`
|   |   |   |-- `current` 
|   |   |   |   |-- udg48dg39g
|   |   |   |   |-- 03dgDGEEjg

* If no pointer file, `*default*` is the latest by git commit time

## About automated citation and documentation rendering
The (rocketride) `artifact coordinate` in `metadata.md` is to allow for automated pulling or documentation rendering of `summary.md` and `metadata.md` documentation. Run at a specified level, it can document the underlying component (and potentially pull in referenced) (e.g. find all cites for 'artifact' would trigger a recursive compilations of citations in the version and hash directories (while potentially pulling 'dependencies' docs from the central [alluviali/rocketride](github.com/alluviali/rocketride)` repo or external (depending on tool support).  

A basic documentation build tool outputs a tree structure (that orders by inclusion, then summary, then commit date).  Manual "overall" summary documentation exists in a separate file, `summary.md` which may exist also at each level - and is printed first in the automated tree of documentation, a respective levels


#### tools
 - tools/
  - doctree-generator/
   - gentree (TBD) generates automated documentation by parsing summary.md and metadata.md recursively, and can allude to thirdparty coordinates that may or may not exist in the main rocketride repository


## Links to compatible repos
Ecosystem enabled!

Rules on linking: projects' `repositories.csv.md` must reference `alluviali/rocketride` in the top 2 entries of the repositories.csv.md file
---
* By groupId, artifact-level unless necessary*

[alluviali/rocketride/prompts/org.nobodyknows/tdd]()

See the header in [repositories.csv.md](repositories.csv.md) for more information

[submit **minimal** pull requests](https://docs.github.com/en/pull-requests)
 //TODO find WYSIWYG inclusion tool for merging moderators

## Downstream
Links to projects that are > ~80% direct result of using existing (i.e. committed) [alluviali/rocketride/prompts](https://github.com/alluviali/rocketride/prompts)

## Repositories
Support for tooling or documentation that build and run from a variety of repos

`repositories.md` is CSV supports full and partial repos (by sub-coordinate)

groupId[:artifactId][:version][:hash],hreflink,"[prompts description]","[conversation description]","[chats descriptions]"
```
org.nobodyknows:https://github.com/alluviali/rocketride/

#full repo
io.friendlier:fflamerysio/mypromptz/

#artifact repo
io.friendlier:react-jula:fflamerysio/mypromptz/

#version repo
io.friendlier:react-jula:1.0.4:fflamerysio/mypromptz/

```

Comply with [alluviali/rocketride spec](https://github.com/alluviali/rocketride/README.md), [repository.md](repository.md) and other policy documents.


## Content policy
- Refer to content policy in repository.md

## Acceptancing Pulls, Maintenence, Deletion (though in history)
- Entries may disappear at any time, including but not limited to 
  - Maintenence, including Pruning
  - Removing previously accepted content due to changes in the Content Policy, as defined in `repository.md` or other `alluviali/rocketride` statements or will

## Pruning
 - won't prune `current` or those with a newer commit timestamp than the `current` file pointer
 
# License

Most content released under MIT license with exception of the /site directory, and other branding-related content and images specific to github.com/alluviali/rocketride

See [NOTICE](NOTICE), [LICENSE](LICENSE) for details