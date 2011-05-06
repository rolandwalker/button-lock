Overview
--------

Modern people using modern Emacs usually look at screens marked up with
font-lock (aka syntax highlighting).  Sometimes modern people even use a
mouse.

This package provides

* *button-lock:* a programmer-friendly library for making text mouseable

* *wiki-nav:* a user-friendly library for making text mouseable

Because these packages are based on font-lock, they are efficient.

button-lock
-----------

Button-lock uses font-lock to make text clickable.  In Emacs-speak: it
creates font-lock keywords which have mouse bindings added to their
text properties.

Button-lock has a simple interface that works like this

	(button-lock-set-button "http://google.com" 'browse-url-at-mouse)

However, button-lock does not create any buttons by default.  You must write
some Lisp code to make it do anything.

For much more information, see the source for button-lock.el and the doc
string for button-lock-set-button.

wiki-nav
--------

Wiki-nav is a user-friendly high-level interface to button-lock.  It
provides a minor mode which recognizes [[wiki-style]] double-bracketed
navigation links in any type of file. Links let the user jump between
sections, between files, or open external URLs.

Example usage:

1. Put `button-lock.el` and `wiki-nav.el` on your Emacs `load-path`
directory.  If you've never heard of a `load-path` directory, create a new
directory named `~/.emacs.d/lisp`, and add this code to your `~/.emacs` file

		(add-to-list 'load-path (expand-file-name "~/.emacs.d/lisp"))

2. Add the following to your `~/.emacs` file

		(require 'wiki-nav)
		(global-wiki-nav-mode 1)

3. Sprinkle double-bracketed

		[[links]]

	in your files.  That's it.  There's more functionality, but simple [[links]]
	may be all you need.  When you click on [[links]], Emacs jumps forward in
        the file to the next matching link.

Advanced usage:

Bracketed links may contain external URLs

	[[http://google.com]]

Or they may use various internally-recognized URI schemes:

	visit: navigates to another file

		[[visit:/etc/hosts]]

		[[visit:/path/to/another/file:NameOfLink]]

	func: navigates to the definition of a function

		[[func:main]]

	line: navigates to a line number

		[[line:12]]

	visit: may be combined with other schemes:

		[[visit:/path/to/another/file.c:func:main]]

		[[visit:/etc/hosts:line:5]]

Path names and similar strings are subjected to URI-style unescaping before
lookup.  To link to a filename which contains a colon, substitute "%3A" for
the colon character.

For much more information, see the source for wiki-nav.el.

Prior Art
---------
The following packages provide functionality that is similar to button-lock
or wiki-nav.

hi-lock.el   
David M. Koppelman <koppel@ece.lsu.edu>

buttons.el   
Miles Bader <miles@gnu.org>

linkd.el   
David O'Toole <dto@gnu.org>

org-mode   
Carsten Dominik &lt;carsten at orgmode dot org&gt;

