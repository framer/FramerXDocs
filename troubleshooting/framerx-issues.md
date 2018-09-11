# .framerx issues

Issues and/or confusion regarding the new .framerx format:

## Framer X documents no longer open or become empty. What now?

Framer X saves your designs and components in brand new  `.framerx`  containers. Unlike in previous versions where the document was simply a folder, you no longer edit things directly inside this file. Instead, every document gets a corresponding **package** folder that gets saved back to the  `.framerx`  file. To see what goes on in here, choose **File &gt; Show Project Folder**.

Aside from introducing a new file format, Framer X also adopts modern macOS saving behavior. Among other things, that means documents are saved automatically when you close the window. If you prefer to manually approve document saving, you can adjust the system-wide behavior in **System Preferences &gt; General &gt; Ask to keep changes when closing documents**.

To mimimize the odds of permanently losing data if something goes wrong with your document, observe the following steps:

* Move aside a copy of your  `.framerx`  file and of the corresponding package folder. Do **not** save or close your document before you have backed up these items. Compress them in the Finder to make sure they stay fully intact.
* If you think you lost canvas data, this is saved in **design/document.json**. Inspect if the file seems to contain your data or not. If missing or empty, you can still restore an older version from the automatic backup. To find them, make sure you're in the **package** folder in Finder. Choose **Go &gt; Go to Folder…** and enter ".backups". Click **Go** and you will see the list of backup zips Framer made. Find one where the document.json still contains your canvas information.
* If this does not help then please [contact us](https://framer.gitbook.io/framer/introduction#getting-help-and-support) and include the backed up  `.framerx`  file and **package** folder and we'll help you out best we can.

