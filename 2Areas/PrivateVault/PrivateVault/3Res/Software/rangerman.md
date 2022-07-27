tags: #filemanager #linux #softare


RANGER(1)									    ranger manual									   RANGER(1)

ranger - visual file manager

SYNOPSIS
       ranger [--version] [--help] [--debug] [--clean] [--cachedir=directory] [--confdir=directory] [--datadir=directory] [--copy-config=which] [--choosefile=target]
       [--choosefiles=target] [--choosedir=target] [--selectfile=filepath] [--show-only-dirs] [--list-unused-keys] [--list-tagged-files=tag] [--profile] [--cmd=command] [path ...]

DESCRIPTION
       ranger is a console file manager with VI key bindings.

RESOURCES
       This manual contains instructions on how to use and configure ranger.

       Inside ranger, you can press ? for a list of key bindings, commands or settings.

       The file README.md contains install instructions.

       The file HACKING.md contains guidelines for code modification.

       The directory doc/configs contains configuration files.	They are usually installed to /etc/ranger/config and can be obtained with ranger's --copy-config option.

       The directory examples contains reference implementations for ranger plugins, sample configuration files and some programs for integrating ranger with other software.  They
       are usually installed to /usr/share/doc/ranger/examples.

       The man page of rifle(1) describes the functions of the file opener

       The section LINKS of this man page contains further resources.

POSITIONAL ARGUMENTS
       path ...      Each path will be opened in a tab and if the path is a file it will be selected.  Omitting this is equivalent to providing the current directory.

OPTIONS
       -d, --debug   Activate the debug mode: Whenever an error occurs, ranger will exit and print a full traceback.  The default behavior is to merely print the name of the
		     exception in the statusbar/log and try to keep running.

       -c, --clean   Activate the clean mode:  ranger will not access or create any configuration files nor will it leave any traces on your system.  This is useful when your
		     configuration is broken, when you want to avoid clutter, etc.

       --cachedir=dir
		     Change the cache directory of ranger from $XDG_CACHE_HOME or ~/.cache/ranger to "dir".

       -r dir, --confdir=dir
		     Change the configuration directory of ranger from $XDG_CONFIG_HOME or ~/.config/ranger to "dir".

       --datadir=dir Change the data directory of ranger from $XDG_DATA_HOME or ~/.local/share/ranger to "dir".

       --copy-config=file
		     Create copies of the default configuration files in your local configuration directory.  Existing ones will not be overwritten.  Possible values: all,
		     commands, commands_full, rc, rifle, scope.

		     Note: You may want to disable loading of the global configuration files by exporting RANGER_LOAD_DEFAULT_RC=FALSE in your environment.  See also: FILES,
		     ENVIRONMENT

		     --copy-config=commands will copy only a small sample configuration file with a thoroughly commented example.  It is recommended to keep this file tidy to avoid
		     getting defunct commands on ranger upgrades.  The full default commands.py can be copied with --copy-config=commands_full, but that file will be ignored by
		     ranger and serves only as a reference for making your own commands.

       --choosefile=targetfile
		     Allows you to pick a file with ranger.  This changes the behavior so that when you open a file, ranger will exit and write the absolute path of that file into
		     targetfile.

       --choosefiles=targetfile
		     Allows you to pick multiple files with ranger.  This changes the behavior so that when you open a file, ranger will exit and write the absolute paths of all
		     selected files into targetfile, adding one newline after each filename.

       --choosedir=targetfile
		     Allows you to pick a directory with ranger.  When you exit ranger, it will write the last visited directory into targetfile.

       --selectfile=targetfile
		     Open ranger with targetfile selected. This is a legacy option, superseded by the behavior for the POSITIONAL ARGUMENTS.

       --show-only-dirs
		     Display only the directories. May be used in conjunction with --choosedir=targetfile.

       --list-unused-keys
		     List common keys which are not bound to any action in the "browser" context.  This list is not complete, you can bind any key that is supported by curses: use
		     the key code returned by "getch()".

       --list-tagged-files=tag
		     List all files which are tagged with the given tag.  Note: Tags are single characters.  The default tag is "*"

       --profile     Print statistics of CPU usage on exit.

       --cmd=command Execute the command after the configuration has been read.  Use this option multiple times to run multiple commands.

       --version     Print the version and exit.

       -h, --help    Print a list of options and exit.

