GREP COMMANDS
===============================================================================
_by Ingo Karkat_

DESCRIPTION
------------------------------------------------------------------------------

This plugin defines variants of the built-in :vimgrep command which target
all arguments, listed buffers, windows in the current tab page or all tab
pages for its search. Additionally, the search defaults to the last search
pattern, so using these commands is often much faster than building the
equivalent search with :vimgrep.

### SEE ALSO

- The GrepHere plugin ([vimscript #4191](http://www.vim.org/scripts/script.php?script_id=4191)) provides a :GrepHere command that
  covers only the current buffer.

### RELATED WORKS

- This is a modern re-implementation of the similar commands defined by
  greputils.vim ([vimscript #1062](http://www.vim.org/scripts/script.php?script_id=1062)), which hasn't been updated since 2005.
- brep ([vimscript #3653](http://www.vim.org/scripts/script.php?script_id=3653)) can grep buffers (also unlisted with [!]) and show
  them in the quickfix list.
- greplace ([vimscript #1813](http://www.vim.org/scripts/script.php?script_id=1813)) can search buffers and arguments; it shows the
  matches in a special replace buffer that can be edited and incorporated into
  the original files.
- vim-lister (https://github.com/tommcdo/vim-lister) also has (among others)
  an :Agrep command.

USAGE
------------------------------------------------------------------------------

    :ArgGrep[Add][!] [{pattern}]
    :ArgGrep[Add][!] /{pattern}/[g][j]
                            Search for {pattern} (or last search pattern if
                            omitted) in all files from the argument-list and set
                            the error list to the matches.
                            Same as :vimgrep {pattern} ##.

    :BufGrep[Add][!] [{pattern}]
    :BufGrep[Add][!] /{pattern}/[g][j]
                            Search for {pattern} (or last search pattern if
                            omitted) in all listed buffers and set the error list
                            to the matches.

    :WinGrep[Add][!] [{pattern}]
    :WinGrep[Add][!] /{pattern}/[g][j]
                            Search for {pattern} (or last search pattern if
                            omitted) in all buffers visible in the current tab
                            page and set the error list to the matches.

    :TabGrep[Add][!] [{pattern}]
    :TabGrep[Add][!] /{pattern}/[g][j]
                            Search for {pattern} (or last search pattern if
                            omitted) in all buffers visible in all tab pages and
                            set the error list to the matches.

INSTALLATION
------------------------------------------------------------------------------

The code is hosted in a Git repo at
    https://github.com/inkarkat/vim-GrepCommands
You can use your favorite plugin manager, or "git clone" into a directory used
for Vim packages. Releases are on the "stable" branch, the latest unstable
development snapshot on "master".

This script is also packaged as a vimball. If you have the "gunzip"
decompressor in your PATH, simply edit the \*.vmb.gz package in Vim; otherwise,
decompress the archive first, e.g. using WinZip. Inside Vim, install by
sourcing the vimball or via the :UseVimball command.

    vim GrepCommands.vmb.gz
    :so %

To uninstall, use the :RmVimball command.

### DEPENDENCIES

- Requires Vim 7.0 or higher.
- Requires the ingo-library.vim plugin ([vimscript #4433](http://www.vim.org/scripts/script.php?script_id=4433)), version 1.012 or
  higher.

LIMITATIONS
------------------------------------------------------------------------------

- Unnamed buffers cannot be searched via :vimgrep. When the scope of the
  search contains only unnamed buffers, "E683: File name missing or invalid
  pattern" is issued.

### CONTRIBUTING

Report any bugs, send patches, or suggest features via the issue tracker at
https://github.com/inkarkat/vim-GrepCommands/issues or email (address below).

HISTORY
------------------------------------------------------------------------------

##### 1.02    29-Nov-2016
- Internal API changes to enable :GrepHere within a [range].
- FIX: v:searchforward requires Vim 7.2; explicitly check for its existence
  and else just assume forward search.
- Add dependency to ingo-library ([vimscript #4433](http://www.vim.org/scripts/script.php?script_id=4433)).

__You need to separately install ingo-library ([vimscript #4433](http://www.vim.org/scripts/script.php?script_id=4433)) version
  1.012 (or higher)!__

##### 1.01    24-Aug-2012
- BUG: Forgot to append l:patternFlags and enclose in delimiters when there's a
non-whitespace pattern; this makes the GrepHere plugin's mappings wrongly jump
to the first match.

##### 1.00    16-Aug-2012
- First published version.

##### 0.01    19-Mar-2012
- Started development.

------------------------------------------------------------------------------
Copyright: (C) 2012-2019 Ingo Karkat -
The [VIM LICENSE](http://vimdoc.sourceforge.net/htmldoc/uganda.html#license) applies to this plugin.

Maintainer:     Ingo Karkat &lt;ingo@karkat.de&gt;
