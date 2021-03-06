Plain Text Wiki
===============

Plain Text Wiki is a TextMate bundle which allows you to use a directory of 
text files as a simple wiki.

The original bundle was by Matt Webb <http://interconnected.org/home>.
The current version by Matt Foster is available on [GitHub](http://github.com/mattfoster/plaintextwiki-tmbundle/tree/master "mattfoster's plaintextwiki-tmbundle at master &mdash; GitHub").
Support for subdirectories is now available thanks to Marcelo Alvim [malvim on GitHub](http://github.com/malvim). His fork may be found [here](http://github.com/malvim/plaintextwiki-tmbundle/tree/master "malvim's plaintextwiki-tmbundle at master &mdash; GitHub").

Installation
------------

Download and unzip Plain-Text-Wiki.zip. Double-click on the bundle to install 
(the bundle requires TextMate: <http://macromates.com>). 

Alternatively, use GetBundles. 

First, run:

	cd ~/Library/Application\ Support/TextMate/Bundles
  	svn co http://svn.textmate.org/trunk/Review/Bundles/GetBundles.tmbundle/
	osascript -e 'tell app "TextMate" to reload bundles'

to get GetBundles and reload TextMate. Then find `GetBundles` in the `Bundles` menu, and run `Get Bundles`.
You can then search for PlainTextWiki, and hit install to grab and install it.

Usage
-----

* Create a new directory
* In TextMate, choose 'Create New Wiki' from the menu 
  Bundles > Plain Text Wiki
* Select your new directory. A file 'IndexPage.txt' will be created and opened
* Reference new pages using CamelCase or &#0091;&#0091;like this&#0093;&#0093;. Page names will appear 
  underlined
* To follow a link, put the text cursor over a page name and hit (⌅) Enter (not Return, ↩)

Return to the index page at any time: Type ⌃⇧I (shift+ctrl+i)

Insert a list of pages by typing `pagelist` and hitting tab. It's a good idea to do this in the index page, and update it regularly.


Subdirectories
--------------

Malvim added support for subdirectories to the plaintextwiki bundle, by modifying it in the following ways:

* If you reference a page &#0091;&#0091;like/this&#0093;&#0093;, the page will be in &lt;current-directory&gt;/like/this.txt
* The `pagelist` command inserts a list of pages under the current directory (the directory of the file where you added the pagelist), recursively (so `pagelist` on IndexPage.txt will insert a list of all the pages in the wiki)
* &#0091;&#0091;/abslolute/links&#0093;&#0093; are supported (for instance: &#0091;&#0091;/indexpage&#0093;&#0093; anywhere is a link to the index page)
* `pagelist` will also only list pages whose names end in '.txt'; That way, you can store other files inside your wiki for reference, but it won't try to open them


Export as HTML
--------------

Choose `Export Wiki as HTML` from the Plain Text Wiki commands menu. You will 
be prompted for a directory where the Web pages will be saved (please make 
sure it's empty).

For converting text to HTML, Plain Text Wiki understands [Markdown](http://daringfireball.net/projects/markdown/syntax "Daring Fireball: Markdown Syntax Documentation"). 

To customise the HTML of the wiki, add `wiki-styles.css` to the project 
directory--it'll be copied to the export directory and included.

For more control, add `wiki-header.html` and `wiki-footer.html` to the project 
directory. Include the string "%s" in `wiki-header.html` to have that replaced 
with the page title on export. Similarly two string markers in `wiki-footer.html` will be replaced with the time and current user.

Bugs and issues
---------------

* Export to HTML seems to be broken in this fork

Please repot any bugs. Patches are welcome! Feel free to fork on GitHub [here](http://github.com/mattfoster/plaintextwiki-tmbundle/tree/master "mattfoster's plaintextwiki-tmbundle at master &mdash; GitHub") or [here](http://github.com/malvim/plaintextwiki-tmbundle/tree/master "malvim's plaintextwiki-tmbundle at master &mdash; GitHub").

Issues:

* Bundle needs to adhere to http://macromates.com/wiki/Bundles/StyleGuide
* Grammar binds to a number of file extensions, but exports only '.txt'

Changes
-------

2009-01 (Marcelo Alvim)

* Added support for absolute links (&#0091;&#0091;/indexpage&#0093;&#0093;, for instance)

2008-12 (Marcelo Alvim)

* Added support for creating links with slashes in the middle (subdirectories)
* Changed 'go to index page' to go to the root of the project, not the current directory
* Various refactorings to ruby scripts
* Added (very little) debugging support and testing 

2008-11 (Matt Foster)

* Updated footer-html
* Merged markdown grammar
* Added nodebox visualisation script
* Various changes to ruby scripts

2007-06-10:

* Fixed Create New Wiki command (which was not working)

2007-06-09:

* Added 'Insert Page List'
* 'Follow Page Link' now ignores case when looking for a text file to open
* Export now looks for wiki-styles.css, wiki-header.html and wiki-footer.html
* Various bugs fixed in way Export adds HTML links
* Export prompts to replace files in the export directory


Miscellaneous
-------------

More background to Plain Text Wiki:
http://interconnected.org/home/2007/05/20/plain_text_wiki