CONCEPTS
       This part explains how certain parts of ranger work and how they can be used efficiently.

   TAGS
       Tags are single characters which are displayed left of a filename.  You can use tags however you want.  Press "t" to toggle tags and "ut" to remove any tags of the
       selection. The default tag is an Asterisk ("*"), but you can use any tag by typing "<tagname>.

   PREVIEWS
       By default, only text files are previewed, but you can enable external preview scripts by setting the option "use_preview_script" and "preview_files" to true.

       This default script is %rangerdir/data/scope.sh. It contains more documentation and calls to many external programs to generate previews. They are automatically used when
       available but completely optional.

       For general usage:
	 - "file" for determining file types

	 - "chardet" (Python package) for improved encoding detection of text files

	 - "sudo" to use the "run as root" feature

	 - "python-bidi" (Python package) to display right-to-left file names correctly (Hebrew, Arabic)

       For enhanced file previews (with scope.sh):
	 - "img2txt" (from "caca-utils") for ASCII-art image previews

	 - "w3mimgdisplay", "ueberzug", "mpv", "iTerm2", "kitty", "terminology" or "urxvt" for image previews

	 - "convert" (from "imagemagick") to auto-rotate images and for SVG previews

	 - "ffmpegthumbnailer" for video thumbnails

	 - "highlight", "bat" or "pygmentize" for syntax highlighting of code

	 - "atool", "bsdtar", "unrar" and/or "7z" to preview archives

	 - "bsdtar", "tar", "unrar", "unzip" and/or "zipinfo" (and "sed") to preview archives as their first image

	 - "lynx", "w3m" or "elinks" to preview html pages

	 - "pdftotext" or "mutool" (and "fmt") for textual pdf previews, "pdftoppm" to preview as image

	 - "djvutxt" for textual DjVu previews, "ddjvu" to preview as image

	 - "calibre" or "epub-thumbnailer" for image previews of ebooks

	 - "transmission-show" for viewing BitTorrent information

	 - "mediainfo" or "exiftool" for viewing information about media files

	 - "odt2txt" for OpenDocument text files (odt, ods, odp and sxw)

	 - "python" or "jq" for JSON files

	 - "fontimage" for font previews

       Install these programs (just the ones you need) and scope.sh will automatically use them.

       Independently of the preview script, there is a feature to preview images by drawing them directly into the terminal. To enable this feature, set the option "preview_images"
       to true and enable one of the image preview modes:

       iTerm2

       This only works in iTerm2 compiled with image preview support, but works over ssh.

       To enable this feature, set the option "preview_images_method" to iterm2.

       This feature relies on the dimensions of the terminal's font.  By default, a width of 8 and height of 11 are used.  To use other values, set the options "iterm2_font_width"
       and "iterm2_font_height" to the desired values.

       kitty

       This only works in Kitty. It requires PIL (or pillow) to work.  Allows remote image previews, for example in an ssh session.

       To enable this feature, set the option "preview_images_method" to kitty.

       terminology

       This only works in terminology. It can render vector graphics, but works only locally.

       To enable this feature, set the option "preview_images_method" to terminology.

       ueberzug

       Ueberzug is a command line utility which draws images on terminals using child windows. It requires PIL (or pillow) and relies on X11. This makes it compatible (in a limited
       way, i.e., tmux splits are not supported) with many terminals and tmux but not the Linux console or Wayland.

       To enable this feature, set the option "preview_images_method" to ueberzug.

       urxvt

       This only works in urxvt compiled with pixbuf support. Does not work over ssh.

       Essentially this mode sets an image as a terminal background temporarily, so it will break any previously set image background.

       To enable this feature, set the option "preview_images_method" to urxvt.

       urxvt-full

       The same as urxvt but utilizing not only the preview pane but the whole terminal window.

       To enable this feature, set the option "preview_images_method" to urxvt-full.

       w3m

       This does not work over ssh, requires certain terminals (tested on "xterm" and "urxvt") and is incompatible with tmux, although it works with screen.

       To enable this feature, install the program "w3m" and set the option "preview_images_method" to w3m.

       When using a terminal with a nonzero border which is not automatically detected, the w3m preview will be misaligned.  Use the "w3m_offset" option to manually adjust the
       image offset. This should be the same value as the terminal's border value.

   SELECTION
       The selection is defined as "All marked files IF THERE ARE ANY, otherwise the current file."  Be aware of this when using the :delete command, which deletes all files in the
       selection.

       You can mark files by pressing <Space>, v, etc.	A yellow Mrk symbol at the bottom right indicates that there are marked files in this directory.

   MACROS
       Macros can be used in commands to abbreviate things.

	%f   the highlighted file
	%d   the path of the current directory
	%s   the selected files in the current directory
	%t   all tagged files in the current directory
	%c   the full paths of the currently copied/cut files
	%p   the full paths of selected files

       The macros %f, %d, %p, and %s also have upper case variants, %F, %D, %P, and %S, which refer to the next tab.  To refer to specific tabs, add a number in between.  (%7s =
       selection of the seventh tab.)

       %c is the only macro which ranges out of the current directory. So you may "abuse" the copying function for other purposes, like diffing two files which are in different
       directories:

	Yank the file A (type yy), move to the file B, then type
	@diff %c %f

       Macros for file paths are generally shell-escaped so they can be used in the "shell" command.

       When mapping keys you can use the placeholder <any>, the key entered in that position can be used through the %any and %any_path macros. (When using multiple <any>
       placeholders you can index the macros: %any0, %any_path0, %any1, %any_path1...) The macro %any will be replaced with the key pressed in the position of the <any>
       placeholder. The macro %any_path will be replaced with the path of the bookmark mapped to the key pressed in the position of the <any> placeholder. For example this macro
       can be used to echo the key that was pressed after "c":

	map c<any> echo %any

       %any is used in the ranger configuration to create a keybinding for adding a bookmark. c<set_bookmark> creates a bookmark for the current directory and the key for the
       bookmark is the first supplied argument. In this case the key pressed after "m":

	map m<any> set_bookmark %any

       The %any_path macro can be used to echo the path of the bookmark that is set to the key pressed after "c":

	map c<any> echo %any_path

       A practical example of the use of %any_path is the pasting of cut/copied files to a bookmarked directory:

	map p'<any> paste dest=%any_path

       The macro %rangerdir expands to the directory of ranger's python library, you can use it for something like this command:
	alias show_commands shell less %rangerdir/config/commands.py

       %confdir expands to the directory given by --confdir.

       %datadir expands to the directory given by --datadir.

       The macro %space expands to a space character. You can use it to add spaces to the end of a command when needed, while preventing editors to strip spaces off the end of the
       line automatically.

       To write a literal %, you need to escape it by writing %%.

       Note that macros are expanded twice when using chain. For example, to insert a space character in a chained command, you would write %%space:
	chain command1; command2%%space

   BOOKMARKS
       Type m<key> to bookmark the current directory. You can re-enter this directory by typing `<key>. <key> can be any letter or digit.  Unlike vim, both lowercase and uppercase
       bookmarks are persistent.

       Each time you jump to a bookmark, the special bookmark at key ` will be set to the last directory. So typing "``" gets you back to where you were before.

       Bookmarks are selectable when tabbing in the :cd command.

       Note: The bookmarks ' (Apostrophe) and ` (Backtick) are the same.

   RIFLE
       Rifle is the file opener of ranger.  It can be used as a standalone program or a python module.	It is located at $repo/ranger/ext/rifle.py.  In contrast to other, more
       simple file openers, rifle can automatically find installed programs so it can be used effectively out of the box on a variety of systems.

       It's configured in rifle.conf through a list of conditions and commands.  For each line the conditions are checked and if they are met, the respective command is taken into
       consideration.  By default, simply the first matching rule is used.  In ranger, you can list and choose rules by typing "r" or simply by typing "<rulenumber><enter>".  If
       you use rifle standalone, you can list all rules with the "-l" option and pick a rule with "-p <number>".

       The rules, along with further documentation, are contained in $repo/ranger/config/rifle.conf.

   FLAGS
       Flags give you a way to modify the behavior of the spawned process.  They are used in the commands ":open_with" (key "r") and ":shell" (key "!").

	f   Fork the process, i.e. run in background. Please use this flag
	    instead of calling "disown" or "nohup", to avoid killing the
	    background command when pressing Ctrl+C in ranger.
	c   Run the current file only, instead of the selection
	r   Run application with root privilege (requires sudo)
	t   Run application in a new terminal window

       There are some additional flags that can currently be used only in the "shell" command: (for example ":shell -w df")

	p   Redirect output to the pager
	s   Silent mode.  Output will be discarded.
	w   Wait for an Enter-press when the process is done

       By default, all the flags are off unless otherwise specified in rc.conf key bindings or rifle.conf rules. You can specify as many flags as you want. An uppercase flag
       negates the effect: "ffcccFsf" is equivalent to "cs".

       The terminal program name for the "t" flag is taken from the environment variable $TERMCMD.  If it doesn't exist, it tries to extract it from $TERM, uses "x-terminal-
       emulator" as a fallback, and then "xterm" if that fails.

       Examples: ":open_with c" will open the file that you currently point at, even if you have selected other files.	":shell -w df" will run "df" and wait for you to press Enter
       before switching back to ranger.

   PLUGINS
       ranger's plugin system consists of python files which are located in ~/.config/ranger/plugins/ and are imported in alphabetical order when starting ranger.  A plugin changes
       rangers behavior by overwriting or extending a function that ranger uses.  This allows you to change pretty much every part of ranger, but there is no guarantee that things
       will continue to work in future versions as the source code evolves.

       Adding new commands via a plugin as simple as specifying them like you would do in the commands.py.

       There are some hooks that are specifically made for the use in plugins.	They are functions that start with hook_ and can be found throughout the code.

	grep 'def hook_' -r /path/to/rangers/source

       Also try:

	pydoc ranger.api

       Note that you should NOT simply overwrite a function unless you know what you're doing.	Instead, save the existing function and call it from your new one.  This way,
       multiple plugins can use the same hook.	There are several sample plugins in the /usr/share/doc/ranger/examples/ directory, including a hello-world plugin that describes
       this procedure.

