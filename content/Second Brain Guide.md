---
date created: Fri, Nov 1st 2024, 8:34 pm
date modified: Wed, Nov 6th 2024, 4:48 pm
tags:
  - reference
---
- [Todo](#todo)
- [My essential thought](#my-essential-thought)
  - [My notes rule](#my-notes-rule)
- [folder note + waypoint plugin](#folder-note--waypoint-plugin)
- [index note](#index-note)
    - [1. Index Note](#1-index-note)
    - [2. Meta-Index Note](#2-meta-index-note)
    - [Example Use Cases](#example-use-cases)
- [Dataview](#dataview)
- [Reference](#reference)
- [Obsidian Logitics Youtuber](#obsidian-logitics-youtuber)
- [PARA: Project, Area, Resources, Aricheve](#para-project-area-resources-aricheve)
- [Obsidian Showcase](#obsidian-showcase)
  - [Source to find some others showcase](#source-to-find-some-others-showcase)
- [Obsidian-Zotero](#obsidian-zotero)
  - [trim space between list nested](#trim-space-between-list-nested)
  - [Remove space + trim space between list nested](#remove-space--trim-space-between-list-nested)
  - [zotero extract meta data](#zotero-extract-meta-data)
- [Pseudocode](#pseudocode)
- [May Check Plugin](#may-check-plugin)
- [Obsidian help](#obsidian-help)

MOC stands for Map of Content, it is the index of the content, easy to check knowledge base

# Todo

classify the editing notes and complete notes

# My essential thought

Obsidian or Roam research and so on with graph view is widely used due to [Zettelkasten Method](https://zettelkasten.de/overview/)The essential is that we need to create the **unique identifier of each note** and **tags instead of category folder**, I will use create date, time and hierarchy tags to make indexes of tags and index of tags Indexs

> "A note is an object, a folder (if you need them) a category/topic and a tag is a status"

Is this true? No, in my brain, note is an object, tags are topics and status, no folder

## My notes rule

[Callouts - Obsidian Help](https://help.obsidian.md/Editing+and+formatting/Callouts)

> [!tip] Piece to Whole:
>
> 1. a piece of knowledge and the whole brain. where should the KL divergence notes put? Statistics or Machine Learning but this note can be the part of the note for diffusion note or VAE note too. Tag or Wiki link is the way to connect piece to the whole. It also follows the common idea: "Have notes first, then do some organization". Try to write notes as many as I can to form a vault, then index them to find and tag or wiki link them to find connection. Similar to how my brain works.
> <I got this insight when check [The Quantum wall](https://publish.obsidian.md/myquantumwell/Knowledge+Management) - a published obsidian vault>
> 2. For a bunch of piece knowledge, such as linear algebra, I put them in one note; If I am 100% sure its belongings, e.g oop definitely belongs to computer science, tag it with cs
> This is the form of my brain.

# folder note + waypoint plugin

# [index note](https://github.com/adanielnoel/obsidian-index-notes)

![[indexnoteplugin.gif]]
In the **Obsidian Index Notes** plugin, there are two main types of index notes you can create: **Index Note** and **Meta-Index Note**. Here’s an explanation of each:

### 1. Index Note

An **Index Note** is a note that contains a list or table of notes within a specific category or tag. This type of note is useful for organizing related notes by displaying an index based on tags or a hierarchy of tags.

- **How to Create**:
  - To create an index note, add a tag with the suffix `/idx` to any note. For example, if you want an index of all notes related to projects, use the tag `#projects/idx`.
  - After a few seconds, the plugin will automatically populate the note with an index block that lists all notes tagged under `#projects`.

- **Purpose**:
  - The index note allows you to quickly view and access all notes associated with a specific tag or category. This can be used as a structured, organized way to navigate through grouped content.

### 2. Meta-Index Note

A **Meta-Index Note** is a higher-level index that links to multiple index notes within your vault. It essentially functions as an index of indexes, making it easier to manage various categories or tags across your vault.

- **How to Create**:
  - To create a meta-index note, add a tag with the suffix `/meta_idx`. For example, `#meta_idx` will create a meta index of all the index notes in your vault.
  - This meta-index note will contain links to other index notes, such as `#projects/idx`, `#university/idx`, etc.

- **Purpose**:
  - The meta-index note serves as a centralized hub for all index notes, making it easy to navigate between different categories or topic areas without needing to manually find each index note.

### Example Use Cases

- **Index Note**: Use `#projects/idx` to automatically create an index of all notes related to projects, where you can see all individual project notes listed.
- **Meta-Index Note**: Use `#meta_idx` to gather links to all index notes (e.g., `#projects/idx`, `#university/idx`, etc.), allowing for easy navigation across various topics in your vault.

# Dataview

```dataview
TABLE WITHOUT ID (tag + "(" + length(rows.file.link) + ")") AS Tags, link(sort(rows.file.name)) AS Files
FROM ""
WHERE file.tags 
FLATTEN file.tags AS tag 
GROUP BY tag
SORT length(rows.file.link) DESC
```

# Reference

[Creating a tag index table with Dataview - Obsidian Forum](https://forum.obsidian.md/t/creating-a-tag-index-table-with-dataview/23997/11)

# [Obsidian Logitics Youtuber](https://www.youtube.com/watch?v=hSTy_BInQs8&t=1247s)

1. rough note
1. anything temp, rough note
2. source material
1. anything consumed, eg. article, papers, podcast, video
2. working on consuming
3. Tags
1. use wiki link as tags instead of # to create tags -> easy to see the backlinks and create index
4. Indexs:
1. put all backlinks of a tag into this "tag" file. eg. tags "ml", this will be a ml note in indexes folder to show all files with ml tags(since we are using wiki link as tags intead of #, so the files in this file will be all backlinks)
5. Template
6. Full notes
7. hashtags: baby, child, adult (grandparent, parent, child) to see if it need more work/time. baby needs more work and time,

![[obsidian_youtuber.png]]

# PARA: Project, Area, Resources, Aricheve

[The PARA Method: The Simple System for Organizing Your Digital Life in Seconds](https://fortelabs.com/blog/para/)
![[PARA.png]]

# Obsidian Showcase

1. [My simple productive setup](https://www.reddit.com/r/ObsidianMD/comments/1fst6xj/my_simple_productive_setup/)
2. Showcase of obsidian help![[obsidianhomepage.png]]
1. I believe this should be the ideal format of the notes, clear, no redundancy
3. [Library - LYT Kit](https://notes.linkingyourthinking.com/Atlas/Library)
4. [Knowledge Management - The Quantum Well - Obsidian Publish](https://publish.obsidian.md/myquantumwell/Knowledge+Management) : this one looks pretty good for me at least but it really takes much time to categorize which is not I want

## Source to find some others showcase

[Really cool obsidian vaults to play around with](https://www.reddit.com/r/ObsidianMD/comments/wxrtup/how_can_i_check_out_some_really_cool_obsidian/)
[GitHub - MaggieAppleton/digital-gardeners](https://github.com/MaggieAppleton/digital-gardeners?tab=readme-ov-file)

# Obsidian-Zotero

[Foam | A personal knowledge management and sharing system for VSCode](https://foambubble.github.io/foam/)

> [!meta]- Metadata
> abstract:: {{abstractNote}}
> zotero_link:: {{pdfZoteroLink}}
> url:: {{url}}
> doi:: {{doi}}
> bibliography:: {{bibliography}}

---

## trim space between list nested

```
${{

mdContent = mdContent.replace(/(\d+\.\s[^\n]+)\n\s*\n(?=(\d+\.)|(\s+\d+\.)|\s*[-*]\s|\s+[-*]\s)/g, '$1\n');

return mdContent.replace(/\\\[/g, '[').replace(/\\\]/g, ']').replace(/\\\(/g, '(').replace(/\\\)/g, ')');

}}$
```

## Remove space + trim space between list nested

````
${{

// Clean up line breaks and special characters

mdContent = mdContent.replace(/(\d+\.\s[^\n]+)\n\s*\n(?=(\d+\.)|(\s+\d+\.)|\s*[-*]\s|\s+[-*]\s)/g, '$1\n')

.replace(/\\/g, ''); // Remove all backslashes

// Remove triple backticks and any surrounding whitespace, ensuring both the opening and closing are removed

mdContent = mdContent.replace(/^\s*```[^\S\r\n]*\n?/, '').replace(/[^\S\r\n]*```[^\S\r\n]*$/g, '').trim();

// Remove triple backticks immediately after the closing '---'

mdContent = mdContent.replace(/---\n\s*```[^\S\r\n]*\n?/, '---\n');

// Ensure there is no extra space above the first '---'

mdContent = mdContent.replace(/^\s*---/m, '---');

// Remove any extra newline or space after the closing '---'

mdContent = mdContent.replace(/---\n\s*\n/, '---\n');

return mdContent;

}}$
````

---

title: "{{title}}"
authors: {{ authors }}
year: {{ date | format("YYYY") }}
publisher: {{ publicationTitle }}
url: {{ url }}

---

## [zotero extract meta data](https://forums.zotero.org/discussion/75796/how-to-retrieve-and-update-metadata-in-zotero)

```java
var items = Zotero.getActiveZoteroPane().getSelectedItems();
let item = items[0]
let identifier =
{
itemType: "journalArticle",
DOI: item.getField('DOI')
};
var translate = new Zotero.Translate.Search();
translate.setIdentifier(identifier);
let translators = await translate.getTranslators();
translate.setTranslator(translators);
let newItems = await translate.translate();
let newItem = newItems[0];

function update(field){
if (newItem.getField(field)){
item.setField(field,newItem.getField(field))
}
}
item.setCreators(newItem.getCreators());

// 可根据下述网址增减需要更新的Field.
// [https://www.zotero.org/support/dev/client_coding/javascript_api/search_fields](https://www.zotero.org/support/dev/client_coding/javascript_api/search_fields)

let fields=["title","publicationTitle","journalAbbreviation","volume",
"issue","date","pages","issue","ISSN","url","abstractNote"
]

for (let field of fields){
update(field);
}

newItem.deleted = true;
item.saveTx();
await newItem.saveTx();
return ("成功！");
```

cmd+shift+s, in read mode

# Pseudocode

```pseudo

    \begin{algorithm}
    \caption{Quicksort}
    \begin{algorithmic}
      \Procedure{Quicksort}{$A, p, r$}
        \If{$p < r$}
          \State $q \gets $ \Call{Partition}{$A, p, r$}
          \State \Call{Quicksort}{$A, p, q - 1$}
          \State \Call{Quicksort}{$A, q + 1, r$}
        \EndIf
      \EndProcedure
      \Procedure{Partition}{$A, p, r$}
        \State $x \gets A[r]$
        \State $i \gets p - 1$
        \For{$j \gets p$ \To $r - 1$}
          \If{$A[j] < x$}
            \State $i \gets i + 1$
            \State exchange
            $A[i]$ with $A[j]$
          \EndIf
        \State exchange $A[i]$ with $A[r]$
        \EndFor
      \EndProcedure
      \end{algorithmic}
    \end{algorithm}
```

# May Check Plugin

[Breadcrumbs](https://publish.obsidian.md/hub/04+-+Guides%2C+Workflows%2C+%26+Courses/Guides/Breadcrumbs+Quickstart+Guide) - parents, child, grandparent. set relationship between notes; useful when set prerequisite of a piece of knowledge, a piece of knowledge and whole knowledge. hard to adapt, no time to maintain;

# Obsidian help

Note: remember to set mode as source mode to see the reference
[Obsidian 中文帮助](https://publish.obsidian.md/help-zh/%E7%94%B1%E6%AD%A4%E5%BC%80%E5%A7%8B)
[Obsidian Markdown reference](https://help.obsidian.md/Home)
[Advanced URI Documentation](https://publish.obsidian.md/advanced-uri-doc/Home)
