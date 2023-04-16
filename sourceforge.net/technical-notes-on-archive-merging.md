# Areca Backup at sourceforge.net (wiki)

## Technical notes on archive merging

### <u>TECHNICAL NOTES ON MERGING ARCHIVES :</u>

Merges use a lot of bandwidth. This is mainly because Areca needs to create a NEW merged archive instead of working directly on the existing ones. This allows Areca to ensure that the existing archives won't be corrupted if an error occurs during the merge operation. (if an error occurs, it can simply destroy this new copy and keep the old ones unchanged)


More precisely, the bandwidth usage will depend on your backup configuration:


A) Standard archives

A.1) Not compressed or compressed as individual files :

In this case, Areca simply creates a copy of your archive's content somewhere on your storage device, and registers this copy as the new - merged - archive. Once it is done, it destroys the old ones so only the merged archive remains.

This involves :

- 1 READ of all your original archive
- 1 WRITE of your merged archiv 

A.2) Compressed as a single zip archive :

In this case, Areca first recovers (and merges) the content of your archives somewhere on your storage device, read these recovered files and creates a zip archive. Once it is done, it destroys the old archives as well as the temporarily recovered files.

This involves :

- 1 READ of all your original archives
- 1 READ and 2 WRITES of your merged archive (one for the recovery, and one for the creation of the final zip archive) 

B) Delta archives

B.1) Not compressed or compressed as individual files :

In this case, Areca directly reads your existing archives and create merged copies of your files (in this case, the merge process is more complicated because we deal with *parts* of files instead of whole files ... so it uses more CPU than standard archives)

This involves :

- 1 READ of all your original archives
- 1 WRITE of your merged archive 

B.2) Compressed as a single zip archive :

This case is the worst one : delta files stored in an archive can't be handled directly. So Areca first creates copies of your delta files on your storage device (as standard files/directories instead of zip archives), reads and merges these delta files (as in B.1) and then create a zip archive with the merged delta files.

This involves :

- 1 READ of all your original archives and 1 WRITE of these archives (as uncompressed files
- 1 READ of all your original (uncompressed) archives and 1 WRITE of your merged archive (as standard delta files
- 1 READ of these merged files and 1 WRITE to create the final zip archiv 

So if you want for instance to merge a 100 GB archive with a 1 kB one :

- Case A.1 will make Areca read about 100 GB and write 100 GB
- Case A.2 will make Areca read about 200 GB and write 200 GB
- Case B.1 will make Areca read about 100 GB and write 100 GB
- Case B.2 will make Areca read about 300 GB and write 300 GB 

Two possible optimizations :

1. Implement a client/server architecture to avoid transferring data over the network (case of a network drive for instance) during the merge operation (the whole operations are performed by the server)
2. Renounce to the transaction mechanism and work directly on the original archives : it would allow to reduce the the R/W operations to 0 in case A.1 (Areca could simply delete the old versions that it doesn't want to keep) 


---

This page has been deleted on 22:12, 5 September 2012 ([Areca Backup v7.2.12~7.2.13](../areca-backup.org/history.md#version-7213-released-on-2012-10-14))

[Top] | [Copyright (c) 2005-2015 Olivier PETRUCCI] | [archive.org]

[Top]: #areca-backup-at-sourceforgenet-wiki "Go to top of the document"
[Copyright (c) 2005-2015 Olivier PETRUCCI]: http://sourceforge.net/apps/mediawiki/areca/index.php?title=Technical_notes_on_archive_merging "Visit the original resource"
[archive.org]: http://web.archive.org/web/20120810003337/http://sourceforge.net/apps/mediawiki/areca/index.php?title=Technical_notes_on_archive_merging "Visit the original resource at archive.org"