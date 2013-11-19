Javadoc Help for Emacs
======================

# About

Javadoc-Help is an add-on module for Emacs that let you jump to a Javadoc page in the browser. 
While editing in Emacs, you can place your cursor on a class name, hit a key (F1) to search 
through multiple online and local Javadocs, and jump to the Javadoc class documentation page
in the system web browser.

When working on Java projects, it's often needed to look up the Javadoc documentation of a class in JDK, 
in third party libraries, or in the current project.  Javadoc-Help allows you search through multiple 
javadocs quickly in Emacs, remote or local, and open up the found class in a browser.


# Feature Overview

* Search Java class name in multiple javadocs
* Support remote online javadoc (URL)
* Support local directory-based javadoc
* Interactive javadoc setup and management
* Search term as class, package, partial name, or regex.
* Allow selection among multiple matched results
* Open a class, its package, or the main index javadoc


# Installation:
  
Copy the javadoc-help.el file to your load-path directory.  It's usually at ~/elisp/.  It's set in your .emacs like this:

      (setq load-path (append (list (expand-file-name "~/elisp")) load-path))
  
Next add the following to your .emacs startup file.

      (require 'javadoc-help)


# Configuration
  
Assign the commands to some keys in your .emacs file.  Examples below assign a set of keys to the javadoc-help functions.

    (global-set-key [(f1)]          'javadoc-lookup)  ; F1 to lookup
    (global-set-key [(shift f1)]    'javadoc-help)    ; Shift-F1 to bring up menu

Javadoc-help uses Emacs' function browse-url to launch the system web browser.
Make sure it's working for your platform.  Try it out with, M-x browse-url.
Usually browse-url defaults to the OS default browser.  Some the OS default browser
might not be set up.  Use 'M-x customize-option' browse-url-browser-function
to pick a specific browser, (like setting Firefox as the browser to use).

