# Building the Journal shell script

1. Get current date/time string (in Melbourne time)

`TZ='Australia/Melbourne' date`

2. Format the output

year:  %Y	(yyyy)
month: %m	(01-12)
day:   %d	(01-31)
hour:  %H	(00-23)
mins:  %M	(00-59)
day:   %A	(Monday)

3. Build the filename as an absolute path

Format: `journal_yyyy-mm.md`

```
filePath="/home/steve/Writings/journal_`TZ='Australia/Melbourne' date +%Y-%m`.md"
```

5. Build the entry title string (with markdown formatting)

```
title="## `TZ='Australia/Melbourne' date '+%Y-%m-%d %H%M %A'/n/n`" 
```

6. Add $title to the end of the file ${filePath}

```
echo -e $title >> ${filePath}
```


