---
Title: How to Save Your Database Changes
Sort: 3
---
To keep a copy of the changes you make to a Dokkan database you want to keep a `diff` file. This is also the primary way to move changes to a new, fresh database.

A `diff` file is a text file that contains a list of [SQL statements](https://codingsight.com/structured-query-language-importance-of-learning-sql/). These SQL statements can be executed one by one and applied to a new database. A `diff` file is also the primary way Creator's add database modifications to their patches.

<br/>

### How to make a `diff` file?
You need your modified database and the original unmodified copy of the same version of database. 

If you have access to the Creator's tools, you have access to an online `diff` creator tool. This tool will attempt to make an optimized `diff` file appropriate for inclusion in a patch. 

If you do not have access to the Creator's tools, and you are on Windows, follow these steps:

 1. Download SQLite tools from [https://www.sqlite.org/download.html](https://www.sqlite.org/download.html). The correct download is named `sqlite-tools-win32-x86-3290000.zip`
	<br /><br />
 2. Using a Zip program of choice (7zip, Winrar, windows built-in), extract the tools to a folder. In my example, I placed the files at `C:\sqlite-tools-win32-x86-3290000\`<br />
	 <img src="https://cdn.discordapp.com/attachments/528713422498562078/609847075118776322/ExtractedFiles.png" width="400">
	 <br /><br />
 3. Place your modified and original version of the database files in that folder.<br />
	 <img src="https://cdn.discordapp.com/attachments/528713422498562078/609847078608306203/Databases.png" width="400">
	 <br /><br />
 4. Open a Command Prompt `cmd.exe` or Powershell `powershell.exe` from either your Windows Start Menu or Windows Run.
	 <br /><br />
 5. Instruct the shell window to navigate to the folder above by typing the following command, followed by enter:
	 ```cmd
	 cd C:\sqlite-tools-win32-x86-3290000\
	 ```
	 `cd` means __c__hange __d__irectory. 
	 <br />
	 <img src="https://cdn.discordapp.com/attachments/528713422498562078/609847077069127708/changedirectory.png" width="400">
	 <br /><br />
 6. Now, instruct the shell window to execute the following command to create your `diff` file:
	```powershell
	.\sqldiff.exe --primarykey original.db modified.db > diff.sql
	```
	* `.\sqldiff.exe` is the program you are executing
	* `--primarykey` is an option for `sqldiff` that will force it to compare changes with the `id` column.
	* `original.db` is the path to your original database
	* `modified.db` is the path to your modified database
	* `> diff.sql` means you are redirecting the output of `sqldiff` to a file named `diff.sql`
	<br /><br />
 7. Now you will have a `diff.sql` file in the same folder.<br />
	 <img src="https://cdn.discordapp.com/attachments/528713422498562078/609847073382072321/diffoutput.png" width="400">
	 <br />
	 You will see one or more lines that look like this:
     
	 ```sql
	 UPDATE cards SET name='New Card Name Here' WHERE id=1000010;
	 ```

**__Important Note__:** You will not get an error if you try and diff two different database versions. What will end up happening is you will get a `diff` file that does not have any content, or way too much content. Please be careful to use matching database versions.

<br/><br/>

### How to use a `diff` file?

 1. Open a database in your SQLite editor of choice ([DB Browser for SQLite](https://sqlitebrowser.org/) is my choice on Windows).
 2. Find the `Execute SQL` option in your SQLite editor. For DB Browser, it's a tab named `Execute SQL`.
 3. Open your `diff` file or copy/paste it into the text window. 
 4. Execute the `diff` SQL. For DB Browser, there is a play button.

#### Troubleshooting

Sometimes, applying your `diff` file will give you an error. This is likely because the data you are trying to import conflicts with data that is already present. 

Depending on the error, you will have to modify your `diff` file to compensate. 