KEY BINDINGS
       Key bindings are defined in the file %rangerdir/config/rc.conf.	Check this file for a list of all key bindings.  You can copy it to your local configuration directory with
       the --copy-config=rc option.

       Many key bindings take an additional numeric argument.  Type 5j to move down 5 lines, 2l to open a file in mode 2, 10<Space> to mark 10 files.

       This list contains the most useful bindings:

   MAIN BINDINGS
       h, j, k, l    Move left, down, up or right

       ^D or J, ^U or K
		     Move a half page down, up

       H, L	     Move back and forward in the history

       gg	     Move to the top

       G	     Move to the bottom

       [, ]	     Move up and down in the parent directory.

       ^R	     Reload everything

       F	     Toggle freeze_files setting.  When active (indicated by a cyan FROZEN message in the status bar), directories and files will not be loaded, improving
		     performance when all the files you need are already loaded.  This does not affect file previews, which can be toggled with zI.  Also try disabling the preview
		     of directories with zP.

       ^L	     Redraw the screen

       i	     Inspect the current file in a bigger window.

       E	     Edit the current file in $VISUAL otherwise $EDITOR otherwise "vim"

       S	     Open a shell in the current directory

       ?	     Opens this man page

       W	     Opens the log window where you can review messages that pop up at the bottom.

       w	     Opens the task window where you can view and modify background processes that currently run in ranger.  In there, you can type "dd" to abort a process and "J"
		     or "K" to change the priority of a process.  Only one process is run at a time.

       ^C	     Stop the currently running background process that ranger has started, like copying files, loading directories or file previews.

       <octal>=, +<who><what>, -<who><what>
		     Change the permissions of the selection.  For example, "777=" is equivalent to "chmod 777 %s", "+ar" does "chmod a+r %s", "-ow" does "chmod o-w %s" etc.

       yy	     Copy (yank) the selection, like pressing Ctrl+C in modern GUI programs.  (You can also type "ya" to add files to the copy buffer, "yr" to remove files again,
		     or "yt" for toggling.)

       dd	     Cut the selection, like pressing Ctrl+X in modern GUI programs.  (There are also "da", "dr" and "dt" shortcuts equivalent to "ya", "yr" and "yt".)

       pp	     Paste the files which were previously copied or cut, like pressing Ctrl+V in modern GUI programs.

		     Conflicts will be renamed by appending an '_' (and a counter if necessary), resulting in "file.ext_", "file.ext_0", etc. If you prefer "file_.ext" you can use
		     the "paste_ext" command.

       po	     Paste the copied/cut files, overwriting existing files.

       pP, pO	     Like pp and po, but queues the operation so that it will be executed after any other operations.  Reminder: type "w" to open the task window.

       pl, pL	     Create symlinks (absolute or relative) to the copied files

       phl	     Create hardlinks to the copied files

       pht	     Duplicate the subdirectory tree of the copied directory, then create hardlinks for each contained file into the new directory tree.

       mX	     Create a bookmark with the name X

       `X	     Move to the bookmark with the name X

       n	     Find the next file.  By default, this gets you to the newest file in the directory, but if you search something using the keys /, cm, ct, ..., it will get you
		     to the next found entry.

       N	     Find the previous file.

       oX	     Change the sort method (like in mutt)

       zX	     Change settings.  See the settings section for a list of settings and their hotkey.

       u?	     Universal undo-key.  Depending on the key that you press after "u", it either restores closed tabs (uq), removes tags (ut), clears the copy/cut buffer (ud),
		     starts the reversed visual mode (uV) or clears the selection (uv).

       f	     Quickly navigate by entering a part of the filename.

       Space	     Mark a file.

       v	     Toggle the mark-status of all files

       V	     Starts the visual mode, which selects all files between the starting point and the cursor until you press ESC.  To unselect files in the same way, use "uV".

       /	     Search for files in the current directory.

       :	     Open the console.

       !	     Open the console with the content "shell " so you can quickly run commands

       @	     Open the console with the content "shell  %s", placing the cursor before the " %s" so you can quickly run commands with the current selection as the argument.

       r	     Open the console with the content "open with " so you can decide which program to use to open the current file selection.

       cd	     Open the console with the content "cd "

       ^P	     Open the console with the most recent command.

       Alt-N	     Open a tab. N has to be a number from 0 to 9. If the tab doesn't exist yet, it will be created.

       Alt-l, Alt-r  Shift a tab left, respectively right.

       gn, ^N	     Create a new tab.

       gt, gT	     Go to the next or previous tab. You can also use TAB and SHIFT+TAB instead.

       gc, ^W	     Close the current tab.  The last tab cannot be closed this way.

       M	     A key chain that allows you to quickly change the line mode of all the files of the current directory.  For a more permanent solution, use the command
		     "default_linemode" in your rc.conf.

       .d	     Apply the typefilter "directory".

       .f	     Apply the typefilter "file".

       .l	     Apply the typefilter "symlink".

       .m	     Apply a new mimetype filter.

       .n	     Apply a new filename filter.

       .#	     Apply a new hash filter.

       ."	     Apply a new duplicate filter.

       .'	     Apply a new unique filter.

       .|	     Combine the two topmost filters from the filter stack in the "OR" relationship, instead of the "AND" used implicitly.

       .&	     Explicitly combine the two topmost filters in the "AND" relationship.  Usually not needed because filters are implicitly in this relationship though might be
		     useful in more complicated scenarios.

       .!	     Negate the topmost filter.

       .r	     Rotate the filter stack by N elements. Where N is provided as a numeric prefix like vim's count and defaults to 1, i.e. move the topmost element to the bottom
		     of the stack.

       .c	     Clear the filter stack.

       .*	     Decompose the topmost filter combinator (e.g. ".!", ".|").

       .p	     Pop the topmost filter from the filter stack.

       ..	     Show the current filter stack state.

   READLINE-LIKE BINDINGS IN THE CONSOLE
       ^B, ^F	     Move left and right (B for back, F for forward)

       ^P, ^N	     Move up and down (P for previous, N for Next)

       ^A, ^E	     Move to the start or to the end

       Alt-B, Alt-LEFT
		     Move backwards by words.

       Alt-F, Alt-RIGHT
		     Move forwards by words.

       ^D	     Delete the current character.

       ^H	     Backspace.

MOUSE BUTTONS
       Left Mouse Button
	   Click on something and you'll move there.  To run a file, "enter" it, like a directory, by clicking on the preview.

       Right Mouse Button
	   Enter a directory or run a file.

       Scroll Wheel
	   Scrolls up or down.	You can point at the column of the parent directory while scrolling to switch directories.

SETTINGS
       This section lists all built-in settings of ranger.  The valid types for the value are in [brackets].  The hotkey to toggle the setting is in <brakets>, if a hotkey exists.

       Settings can be changed in the file ~/.config/ranger/rc.conf or on the fly with the command :set option value.  Examples:

	set column_ratios 1,2,3
	set show_hidden true

       Toggling options can be done with:

	set show_hidden!

       The different types of settings and an example for each type:

	setting type   | example values
	---------------+----------------------------
	bool	       | true, false
	integer        | 1, 23, 1337
	string	       | foo, hello world
	list	       | 1,2,3,4
	none	       | none

       You can view a list of all settings and their current values by pressing "3?"  in ranger.

       automatically_count_files [bool]
	   Should ranger count and display the number of files in each directory as soon as it's visible?  This gets slow with remote file systems.  Turning it off will still allow
	   you to see the number of files after entering the directory.

       autosave_bookmarks [bool]
	   Save bookmarks (used with mX and `X) instantly?  This helps to synchronize bookmarks between multiple ranger instances but leads to *slight* performance loss.  When
	   false, bookmarks are saved when ranger is exited.

       autoupdate_cumulative_size [bool]
	   You can display the "real" cumulative size of directories by using the command :get_cumulative_size or typing "dc".	The size is expensive to calculate and will not be
	   updated automatically.  You can choose to update it automatically though by turning on this option.

       cd_bookmarks [bool]
	   Specify whether bookmarks should be included in the tab completion of the "cd" command.

       cd_tab_case [string]
	   Changes case sensitivity for the "cd" command tab completion. Possible values are:

	    sensitive
	    insensitive
	    smart

       cd_tab_fuzzy [bool]
	   Use fuzzy tab completion with the "cd" command. For example, :cd /u/lo/b<TAB> expands to :cd /usr/local/bin.

       clear_filters_on_dir_change [bool]
	   If set to 'true', persistent filters would be cleared upon leaving the directory

       collapse_preview [bool] <zc>
	   When no preview is visible, should the last column be squeezed to make use of the whitespace?

       colorscheme [string]
	   Which colorscheme to use?  These colorschemes are available by default: default, jungle, snow.  Snow is a monochrome scheme, jungle replaces blue directories with green
	   ones for better visibility on certain terminals.

       column_ratios [list]
	   How many columns are there, and what are their relative widths?  For example, a value of 1,1,1 would mean 3 evenly sized columns. 1,1,1,1,4 means 5 columns with the
	   preview column being as large as the other columns combined.

       confirm_on_delete [string]
	   Ask for a confirmation when running the "delete" command?  Valid values are "always" (default), "never", "multiple". With "multiple", ranger will ask only if you delete
	   multiple files at once.

       dirname_in_tabs [bool]
	   Display the directory name in tabs?

       display_size_in_main_column [bool]
	   Display the file size in the main column?

       display_size_in_status_bar [bool]
	   Display the file size in the status bar?

       display_free_space_in_status_bar [bool]
	   Display the free disk space in the status bar?

       display_tags_in_all_columns [bool]
	   Display tags in all columns?

       draw_borders [string]
	   Draw borders around or between the columns? Possible values are:

	    none	   no borders of any sort
	    outline	   draw an outline around all the columns
	    separators	   draw only vertical lines between columns
	    both	   both of the above

       draw_progress_bar_in_status_bar [bool]
	   Draw a progress bar in the status bar which displays the average state of all currently running tasks which support progress bars?

       flushinput [bool] <zi>
	   Flush the input after each key hit?	One advantage is that when scrolling down with "j", ranger stops scrolling instantly when you release the key.	One disadvantage is
	   that when you type commands blindly, some keys might get lost.

       freeze_files [bool] <F>
	   When active, directories and files will not be loaded, improving performance when all the files you need are already loaded.  This does not affect file previews.

       global_inode_type_filter [string]
	   Like filter_inode_type, but globally for all directories.  Useful in combination with --choosedir:

	    ranger --choosedir=/tmp/x --cmd='set global_inode_type_filter d'

       hidden_filter [string]
	   A regular expression pattern for files which should be hidden.  For example, this pattern will hide all files that start with a dot or end with a tilde.

	    set hidden_filter ^\.|~$

       hint_collapse_threshold [int]
	   The key hint lists up to this size have their sublists expanded.  Otherwise the submaps are replaced with "...".

       hostname_in_titlebar [bool]
	   Show hostname in titlebar?

       size_in_bytes [bool]
	   Print file sizes in bytes instead of the default human-readable format.

       idle_delay [integer]
	   The delay that ranger idly waits for user input, in milliseconds, with a resolution of 100ms.  Lower delay reduces lag between directory updates but increases CPU load.

       iterm2_font_height [integer]
	   Change the assumed font height in iTerm2, which may help with iTerm image previews

       iterm2_font_width [integer]
	   Change the assumed font width in iTerm2, which may help with iTerm image previews

       line_numbers [string]
	   Show line numbers in main column.  Possible values are:

	    false      turn the feature off
	    absolute   absolute line numbers for use with "<N>gg"
	    relative   relative line numbers for "<N>k" or "<N>j"

       max_console_history_size [integer, none]
	   How many console commands should be kept in history?  "none" will disable the limit.

       max_history_size [integer, none]
	   How many directory changes should be kept in history?

       metadata_deep_search [bool]
	   When the metadata manager module looks for metadata, should it only look for a ".metadata.json" file in the current directory, or do a deep search and check all
	   directories above the current one as well?

       mouse_enabled [bool] <zm>
	   Enable mouse input?

       nested_ranger_warning [string]
	   Warn at startup if "RANGER_LEVEL" is greater than 0, in other words give a warning when you nest ranger in a subshell started by ranger. Allowed values are "true",
	   "false" and "error". The special value "error" promotes the warning to an error, this is usually shown as red text but will crash ranger when run with the "--debug"
	   flag.

       one_indexed [bool]
	   Start line numbers from 1.  Possible values are:

	    false      start line numbers from 0
	    true       start line numbers from 1

       open_all_images [bool]
	   Open all images in this directory when running certain image viewers like feh or sxiv?  You can still open selected files by marking them.

	   If there would be too many files for the system to handle, this option will be temporarily disabled automatically.

       padding_right [bool]
	   When collapse_preview is on and there is no preview, should there remain a little padding on the right?  This allows you to click into that space to run the file.

       preview_directories [bool] <zP>
	   Preview directories in the preview column?

       preview_files [bool] <zp>
	   Preview files in the preview column?

       preview_images [bool]
	   Draw images inside the console with the external program w3mimgpreview?

       preview_images_method [string]
	   Set the preview image method. Supported methods: w3m, iterm2, urxvt, urxvt-full, terminology.  See PREVIEWS section.

       preview_max_size [int]
	   Avoid previewing files that exceed a certain size, in bytes.  Use a value of 0 to disable this feature.

       preview_script [string, none]
	   Which script should handle generating previews?  If the file doesn't exist, or use_preview_script is off, ranger will handle previews itself by just printing the
	   content.

       relative_current_zero [bool]
	   When line_numbers is set to relative, show 0 on the current line if true or show the absolute number of the current line when false.

       save_backtick_bookmark [bool]
	   Save the "`" bookmark to disk.  This bookmark is used to switch to the last directory by typing "``".

       save_console_history [bool]
	   Should the console history be saved on exit?  If disabled, the console history is reset when you restart ranger.

       save_tabs_on_exit [bool]
	   Save all tabs, except the active, on exit? The last saved tabs are restored once when starting the next session. Multiple sessions are stored in a stack and the oldest
	   saved tabs are restored first.

       scroll_offset [integer]
	   Try to keep this much space between the top/bottom border when scrolling.

       shorten_title [integer]
	   Trim the title of the window if it gets long?  The number defines how many directories are displayed at once. A value of 0 turns off this feature.

       show_cursor [bool]
	   Always show the terminal cursor?

       show_hidden_bookmarks [bool]
	   Show dotfiles in the bookmark preview window? (Type ')

       show_hidden [bool] <zh>, <^H>
	   Show hidden files?

       show_selection_in_titlebar [bool]
	   Add the highlighted file to the path in the titlebar

       sort_case_insensitive [bool] <zc>
	   Sort case-insensitively?  If true, "a" will be listed before "B" even though its ASCII value is higher.

       sort_directories_first [bool] <zd>
	   Sort directories first?

       sort_reverse [bool] <or>
	   Reverse the order of files?

       sort_unicode [bool]
	   When sorting according to some string, should the unicode characters be compared, instead of looking at the raw character values to save time?

       sort [string] <oa>, <ob>, <oc>, <oe>, <om>, <on>, <ot>, <os>, <oz>
	   Which sorting mechanism should be used?  Choose one of atime, basename, ctime, extension, mtime, natural, type, size, random

	   Note: You can reverse the order by typing an uppercase second letter in the key combination, e.g. "oN" to sort from Z to A.

       status_bar_on_top [bool]
	   Put the status bar at the top of the window?

       tilde_in_titlebar [bool]
	   Abbreviate $HOME with ~ in the titlebar (first line) of ranger?

       unicode_ellipsis [bool]
	   Use a unicode "..." character instead of "~" to mark cut-off filenames?

       bidi_support [bool]
	   Try to properly display file names in RTL languages (Hebrew, Arabic) by using a BIDI algorithm to reverse the relevant parts of the text.  Requires the python-bidi pip
	   package.

       update_title [bool]
	   Set a window title? Updates both the WM_NAME and WM_ICON_NAME properties.

       update_tmux_title [bool]
	   Set the tmux/screen window-name to "ranger"?

       use_preview_script [bool] <zv>
	   Use the preview script defined in the setting preview_script?

       vcs_aware [bool]
	   Gather and display data about version control systems. Supported vcs: git, hg.

       vcs_backend_git, vcs_backend_hg, vcs_backend_bzr, vcs_backend_svn [string]
	   Sets the state for the version control backend. The possible values are:

	    disabled   Don't display any information.
	    local      Display only local state.
	    enabled    Display both, local and remote state.
		       May be slow for hg and bzr.

       vcs_msg_length [int]
	   Length to truncate first line of the commit messages to when shown in the statusbar.  Defaults to 50.

       viewmode [string]
	   Sets the view mode, which can be miller to display the files in the traditional miller column view that shows multiple levels of the hierarchy, or multipane to use
	   multiple panes (one per tab) similar to midnight-commander.

       w3m_delay [float]
	   Delay in seconds before displaying an image with the w3m method.  Increase it in case of experiencing display corruption.

       w3m_offset [int]
	   Offset in pixels for the inner border of the terminal. Some terminals require the offset to be specified explicitly, among others st and UXterm, some don't like urxvt.

       wrap_plaintext_previews [bool]
	   Whether or not to wrap long lines in the pager, this includes previews of plain text files.

       wrap_scroll [bool]
	   Enable scroll wrapping - moving down while on the last item will wrap around to the top and vice versa.

       xterm_alt_key [bool]
	   Enable this if key combinations with the Alt Key don't work for you.  (Especially on xterm)

COMMANDS
       You can enter the commands in the console which is opened by pressing ":".

       You can always get a list of the currently existing commands by typing "?c" in ranger.  For your convenience, this is a list of the "public" commands including their
       parameters, excluding descriptions:

	alias [newcommand] [oldcommand]
	bulkrename
	cd [path]
	chain command1[; command2[; command3...]]
	chmod octal_number
	cmap key command
	console [-pSTARTPOSITION] command
	copycmap key newkey [newkey2...]
	copymap key newkey [newkey2...]
	copypmap key newkey [newkey2...]
	copytmap key newkey [newkey2...]
	cunmap keys...
	default_linemode [path=regexp | tag=tags] linemodename
	delete
	echo [text]
	edit [filename]
	eval [-q] python_code
	filter [string]
	filter_inode_type [dfl]
	find pattern
	flat level
	grep pattern
	help
	jump_non [-FLAGS...]
	linemode linemodename
	load_copy_buffer
	map key command
	mark pattern
	mark_tag [tags]
	meta key value
	mkdir dirname
	open_with [application] [flags] [mode]
	pmap key command
	prompt_metadata [key1 [key2 [...]]]
	punmap keys...
	quit
	quit!
	quitall
	quitall!
	relink newpath
	rename_append [-FLAGS...]
	rename newname
	save_copy_buffer
	scout [-FLAGS...] pattern
	search pattern
	search_inc pattern
	set option value
	setintag tags option value
	setlocal [path=<path>] option value
	shell [-FLAGS...] command
	source filename
	terminal
	tmap key command
	touch filename
	trash
	travel pattern
	tunmap keys...
	unmap keys...
	unmark pattern
	unmark_tag [tags]

       There are additional commands which are directly translated to python functions, one for every method in the ranger.core.actions.Actions class.	They are not documented
       here, since they are mostly for key bindings, not to be typed in by a user.  Read the source if you are interested in them.

       These are the public commands including their descriptions:

       alias [newcommand] [oldcommand]
	 Copies the oldcommand as newcommand.

       bulkrename
	 This command opens a list of selected files in an external editor.  After you edit and save the file, it will generate a shell script which does bulk renaming according to
	 the changes you did in the file.

	 This shell script is opened in an editor for you to review.  After you close it, it will be executed.

       cd [path]
	 The cd command changes the directory.	If path is a file, selects that file.  The command ":cd -" is equivalent to typing ``.

       chain command1[; command2[; command3...]]
	 Combines multiple commands into one, separated by semicolons.

       chmod octal_number
	 Sets the permissions of the selection to the octal number.

	 The octal number is between 000 and 777. The digits specify the permissions for the user, the group and others.  A 1 permits execution, a 2 permits writing, a 4 permits
	 reading.  Add those numbers to combine them. So a 7 permits everything.

	 Key bindings in the form of [-+]<who><what> and <octal>= also exist.  For example, +ar allows reading for everyone, -ow forbids others to write and 777= allows everything.

	 See also: man 1 chmod

       console [-pN] command
	 Opens the console with the command already typed in.  The cursor is placed at N.

       copymap	key newkey [newkey2 ...]
       copycmap key newkey [newkey2 ...]
       copypmap key newkey [newkey2 ...]
       copytmap key newkey [newkey2 ...]
	 Copies the keybinding key to newkey in the "browser" context.	This is a deep copy, so if you change the new binding (or parts of it) later, the old one is not modified.
	 For example, copymap j down will make the key sequence "down" move the cursor down one item.

	 To copy key bindings of the console, pager or taskview use "copycmap", "copypmap" or "copytmap" respectively.

       default_linemode [path=regexp | tag=tags] linemodename
	 Sets the default linemode.  See linemode command.

	 Examples:

	 Set the global default linemode to "permissions":
	  :default_linemode permissions

	 Set the default linemode to "permissions" for all files tagged with "p" or "P":
	  :default_linemode tag=pP permissions

	 Set the default linemode for all files in ~/books/ to "metatitle":
	  :default_linemode path=/home/.*?/books/.* metatitle

       delete
	 Destroy all files in the selection with a roundhouse kick.  ranger will ask for a confirmation if you attempt to delete multiple (marked) files or non-empty directories.
	 This can be changed by modifying the setting "confirm_on_delete".

       echo text
	 Display the text in the statusbar.

       edit [filename]
	 Edit the current file or the file in the argument.

       eval [-q] python_code
	 Evaluates the python code.  `fm' is a reference to the FM instance.  To display text, use the function `p'.  The result is displayed on the screen unless you use the "-q"
	 option.

	 Examples:
	  :eval fm
	  :eval len(fm.tabs)
	  :eval p("Hello World!")

       filter [string]
	 Displays only the files which contain the string in their basename.  Running this command without any parameter will reset the filter.

	 This command is based on the scout command and supports all of its options.

       filter_inode_type [dfl]
	 Displays only the files of specified inode type. To display only directories, use the 'd' parameter. To display only files, use the 'f' parameter. To display only links,
	 use the 'l' parameter. Parameters can be combined. To remove this filter, use no parameter.

       filter_stack [command [args]]
	 Manage the filter stack, adding, removing and manipulating filters. For example, to show only duplicate files and symlinks:

	   :filter_stack add type f
	   :filter_stack add duplicate
	   :filter_stack add and
	   :filter_stack add type l
	   :filter_stack add or

	 Or using the mapped keys:

	   .f ." .& .l .|

	 Available subcommands:

	 add FILTER_TYPE [ARGS...]
	   Add a new filter to the top of the filter stack. Each filter on the stack is applied in turn, resulting in an implicit logical "AND" relation. The following
	   "FILTER_TYPE"s are available:

	   duplicate
	     Filter files so only files that have duplicates in the same directory are shown. Useful when cleaning up identical songs and memes that were saved using distinct file
	     names.

	   filename NAME
	     Filter files that contain NAME in the filename, regular expression syntax is allowed.

	   hash PATH
	     Filter files so only files with the same hash as PATH are shown.

	   mimetype TYPE
	     Filter files of a certain MIME type, regular expression syntax is allowed.

	   typefilter [d|f|l]
	     Filter files of a certain type, "d" for directories, "f" for files and "l" for symlinks.

	   unique
	     Filter files so only unique files and the oldest file of every set of duplicates is shown.

	   and
	     Explicitly combine the two topmost filters in the "AND" relationship.  Usually not needed because filters are implicitly in this relationship though might be useful in
	     more complicated scenarios.

	   not
	     Negate the topmost filter.

	   or
	     Combine the two topmost filters from the filter stack in the "OR" relationship, instead of the "AND" used implicitly.

	 pop
	   Pop the topmost filter from the filter stack.

	 decompose
	   Decompose the topmost filter combinator (e.g. ".!", ".|").

	 rotate [N=1]
	   Rotate the filter stack by N elements. Where N is passed as argument or as a numeric prefix like vim's count, default to 1, i.e. move the topmost element to the bottom
	   of the stack.

	 clear
	   Clear the filter stack.

	 show
	   Show the current filter stack state.

       find pattern
	 Search files in the current directory that contain the given (case-insensitive) string in their name as you type.  Once there is an unambiguous result, it will be run
	 immediately. (Or entered, if it's a directory.)

	 This command is based on the scout command and supports all of its options.

       flat level
	 Flattens the directory view up to the specified level. Level -1 means infinite level. Level 0 means standard view without flattened directory view. Level values -2 and
	 less are invalid.

       grep pattern
	 Looks for a string in all marked files or directories.

       help
	 Provides a quick way to view ranger documentations.

       jump_non [-flags...]
	 Jumps to first non-directory if highlighted file is a directory and vice versa.

	 Flags:
	  -r	Jump in reverse order
	  -w	Wrap around if reaching end of filelist

       linemode linemodename
	 Sets the linemode of all files in the current directory.  The linemode may be:

	  "filename":
	    display each line as "<basename>...<size>"
	  "fileinfo":
	    display each line as "<basename>...<file(1) output>"
	  "mtime":
	    display each line as "<basename>...<mtime>" in ISO format
	  "humanreadablemtime":
	    display each line as "<basename>...<mtime>" in a human readable
	    format, more precise the more recent.
	  "sizemtime":
	    display each line as "<basename>...<size> <mtime>" in ISO format
	  "humanreadablesizemtime":
	    display each line as "<basename>...<size> <mtime>" in a human
	    readable format, more precise the more recent.
	  "permissions":
	    display each line as "<permissions> <owner> <group> <basename>"
	  "metatitle":
	    display metadata from .metadata.json files if available, fall back
	    to the "filename" linemode if no metadata was found.
	    See :meta command.

	 The custom linemodes may be added by subclassing the LinemodeBase class.  See the ranger.core.linemode module for some examples.

       load_copy_buffer
	 Load the copy buffer from ~/.config/ranger/copy_buffer.  This can be used to pass the list of copied files to another ranger instance.

       map  key command
       cmap key command
       pmap key command
       tmap key command
	 Assign the key combination to the given command.  Whenever you type the key/keys, the command will be executed.  Additionally, if you use a quantifier when typing the key,
	 like 5j, it will be passed to the command as the attribute "self.quantifier".

	 The keys you bind with this command are accessible in the file browser only, not in the console, pager or taskview.  To bind keys there, use the commands "cmap", "pmap" or
	 "tmap".

       mark pattern
	 Mark all files matching the regular expression pattern.

	 This command is based on the scout command and supports all of its options.

       mark_tag [tags]
	 Mark all tags that are tagged with either of the given tags.  When leaving out the tag argument, all tagged files are marked.

       meta key value
	 Set the metadata of the currently highlighted file.  Example:

	  :meta title The Hitchhiker's Guide to the Galaxy
	  :meta year 1979

	 This metadata can be displayed by, for example, using the "metatitle" line mode by typing Mt.

       mkdir dirname
	 Creates a directory with the name dirname.

       open_with [application] [flags] [mode]
	 Open the selected files with the given application, unless it is omitted, in which case the default application is used.  flags change the way the application is executed
	 and are described in their own section in this man page.  The mode is a number that specifies which application to use.  The list of applications is generated by the
	 external file opener "rifle" and can be displayed when pressing "r" in ranger.

	 Note that if you specify an application, the mode is ignored.

       prompt_metadata [keys ...]
	 Prompt the user to input metadata with the "meta" command for multiple keys in a row.

       quit
	 Closes the current tab, if there's only one tab. Otherwise quits if there are no tasks in progress.  The current directory will be bookmarked as ' so you can re-enter it
	 by typing `` or '' the next time you start ranger.

       quit!
	 Like "quit", except will force quit even if tasks are in progress.

       quitall
	 Like "quit", except will quit even if multiple tabs are open.

       quitall!
	 Like "quitall", except will force quit even if tasks are in progress.

       relink newpath
	 Change the link destination of the current symlink file to <newpath>. First <tab> will load the original link.

       rename newname
	 Rename the current file.  If a file with that name already exists, the renaming will fail.  Also try the key binding A for appending something to a file name.

       rename_append [-flags...]
	 Opens the console with ":rename <current file>" with the cursor positioned before the file extension.

	 Flags:
	  -a	Position before all extensions
	  -r	Remove everything before extensions

       save_copy_buffer
	 Save the copy buffer to ~/.config/ranger/copy_buffer.	This can be used to pass the list of copied files to another ranger instance.

       scout [-flags...] [--] pattern
	 Swiss army knife command for searching, traveling and filtering files.

	 Flags:
	  -a	Automatically open a file on unambiguous match
	  -e	Open the selected file when pressing enter
	  -f	Filter files that match the current search pattern
	  -g	Interpret pattern as a glob pattern
	  -i	Ignore the letter case of the files
	  -k	Keep the console open when changing a directory with the command
	  -l	Letter skipping; e.g. allow "rdme" to match the file "readme"
	  -m	Mark the matching files after pressing enter
	  -M	Unmark the matching files after pressing enter
	  -p	Permanent filter: hide non-matching files after pressing enter
	  -r	Interpret pattern as a regular expression pattern
	  -s	Smart case; like -i unless pattern contains upper case letters
	  -t	Apply filter and search pattern as you type
	  -v	Inverts the match

	 Multiple flags can be combined.  For example, ":scout -gpt" would create a :filter-like command using globbing.

       search pattern
	 Search files in the current directory that match the given (case insensitive) regular expression pattern.

	 This command is based on the scout command and supports all of its options.

       search_inc pattern
	 Search files in the current directory that match the given (case insensitive) regular expression pattern.  This command gets you to matching files as you type.

	 This command is based on the scout command and supports all of its options.

       set option value
	 Assigns a new value to an option.  Valid options are listed in the settings section.  Use tab completion to get the current value of an option, though this doesn't work
	 for functions and regular expressions. Valid values are:

	  setting type	 | example values
	  ---------------+----------------------------
	  bool		 | true, false
	  integer	 | 1, 23, 1337
	  string	 | foo, hello world
	  list		 | 1,2,3,4
	  none		 | none

       setintag tags option value
	 Assigns a new value to an option, but locally for the directories that are marked with tag.  This means, that this option only takes effect when visiting that directory.

	 For example, to change the sorting order in your downloads directory, tag it with the v tag by typing "v, then use this command:

	  setintag v sort ctime

       setlocal [path=path] option value
	 Assigns a new value to an option, but locally for the directory given by path. This means, that this option only takes effect when visiting that directory. If no path is
	 given, uses the current directory.

	 path is a regular expression.	This means that "path=~/dl" applies to all paths that start with ~/dl, e.g. ~/dl2 and ~/dl/foo. To avoid this, use "path=~/dl$".

	 path can be quoted with either single or double quotes to prevent unwanted splitting. path='~/dl dl$' or path="~/dl dl$"

       shell [-flags] command
	 Run a shell command.  flags are discussed in their own section.

       source filename
	 Reads commands from a file and executes them in the ranger console.

	 This can be used to re-evaluate the rc.conf file after changing it:

	  map X chain shell vim -p %confdir/rc.conf %rangerdir/config/rc.conf; \
			    source %confdir/rc.conf

       scroll_preview value
	 Scroll the file preview by value lines.

       terminal
	 Spawns the x-terminal-emulator starting in the current directory.

       touch filename
	 Creates an empty file with the name filename, unless it already exists.

       trash
	 Move all files in the selection to the trash using rifle. Rifle tries to use a trash manager like trash-cli if available but will fall back to moving files to either
	 $XDG_DATA_HOME/ranger-trash or ~/.ranger/ranger-trash. This is a less permanent version of delete, relying on the user to clear out the trash whenever it's convenient.
	 While having the possibility of restoring trashed files until this happens. ranger will ask for a confirmation if you attempt to trash multiple (marked) files or non-empty
	 directories. This can be changed by modifying the setting "confirm_on_delete".

       travel pattern
	 Filters the current directory for files containing the letters in the string, possibly with other letters in between.	The filter is applied as you type.  When only one
	 directory is left, it is entered and the console is automatically reopened, allowing for fast travel.	To close the console, press ESC or execute a file.

	 This command is based on the scout command and supports all of its options.

       unmap  [keys ...]
       cunmap [keys ...]
       punmap [keys ...]
       tunmap [keys ...]
	 Removes the given key mappings in the "browser" context.  To unmap key bindings in the console, pager, or taskview use "cunmap", "punmap" or "tunmap".

       unmark pattern
	 Unmark all files matching a regular expression pattern.

	 This command is based on the scout command and supports all of its options.

       unmark_tag [tags]
	 Unmark all tags that are tagged with either of the given tags.  When leaving out the tag argument, all tagged files are unmarked.

FILES
       ranger reads several configuration files which are located in $HOME/.config/ranger or $XDG_CONFIG_HOME/ranger if $XDG_CONFIG_HOME is defined.  You can use the --copy-config
       option to obtain the default configuration files.  The files contain further documentation.

       rc.conf, commands.py and colorschemes do not need to be copied fully as they will only be adding to the default configuration files except if explicitly overridden. This may
       lead to some confusing situations, for example when a key is being bound despite the corresponding line being removed from the user's copy of the configuration file. This
       behavior may be disabled with an environment variable (see also: ENVIRONMENT). Note: All other configuration files only read from one source; i.e. default OR user, not both.
       rc.conf and commands.py are additionally read from /etc/ranger if they exist for system-wide configuration, user configuration overrides system configuration which overrides
       the default configuration.

       When starting ranger with the --clean option, it will not access or create any of these files.

   CONFIGURATION
       rc.conf	 Contains a list of commands which are executed on startup.  Mostly key bindings and settings are defined here.

       commands.py
		 A python module that defines commands which can be used in ranger's console by typing ":" or in the rc.conf file.  Note that you can define commands in the same
		 manner within plugins.

       commands_full.py
		 This file is copied by --copy-config=commands_full and serves as a reference for custom commands.  It is entirely ignored by ranger.

       rifle.conf
		 This is the configuration file for the built-in file launcher called "rifle".

       scope.sh  This is a script that handles file previews.  When the options use_preview_script and preview_files are set, the program specified in the option preview_script is
		 run and its output and/or exit code determines rangers reaction.

       colorschemes/
		 Colorschemes can be placed here.

       plugins/  Plugins can be placed here.

   STORAGE
       bookmarks This file contains a list of bookmarks.  The syntax is /^(.):(.*)$/. The first character is the bookmark key and the rest after the colon is the path to the file.
		 In ranger, bookmarks can be set by typing m<key>, accessed by typing '<key> and deleted by typing um<key>.

       copy_buffer
		 When running the command :save_copy_buffer, the paths of all currently copied files are saved in this file.  You can later run :load_copy_buffer to copy the same
		 files again, pass them to another ranger instance or process them in a script.

       history	 Contains a list of commands that have been previously typed in.

       tagged	 Contains a list of tagged files. The syntax is /^(.:)?(.*)$/ where the first letter is the optional name of the tag and the rest after the optional colon is the
		 path to the file.  In ranger, tags can be set by pressing t and removed with T.  To assign a named tag, type "<tagname>.

ENVIRONMENT
       These environment variables have an effect on ranger:

       RANGER_LEVEL
	       ranger sets this environment variable to "1" or increments it if it already exists.  External programs can determine whether they were spawned from ranger by
	       checking for this variable.

       RANGER_LOAD_DEFAULT_RC
	       If this variable is set to FALSE, ranger will not load the default rc.conf.  This can save time if you copied the whole rc.conf to ~/.config/ranger/ and don't need
	       the default one at all.

       VISUAL  Defines the editor to be used for the "E" key.  Falls back to EDITOR if undefined or empty.

       EDITOR  Defines the editor to be used for the "E" key if VISUAL is undefined or empty.  Defaults to "vim".

       SHELL   Defines the shell that ranger is going to use with the :shell command and the "S" key.  Defaults to "/bin/sh".

       TERMCMD Defines the terminal emulator command that ranger is going to use with the :terminal command and the "t" run flag.  Defaults to "xterm".

       BAT_STYLE
	       Specifies the theme to be used for syntax highlighting when bat is installed, unless highlight is also installed. Find out possible values by running "bat
	       --list-themes".

       PYGMENTIZE_STYLE
	       Specifies the theme to be used for syntax highlighting when pygmentize is installed, unless highlight is also installed. Find out possible values by running:
		python -c 'import pygments.styles; [print(stl) for stl in
		pygments.styles.get_all_styles()]'

       HIGHLIGHT_STYLE
	       Specifies the theme to be used for syntax highlighting when highlight is installed. Find out possible values by running "highlight --list-themes".

       HIGHLIGHT_TABWIDTH
	       Specifies the number of spaces to use to replace tabs in highlighted files.

       HIGHLIGHT_OPTIONS
	       highlight will pick up command line options specified in this variable. A "--style=" option specified here will override "HIGHLIGHT_STYLE". Similarly,
	       "--replace-tabs=" will override "HIGHLIGHT_TABWIDTH".

       OPENSCAD_COLORSCHEME
	       Specifies the colorscheme used by openscad while previewing 3D models. Read openscad man page for colorschemes. Ranger will default to Tomorrow Night.

       OPENSCAD_IMGSIZE
	       Specifies the internal resolution openscad will use for rendering 3D models.  The image will be downscaled to fit the preview pane. This resolution will default to
	       "1000,1000" if no value is set.

       XDG_CONFIG_HOME
	       Specifies the directory for configuration files. Defaults to $HOME/.config.

       PYTHONOPTIMIZE
	       This variable determines the optimize level of python.

	       Using PYTHONOPTIMIZE=1 (like python -O) will make python discard assertion statements.  You will gain efficiency at the cost of losing some debug info.

	       Using PYTHONOPTIMIZE=2 (like python -OO) will additionally discard any docstrings.  Using this will disable the <F1> key on commands.

       W3MIMGDISPLAY_PATH
	       By changing this variable, you can change the path of the executable file for image previews.  By default, it is set to /usr/lib/w3m/w3mimgdisplay.

EXAMPLES
       There are various examples on how to extend ranger with plugins or combine ranger with other programs.  These can be found in the /usr/share/doc/ranger/examples/ directory,
       or the doc/ranger/ that is provided along with the source code.

LICENSE
       GNU General Public License 3 or (at your option) any later version.

LINKS
       Download: <https://ranger.github.io/ranger-stable.tar.gz>
       The project page: <https://ranger.github.io/>
       The mailing list: <https://savannah.nongnu.org/mail/?group=ranger>
       IRC channel: #ranger on freenode.net

       ranger is maintained with the git version control system.  To fetch a fresh copy, run:

	git clone git@github.com:ranger/ranger.git

SEE ALSO
       rifle(1)

BUGS
       Report bugs here: <https://github.com/ranger/ranger/issues>

       Please include as much relevant information as possible.  For the most diagnostic output, run ranger like this: "PYTHONOPTIMIZE= ranger --debug"

2019-12-31									    ranger-1.9.3									   RANGER(1)
