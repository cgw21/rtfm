#  what 
RTFM is a great and useful book, BUT a bit pointless when you have to transcribe it, so this little program will aim to be the spiritual successor to it.

I would recommend picking up a copy of the book from amazon, it is pretty handy to have!

# Usage 
```
e: rtfm.py [OPTIONS]

For when you just cant remember the syntax, you should just RTFM

Options:
  --version             show program's version number and exit
  -h, --help            show this help message and exit
  -t TAG, --tag=TAG     Specify one or more tags to look for (a,b,c)
  -c CMD, --cmd=CMD     Specify a command to search (ls)
  -R, --ref             Show the referances for cmd ID (1)
  -p PRINTER, --print=PRINTER
                        Print Types : P(retty) p(astable) w(iki) h(tml)
  -i INSERT, --insert=INSERT
                        Insert c(ommand) | t(ags) r(eferances)
  -D DUMP, --dump=DUMP  Just Dump infomration about
                        t(ags)|c(commands)|r(eferances)a(ll)
  -d, --debug           Display verbose processing details (default: False)
  -u, --update          Check for updates (default: false)
  -v                    Shows the current version number and the current DB
                        hash and exits
```

Search for the tag 'intersting'
`./rtfm.py -t interesting`


Search for the command psexec.py
```
./rtfm.py -c rtfm

++++++++++++++++++++++++++++++
Command ID : 0
Command    : RTFM

Comment    : helpception
Tags       : Linux
Date Added : 2017-01-30
++++++++++++++++++++++++++++++
```
Show us all windows commands with the term psexec
`./rtfm.py -t windows -c psexec`

Show us all the current tags
`./rtfm.py -D t`

Sql inject to get more than one search . . .oops
`./rtfm.py -c "psexec'% or cmd like '%samrdump"`

Pull Updates to the DB
`./rtfm.py -u`

The updates are 'safe' in the form they wont write over your DB, git pull is not a safe update

Add a tag to the CMD
`./rtfm.py -i t`


Insert commands into the db
`./rtfm.py -i c`

On all of these, I have tried to add 'debug' calls '-d'

There is also a number of output options, such as copy any paste, pretty, wiki and HTML:
```
23:15:root:snips: ./rtfm.py -c rtfm -p p
++++++++++++++++++++++++++++++
RTFM

helpception
++++++++++++++++++++++++++++++

23:15:root:snips: ./rtfm.py -c rtfm -p P
+-------------+-------------+
| Command ID  | 0           |
+-------------+-------------+
| Command     | RTFM        |
|             |             |
| Comment     | helpception |
| Tags        | Linux       |
| Date added  | 2017-01-30  |
+-------------+-------------+

```
# TODO 
 * Lots, this is an alpha so far
 * The 'important' functionality is present, but still lots of work to do

##Fixes:
  * Indexes on comments
  * Probably should use prepared statements: local so don't care
  * Check for dupe tags
  * Warn on dupe tags
  * Working DB check

##Pipeline:
  * Output format to allow easy sync
     Dump cmd, then null ids, tags and tag contetns, inefficent but maybe the only way?
     cmd|tagcontent|tagmap
  * Swap to more sophisticated SQL, quite innefficent at the moment
  * Populate referances table
  * update                   : u <db|program>
  * insert line               : i <Referance>
  * "dump" tags, commands, refances : D <all|referances>
  * Search - Case sensitve versions : T and C 
  * Create a HTML page           : H
  * create a WIKI format           : W
  * Remark (comment)  Search          : r
  * Drop to SQL Shell               : s
  * Template engine(autofill [user] : A user=innes,pass=password,attacker=1.1.1.1,victim=2.2.2.2
  * Make code more sane and betterize the layout 

##Future:
  * Cool Thing mode
  * teach me mode
  * Quiz me mode? 
  * Fix the typos

# Credits 
The people that deserve the credits will be in the reference table of the DB. They are the ones doing the work!
This initial release does not have this yet, though it is planned!

# Thanks
Thanks in no particular order :) : 
@VC
@Rekzon
