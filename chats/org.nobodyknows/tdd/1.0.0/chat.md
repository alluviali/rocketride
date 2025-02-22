---
author: alluviali
copyright: copyright 2025 alluviali
source: https://github.com/alluviali/rocketride
name: TDD from then the now
goal: refresh my memory of TDD and how AI gen changes the development lifecycle.  Maybe make AI generate some code that passes tests ;)
summary: this was enlightening, discouraging, and
results: the model was ok, but was pretty confused about color rendering techniques
version-strategy: will make new version when conversation forks measurably.  will add new hashes for common fork points
---
## Tips for chats and conversations headers

* To make non-preprocessed more viewable, try to remember to add a header before the conversation contents, like # Conversation below

* Tip: include this for a "header" in chats.  Automated parsing begins at the *third* '---' (second section is summary).  There may be (suggested) frontmatter (copyrights, author, name, goal, summary, results, version-strategy) before this content which may not be visible in a markdown reader.

* pre-process with Jekyll to use frontmatter keys in this section e.g. # {{ name }}

* Note, this is markdown, but the underlying file format is:
```
`>` (*to* chat) and 
`<` (*from* chat, rare) and 
`<-` (human response summary of chat)
`<--` (human reaction to the response)

tip: wrap `<`, `<-`, `<--` in triple-backticks for easier readability
``` 
---
# Conversation
 

> do you know what TDD is?

> I'd like to create a code project that takes a spec file and outputs code.  I want it to be based on a spec file.  The spec file should contain these sections: list of interfaces, an object hierarchy. 

> can you recommend formats that already exist?
```
<- openAPI
<- custom JSON
<- UML
<- protocol buffers
```

> I need it to be fully capable of expressing, at a minimum, Java interfaces, and method signatures
```
<- oh.
<-- yeah, that reminds me of a lot of decades I spent building knowledge, what an interesting future is coming!  I'm glad I know pain.
```

