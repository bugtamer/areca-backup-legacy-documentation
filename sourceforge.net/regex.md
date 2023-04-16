# Areca Backup at sourceforge.net (wiki)

## Regex

Regular expressions additional help ... don't hesitate to add your own examples / comments here


## Regular expressions quick reference :

Here is a listing of the most popular regular expression patterns.

| Rule                                                     | Syntax                                                     |
|----------------------------------------------------------|------------------------------------------------------------|
| Exactly one occurence of x                               | x                                                          |
| At least one occurence of x                              | x+                                                         |
| 0 or many occurences of x                                | x*                                                         |
| 0 or 1 occurence of x                                    | x?                                                         |
| Escape character                                         | \                                                          |
| Any single character                                     | .                                                          |
| One character in a predefined set                        | [list-of-characters] ... examples : [ABCD], [012345789]    |
| One character in a character range                       | [character1-character2] ... examples : [0-9], [a-zA-Z] ... |
| Any character except those contained in a predefined set | [^list-of-characters] ... examples : [^ABCD], [^0-9]       |
| Tab                                                      | \t                                                         |
| New line                                                 | \n                                                         |
| Carriage return                                          | \r                                                         |
| Beginning of the line                                    | ^                                                          |
| End of the line                                          | $                                                          |


## Examples :

| Example                           | Syntax          |
|-----------------------------------|-----------------|
| All filenames ending with ".html" | ^.*\.html$      |
| All filenames containing "client" | ^.*client.*$    |
| All folders containing "_svn"     | ^.*\\_svn\\.*$  |


---

This page has been deleted on 22:10, 5 September 2012 ([Areca Backup v7.2.12~7.2.13](../areca-backup.org/history.md#version-7213-released-on-2012-10-14))

[Top] | [Copyright (c) 2005-2015 Olivier PETRUCCI] | [archive.org]

[Top]: #areca-backup-at-sourceforgenet-wiki "Go to top of the document"
[Copyright (c) 2005-2015 Olivier PETRUCCI]: http://sourceforge.net/apps/mediawiki/areca/index.php?title=regex "Visit the original resource"
[archive.org]: http://web.archive.org/web/20120208040616/http://sourceforge.net:80/apps/mediawiki/areca/index.php?title=regex "Visit the original resource at archive.org"