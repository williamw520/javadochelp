Javadoc Help for Emacs
======================

## About

Javadoc-Help is an add-on module for Emacs that let you jump to a Javadoc page in the browser. 
While editing in Emacs, you can place your cursor on a class name, hit a key (F1) to search 
through multiple online and local Javadocs, and jump to the Javadoc class documentation page
in the system web browser.

When working on Java projects, it's often needed to look up the Javadoc documentation of a class in JDK, 
in third party libraries, or in the current project.  Javadoc-Help allows you search through multiple 
javadocs quickly in Emacs, remote or local, and open up the found class in a browser.


## Feature Overview

* Search Java class name in multiple javadocs
* Support remote online javadoc (URL)
* Support local directory-based javadoc
* Interactive javadoc setup and management
* Search term as class, package, partial name, or regex.
* Allow selection among multiple matched results
* Open a class, its package, or the main index javadoc


## Installation:
  
Copy the javadoc-help.el file to your load-path directory.  It's usually at ~/elisp/.  It's set in your .emacs like this:

    (setq load-path (append (list (expand-file-name "~/elisp")) load-path))
  
Next add the following to your .emacs startup file.

    (require 'javadoc-help)
  
Assign the commands to some keys in your .emacs file.  Examples below assign a set of keys to the javadoc-help functions.

    (global-set-key [(f1)]          'javadoc-lookup)  ; F1 to lookup term on the configured Javadocs.
    (global-set-key [(meta f1)]     'javadoc-help)    ; Meta-F1 to bring up the Javadoc-help menu to set up Javadocs.

Note that Javadoc-help uses browse-url to launch the system web browser.
Make sure it's working in Emacs.  Try it out with M-x browse-url.  Usually
browse-url is set to the OS default browser.  Some OS might not have default 
browser set up.  Use 'M-x customize-option' browse-url-browser-function
to pick a specific browser, like setting Firefox as the browser to use.

## Javadoc-help Setup and Usage

Set up the javadocs by going to the Javadoc-help setup menu (Meta-F1).
Add an online url-based javadoc using the 'u' command, or add a local
file-based javadoc using the 'f' command.  The online javadoc url 
should point to the main index directory of the javadoc, e.g. 
http://commons.apache.org/proper/commons-lang/javadocs/api-release/.
The local file javadoc path should point to the directory containing
the allclasses-frame.html file, e.g. c:/jdk/docs/api/ or /opt/jsee/docs/api/.

After adding the javadoc url, try the 'o' command key to open the main
index page of the javadoc in the browser.

To look up the javadoc for a class, invoke the javadoc-lookup (F1) command.
Type in the name to look up.  The name near the cursor in the current buffer
is automatically used as the initial input.  The search term can be a partial
class name, a package name, or it can be a regex.  For example,

    Connection
    String
    .*lang.*String
    java.io

The lookup might produce multiple matches.  The *Javadoc-Search-Result* 
window offers a number of commands to launch the browser on the class,
the package, or the main javadoc page.

The search term history is accessable via the up/down arrows during input.

If you prefer setting up the javadoc urls in your .emacs file, you can call
javadoc-set-predefined-urls in .emacs to set up the pre-defined javadoc urls.

    e.g.
    (javadoc-set-predefined-urls '("c:/jdk/docs/api" "/opt/jsee/docs/api"))

Note that the allclasses-frame.html of online javadoc url is downloaded to
~/.javadoc-cache for faster access.  If the online verison has changed, use
the refresh command ('r') in the Javadoc-help setup menu to re-download the
new version.

## Uninstall and Cleanup

Besides the javadoc-help.el file, there are two places that have javadoc-help
generated files.  1. ~/.javadoc-help is the configuration file.  2. ~/.javadoc-cache
contains the downloaded allclasses-frame.html files from online javadocs.

