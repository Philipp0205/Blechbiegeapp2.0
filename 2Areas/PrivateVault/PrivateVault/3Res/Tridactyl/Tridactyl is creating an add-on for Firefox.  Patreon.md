-   Welcome to the fourth tips and tricks newsletter for donors! Sorry for the extreme tardiness - I moved house and lost track of time.
    
    This newsletter is going to cover probably the most important feature of Tridactyl: the ability to have stuff happen when you press keys in a certain order, which we call binding. It's a topic with a surprising amount of depth so feel free to dip in and out of this newsletter. It's probably a bit too long and broad to tackle in one sitting.
    
    **\# Binding**
    
    In Tridactyl, we bind sequences of keypresses to ex-strings (also called ex-commands) which are immediately executed. Most actions in Tridactyl - for example, scrolling down (\`:scrollline\`) or switching to a specific tab (\`:tab \[N\]\`) - are ex-commands. Keys which are not part of a valid key-sequence are passed through to websites and Firefox.
    
    Firefox reserves some key-combinations such as Ctrl-T and Ctrl-W; Tridactyl binds using these key combinations will not work (and there is no easy way of finding out other than just trying them). If you're feeling intrepid you can overcome this restriction by running this script on Linux - [https://github.com/alerque/que-firefox/blob/6dd5d6c9e1f60ff888cda33d8f2c198458b14a71/bin/patch-firefox.sh](https://github.com/alerque/que-firefox/blob/6dd5d6c9e1f60ff888cda33d8f2c198458b14a71/bin/patch-firefox.sh) - but you'll need to run it each time Firefox updates.
    
    We don't map key sequences to key sequences like Vim does (so, for example, you can't bind j to the down arrow) due to Firefox limitations.
    
    The general syntax for binding is simply \`:bind \[key sequence\] \[ex-string\]\`. We'll now get into the gory details...
    
    **\## Key sequence syntax**
    
    Each element of a key sequence is either:
    
    \-   a single character - such as \`j\` representing a keypress of \`j\` - or
    
    \-   a special representation enclosed by angle brackets \`<>\` of a set of zero or more special modifiers and a single character or a special key, for example \`<C-ArrowUp>\`, with a dash separating the modifiers and the character.
    
    The special permitted modifiers are:
    
    \-   \`C\` for left or right ctrl
    
    \-   \`A\` for left alt
    
    \-   \`M\` for the "meta" key (splat on Macintosh - ill-defined on other OSes)
    
    \-   \`S\` for left or right shift. Note that characters such as \`@\` which require the shift key to be pressed to be entered do not need the \`S\` modifier to be specified.
    
    The names of special keys can be found here: [https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/key/Key\_Values](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/key/Key_Values)
    
    A key sequence is made up of a series of elements with no separators between them.
    
    For example, the key sequence \`,<C-ArrowDown>k\` would match the following interaction with your keyboard:
    
    1\. \`,\` pressed and released
    
    2\. \`Control\` pressed and held
    
    3\. \`ArrowDown\` pressed and released
    
    4\. \`Control\` released
    
    5\. \`k\` pressed and released
    
    **\## Numeric prefixes**
    
    All binds accept numeric prefixes, such as \`2gt\` which would take you to the second tab. They do this by simply appending the supplied prefix to the bound ex-string before it is executed. For example, if I run
    
    \`\`\`
    
    :bind ,j fillcmdline tabopen
    
    10,j
    
    \`\`\`
    
    \`fillcmdline tabopen 10\` will be executed and the command line will appear prefilled with \`:tabopen 10 \`.
    
    This does mean that binds cannot start with a numeric prefix (but e.g. \`bind ,1 \[ex string\]\` does work).
    
    Not all ex-strings will do anything meaningful with the supplied count - but many will. If there is a command that you would like to support counts, just file an issue - it's usually easy for us to add.
    
    **\## Binding in other modes**
    
    By default, \`:bind\` binds key sequences to ex-strings in normal mode (the mode you are in most of the time). You can create bindings in all of the modes in Tridactyl - even \`ignore\` mode - very simply:
    
    \`:bind --mode=\[modename\] \[key sequence\] \[ex-string\]\`
    
    For example, to make \`:\` work in ignore mode, you could run \`:bind --mode=ignore : fillcmdline\_notrail\`. Ex-strings that are exclusively meaningful in a specific mode have the syntax \`\[mode\].\[command name\]\` - for example, \`ex.accept\_line\` is the ex-string that tells Tridactyl to execute the command that is currently written in the command line. See the "Viewing binds" section for more details on these mode-specific ex-strings.
    
    **\# Unbinding**
    
    Unbound keys are passed through to the webpage or Firefox. Unbind a key sequence with \`:unbind \[--mode=\[mode=normal\] \[keysequence\]\`, for example, \`:unbind <C-f>\`.
    
    **\## \`blacklistkeys\`**
    
    Keys which are not bound in Tridactyl are passed through to websites and Firefox, so websites and Firefox can bind actions to them. If a website wants to bind to a key, usually it takes priority over Firefox except for a few special key combinations.
    
    If a page is stealing a key that you want Firefox to claim, for example, \`'\` (Firefox's "focus link matching text" mode), run \`:set blacklistkeys \["'","/"\]\`. Note that you must use JavaScript array syntax and that you need to include all the keys you wish to protect, including \`/\` which is protected by default. If you omitted \`/\` it would no longer be protected.
    
    NB: this works on most but not all pages. See \[issue #904\]([https://github.com/tridactyl/tridactyl/issues/904).](https://github.com/tridactyl/tridactyl/issues/904).)
    
    **\# Resetting a bind to default**
    
    \`reset \[key sequence\]\` resets the key sequence to its default value. Not to be confused with \`:unset\` which does the same thing but for settings (the insanity in the naming comes from the fact that we had keybinds before we had general settings - sorry!).
    
    **\# Per-site binds**
    
    \`:bindurl \[url regex\]\` and \`:unbindurl\` allow you to bind keys on sites that match the supplied regex. This is often used to control which links have hints displayed on them, as was explored extensively in \[the first newsletter\]([https://github.com/tridactyl/tridactyl/blob/master/doc/newsletters/tips-and-tricks/1-hint-css-selectors.md).](https://github.com/tridactyl/tridactyl/blob/master/doc/newsletters/tips-and-tricks/1-hint-css-selectors.md).)
    
    Unbinding keys per site works similarly with \`:unbindurl\`. For example, it is common to unbind \`f\` on YouTube so that YouTube's own bind for \`f\` to toggle fullscreen video can be used: \`:unbindurl ^http(s?)://youtube\\.com f\`.
    
    **\# Special modes**
    
    Most modes are just collections of key sequences bound to ex-strings. There are some exceptions to this; sometimes keys perform some other action and sometimes modes have other properties.
    
    Here I'll list each of the slightly weird modes and what is weird about them.
    
    **\## Hint mode**
    
    In hint mode, keys being fed to the hint filter are not done so using an ex-string - see \`:set hintchars\` instead to control which keys perform filtering. The rest of the commands in the mode are bound to ex-strings - for example, \`<Enter>\` is bound to \`hint.selectFocusedHint\`.
    
    **\## Insert mode**
    
    There's nothing special about keys in this mode. Insert mode is entered automatically once a text area is focused, unless you're already in \`input\` mode (e.g. from \`gi\`). You are returned to normal mode once a text area loses focus.
    
    You may find the \`text.\` ex-strings useful for manipulating text - they can be viewed by clicking the link at the top of the \`:help\` page where it says "Tridactyl also provides a few functions to manipulate text in the command line or text areas that can be found \_here\_.".
    
    **\## Ex-mode**
    
    Ex-mode, the mode you are in when the command line is open, is a fairly standard mode where key sequences are bound to ex-strings. For example, \`<C-o>yy\` is bound to \`:ex.execute\_ex\_on\_completion\_args clipboard yank\` which copies the highlighted completion to the clipboard. The exception to this is that the command line is a normal text-area - there are no key-sequences associated with characters entered into the text-area. Filtering is done on the contents of this text-area (and so, e.g., pasting text works normally there).
    
    **\## Browser mode**
    
    This mode is unlike any other. Rather than binding key sequences to ex-strings, it binds "octopus-style" Mozilla-approved keyboard shortcuts firstly to "user actions" and, if it finds none, ex-strings. It has two advantages to the other modes: it is available everywhere in the browser, including protected pages such as \`about:addons\`, and it can perform user-actions (actions which Mozilla will only allow to happen if we can prove that a user instigated it) which our usual binds cannot. For now, the only user-action we have is \`escapehatch\` which opens and closes the sidebar to get focus back to the page, bound to \`<C-,>\` by default.
    
    Valid keyboard shortcuts consist of one or more modifiers (such as control) and a normal key, so long as that combination of modifiers and key is not on a blacklist of binds that are Mozilla thinks are too important for you to redefine. No errors are provided by Mozilla if the shortcut you choose is on the blacklist - it just won't work when you press the shortcut.
    
    This blacklist varies per system - see [https://searchfox.org/mozilla-central/rev/1f4e023df8ff04b893ca792492f1e2e9629bfddb/toolkit/modules/ShortcutUtils.jsm](https://searchfox.org/mozilla-central/rev/1f4e023df8ff04b893ca792492f1e2e9629bfddb/toolkit/modules/ShortcutUtils.jsm)#315 and [https://searchfox.org/mozilla-central/rev/1f4e023df8ff04b893ca792492f1e2e9629bfddb/toolkit/modules/ShortcutUtils.jsm](https://searchfox.org/mozilla-central/rev/1f4e023df8ff04b893ca792492f1e2e9629bfddb/toolkit/modules/ShortcutUtils.jsm)#287 if you want to get an idea of how complicated it is. My personal approach is this: try binding it. If it doesn't work, assume it's on the blacklist and try a different shortcut.
    
    A workaround if your desired shortcut is on the blacklist is to use an external program to map that shortcut to another one which can be used. For example, you could use \`xkeysnail\` under X11/Linux, \`AutoHotKey\` under Windows, or \`karabiner\` under OSX.
    
    If you wanted to bind \`<C-t>\` to \`:tabopen\` to avoid focus on the address bar, with \`xkeysnail\`'s \`[config.py](http://config.py/)\` you might do:
    
    \`\`\`
    
    \# ~/.config/xkeysnail/[config.py](http://config.py/)
    
    from xkeysnail.transform import \*
    
    define\_keymap(re.compile("Firefox|Google-chrome"), {
    
        # Rebind ctrl-t to ctrl-. so it can be rebound
    
        K("C-t"): K("C-."),
    
    }, "Firefox and Chrome")
    
    \`\`\`
    
    \`\`\`
    
    \# ~/.config/tridactyl/tridactylrc
    
    bind --mode=browser <C-.> tabopen
    
    \`\`\`
    
    **\## Visual mode**
    
    As with insert mode, visual mode is entered and left automatically. This happens when text is selected or deselected and can be controlled with \`:set visual{enter,exit}auto\`.
    
    **\## N-mode mode**
    
    This is a special "meta" mode. It accepts \`N\` key sequences, regardless of validity, in the underlying mode and then executes the final command provided. There is only one explicit bind in \`nmode\`: pressing \`<Esc>\` executes the final command immediately.
    
    E.g. \`:nmode \[underlying mode\] \[key sequences to accept\] \[final ex-string\]\`. For example, in ignore mode, \`<C-o>\` is bound to \`nmode normal 1 mode ignore\`, which allows you to execute one bind in normal mode before returning to ignore mode. In normal mode, \`<C-v>\` similarly runs \`:nmode ignore 1 mode normal\` which lets you pass a single key through to a website. I personally find this particularly useful on YouTube: \`<C-v>f\` toggles fullscreen video by using the default YouTube bind.
    
    **\# Mapping keys to keys for Tridactyl**
    
    You can map single characters to other characters within Tridactyl with \`keymap \[source\] \[dest\]\`.
    
    This is mostly useful for non-QWERTY users who want to be able to use Tridactyl binds without having to rebind lots of them manually. See the wiki for example usage for Cyrillic and bépo layouts: [https://github.com/tridactyl/tridactyl/wiki/Internationalisation.](https://github.com/tridactyl/tridactyl/wiki/Internationalisation.)
    
    **\# Getting the command line back**
    
    There's nothing in Tridactyl that prevents you from unbinding \`:\`, the key which lets you access the command line. If this happens to you, you can get it back easily by using the Firefox address bar to run \`tri reset :\`. In general \`tri \[ex-command\]\` is mostly equivalent to running the supplied ex-command in the command line and is very handy in a pinch.
    
    **\# Viewing binds**
    
    You can see binds with bind completions (e.g. \`:bind --mode=visual\`) or, en masse, with \`:viewconfig \[name of bind store\]\`. All of these "store" names end with the word \`maps\`. For sentimental reasons the most common modes have irregular names. These are:
    
    \-   normal mode: \`nmaps\`
    
    \-   insert mode: \`imaps\`
    
    \-   visual mode: \`vmaps\`
    
    Every other mode, including custom modes, follows the convention \`\[mode name\]maps\`. For example, ignore mode has the store \`ignoremaps\`.
    
    So to view the ignore mode bindings you can run \`:viewconfig ignoremaps\`. If you wish to only view the bindings that you have set, run \`:viewconfig --user ignoremaps\`.
    
    For normal mode you can also do \`:help \[key sequence\]\`.
    
    There is currently a bug in Tridactyl where the help for ex-strings for other modes, e.g. \`hint.\` is not available. Follow [https://github.com/tridactyl/tridactyl/issue/3626](https://github.com/tridactyl/tridactyl/issue/3626) and [https://github.com/tridactyl/tridactyl/issue/2926](https://github.com/tridactyl/tridactyl/issue/2926) for updates.
    
    **\# Shadowing**
    
    If you try to bind to a key sequence for which there already exists a bind to a prefix of that key sequence, you will get a warning and you will be unable to use the bind (although it will still be made).
    
    For example, if you have a bind for \`j\` and add a bind \`jk\`, you will get a warning that \`jk\` is shadowed by \`j\` - you won't be able to execute \`jk\` as the bind for \`j\` will immediately be executed when you press \`j\`. However, you would be able to bind to \`,jk\` and execute that bind. If you wished to be able to use \`jk\` you would first need to run \`:unbind j\`.
    
    **\# Custom modes**
    
    Creating a new mode is very straightforward: simply add a bind with \`:bind --mode=\[new modename\]\`. It's wise to make this first bind be a way to return to normal mode, e.g. \`:bind --mode=mynewmode <esc> mode normal\`. You can enter the mode with \`:mode \[new modename\]\`. You might want to run this from a bind or in an autocmd, e.g. \`:autocmd DocStart ^[https://mysite.com](https://mysite.com/) mode mysitemode\`.</esc>
    
    Custom modes can serve a similar purpose to \`:bindurl\`, but are easier to apply to multiple sites or across parts of a site. For example, you might want a special \`video\` mode that you trigger on \`:autocmd FullscreenEnter\`.
    
    **\## Inheritance**
    
    Custom modes are often existing modes plus a few extra binds - by default, for example, \`visual\` mode is based on \`normal\` mode and \`input\` mode (where you can press \`<Tab>\` to cycle through text boxes) is based on \`insert\` mode.
    
    We have made this marginally less painful by adding a special optional \`🕷🕷INHERITS🕷🕷\` field to the bind stores, which tells a mode that it should add its bindings on top of the specified mode. For now, only default bindings are inherited - bindings you make to modes are not inherited - but we'd like to fix that someday.
    
    You can set the field with \`set \[mode name\]maps.🕷🕷INHERITS🕷🕷 \[mode name to inherit from\]maps\`. E.g. \`set youtubemaps.🕷🕷INHERITS🕷🕷 ignoremaps\` if I had made a \`youtube\` mode. NB: the \`\[mode name\]maps\` follow the naming conventions specified in the "Viewing binds" section.
    
    **\# Final remarks**
    
    The next tips and tricks newsletter will be on the native messenger, but the next newsletter you will receive will be the quarterly newsletter. I'll probably finish that within a week or two. And apologies once again for the lateness of this newsletter!
    
    Thanks for your support, bovine3dom
    
    Welcome to the fourth tips and tricks newsletter for donors! Sorry for the extreme tardiness - I moved house and lost track of time.
    
    This newsletter is going to cover probably the most important feature of Tridactyl: the ability to have stuff happen when you press keys in a certain order, which we call binding. It's a topic with a surprising amount of depth so feel free to dip in and out of this newsletter. It's probably a bit too long and broad to tackle in one sitting.
    
    **\# Binding**
    
    In Tridactyl, we bind sequences of keypresses to ex-strings (also called ex-commands) which are immediately executed. Most actions in Tridactyl - for example, scrolling down (\`:scrollline\`) or switching to a specific tab (\`:tab \[N\]\`) - are ex-commands. Keys which are not part of a valid key-sequence are passed through to websites and Firefox.
    
    Firefox reserves some key-combinations such as Ctrl-T and Ctrl-W; Tridactyl binds using these key combinations will not work (and there is no easy way of finding out other than just trying them). If you're feeling intrepid you can overcome this restriction by running this script on Linux - [https://github.com/alerque/que-firefox/blob/6dd5d6c9e1f60ff888cda33d8f2c198458b14a71/bin/patch-firefox.sh](https://github.com/alerque/que-firefox/blob/6dd5d6c9e1f60ff888cda33d8f2c198458b14a71/bin/patch-firefox.sh) - but you'll need to run it each time Firefox updates.
    
    We don't map key sequences to key sequences like Vim does (so, for example, you can't bind j to the down arrow) due to Firefox limitations.
    
    The general syntax for binding is simply \`:bind \[key sequence\] \[ex-string\]\`. We'll now get into the gory details...
    
    **\## Key sequence syntax**
    
    Each element of a key sequence is either:
    
    \-   a single character - such as \`j\` representing a keypress of \`j\` - or
    
    \-   a special representation enclosed by angle brackets \`<>\` of a set of zero or more special modifiers and a single character or a special key, for example \`<C-ArrowUp>\`, with a dash separating the modifiers and the character.
    
    The special permitted modifiers are:
    
    \-   \`C\` for left or right ctrl
    
    \-   \`A\` for left alt
    
    \-   \`M\` for the "meta" key (splat on Macintosh - ill-defined on other OSes)
    
    \-   \`S\` for left or right shift. Note that characters such as \`@\` which require the shift key to be pressed to be entered do not need the \`S\` modifier to be specified.
    
    The names of special keys can be found here: [https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/key/Key\_Values](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/key/Key_Values)
    
    A key sequence is made up of a series of elements with no separators between them.
    
    For example, the key sequence \`,<C-ArrowDown>k\` would match the following interaction with your keyboard:
    
    1\. \`,\` pressed and released
    
    2\. \`Control\` pressed and held
    
    3\. \`ArrowDown\` pressed and released
    
    4\. \`Control\` released
    
    5\. \`k\` pressed and released
    
    **\## Numeric prefixes**
    
    All binds accept numeric prefixes, such as \`2gt\` which would take you to the second tab. They do this by simply appending the supplied prefix to the bound ex-string before it is executed. For example, if I run
    
    \`\`\`
    
    :bind ,j fillcmdline tabopen
    
    10,j
    
    \`\`\`
    
    \`fillcmdline tabopen 10\` will be executed and the command line will appear prefilled with \`:tabopen 10 \`.
    
    This does mean that binds cannot start with a numeric prefix (but e.g. \`bind ,1 \[ex string\]\` does work).
    
    Not all ex-strings will do anything meaningful with the supplied count - but many will. If there is a command that you would like to support counts, just file an issue - it's usually easy for us to add.
    
    **\## Binding in other modes**
    
    By default, \`:bind\` binds key sequences to ex-strings in normal mode (the mode you are in most of the time). You can create bindings in all of the modes in Tridactyl - even \`ignore\` mode - very simply:
    
    \`:bind --mode=\[modename\] \[key sequence\] \[ex-string\]\`
    
    For example, to make \`:\` work in ignore mode, you could run \`:bind --mode=ignore : fillcmdline\_notrail\`. Ex-strings that are exclusively meaningful in a specific mode have the syntax \`\[mode\].\[command name\]\` - for example, \`ex.accept\_line\` is the ex-string that tells Tridactyl to execute the command that is currently written in the command line. See the "Viewing binds" section for more details on these mode-specific ex-strings.
    
    **\# Unbinding**
    
    Unbound keys are passed through to the webpage or Firefox. Unbind a key sequence with \`:unbind \[--mode=\[mode=normal\] \[keysequence\]\`, for example, \`:unbind <C-f>\`.
    
    **\## \`blacklistkeys\`**
    
    Keys which are not bound in Tridactyl are passed through to websites and Firefox, so websites and Firefox can bind actions to them. If a website wants to bind to a key, usually it takes priority over Firefox except for a few special key combinations.
    
    If a page is stealing a key that you want Firefox to claim, for example, \`'\` (Firefox's "focus link matching text" mode), run \`:set blacklistkeys \["'","/"\]\`. Note that you must use JavaScript array syntax and that you need to include all the keys you wish to protect, including \`/\` which is protected by default. If you omitted \`/\` it would no longer be protected.
    
    NB: this works on most but not all pages. See \[issue #904\]([https://github.com/tridactyl/tridactyl/issues/904).](https://github.com/tridactyl/tridactyl/issues/904).)
    
    **\# Resetting a bind to default**
    
    \`reset \[key sequence\]\` resets the key sequence to its default value. Not to be confused with \`:unset\` which does the same thing but for settings (the insanity in the naming comes from the fact that we had keybinds before we had general settings - sorry!).
    
    **\# Per-site binds**
    
    \`:bindurl \[url regex\]\` and \`:unbindurl\` allow you to bind keys on sites that match the supplied regex. This is often used to control which links have hints displayed on them, as was explored extensively in \[the first newsletter\]([https://github.com/tridactyl/tridactyl/blob/master/doc/newsletters/tips-and-tricks/1-hint-css-selectors.md).](https://github.com/tridactyl/tridactyl/blob/master/doc/newsletters/tips-and-tricks/1-hint-css-selectors.md).)
    
    Unbinding keys per site works similarly with \`:unbindurl\`. For example, it is common to unbind \`f\` on YouTube so that YouTube's own bind for \`f\` to toggle fullscreen video can be used: \`:unbindurl ^http(s?)://youtube\\.com f\`.
    
    **\# Special modes**
    
    Most modes are just collections of key sequences bound to ex-strings. There are some exceptions to this; sometimes keys perform some other action and sometimes modes have other properties.
    
    Here I'll list each of the slightly weird modes and what is weird about them.
    
    **\## Hint mode**
    
    In hint mode, keys being fed to the hint filter are not done so using an ex-string - see \`:set hintchars\` instead to control which keys perform filtering. The rest of the commands in the mode are bound to ex-strings - for example, \`<Enter>\` is bound to \`hint.selectFocusedHint\`.
    
    **\## Insert mode**
    
    There's nothing special about keys in this mode. Insert mode is entered automatically once a text area is focused, unless you're already in \`input\` mode (e.g. from \`gi\`). You are returned to normal mode once a text area loses focus.
    
    You may find the \`text.\` ex-strings useful for manipulating text - they can be viewed by clicking the link at the top of the \`:help\` page where it says "Tridactyl also provides a few functions to manipulate text in the command line or text areas that can be found \_here\_.".
    
    **\## Ex-mode**
    
    Ex-mode, the mode you are in when the command line is open, is a fairly standard mode where key sequences are bound to ex-strings. For example, \`<C-o>yy\` is bound to \`:ex.execute\_ex\_on\_completion\_args clipboard yank\` which copies the highlighted completion to the clipboard. The exception to this is that the command line is a normal text-area - there are no key-sequences associated with characters entered into the text-area. Filtering is done on the contents of this text-area (and so, e.g., pasting text works normally there).
    
    **\## Browser mode**
    
    This mode is unlike any other. Rather than binding key sequences to ex-strings, it binds "octopus-style" Mozilla-approved keyboard shortcuts firstly to "user actions" and, if it finds none, ex-strings. It has two advantages to the other modes: it is available everywhere in the browser, including protected pages such as \`about:addons\`, and it can perform user-actions (actions which Mozilla will only allow to happen if we can prove that a user instigated it) which our usual binds cannot. For now, the only user-action we have is \`escapehatch\` which opens and closes the sidebar to get focus back to the page, bound to \`<C-,>\` by default.
    
    Valid keyboard shortcuts consist of one or more modifiers (such as control) and a normal key, so long as that combination of modifiers and key is not on a blacklist of binds that are Mozilla thinks are too important for you to redefine. No errors are provided by Mozilla if the shortcut you choose is on the blacklist - it just won't work when you press the shortcut.
    
    This blacklist varies per system - see [https://searchfox.org/mozilla-central/rev/1f4e023df8ff04b893ca792492f1e2e9629bfddb/toolkit/modules/ShortcutUtils.jsm](https://searchfox.org/mozilla-central/rev/1f4e023df8ff04b893ca792492f1e2e9629bfddb/toolkit/modules/ShortcutUtils.jsm)#315 and [https://searchfox.org/mozilla-central/rev/1f4e023df8ff04b893ca792492f1e2e9629bfddb/toolkit/modules/ShortcutUtils.jsm](https://searchfox.org/mozilla-central/rev/1f4e023df8ff04b893ca792492f1e2e9629bfddb/toolkit/modules/ShortcutUtils.jsm)#287 if you want to get an idea of how complicated it is. My personal approach is this: try binding it. If it doesn't work, assume it's on the blacklist and try a different shortcut.
    
    A workaround if your desired shortcut is on the blacklist is to use an external program to map that shortcut to another one which can be used. For example, you could use \`xkeysnail\` under X11/Linux, \`AutoHotKey\` under Windows, or \`karabiner\` under OSX.
    
    If you wanted to bind \`<C-t>\` to \`:tabopen\` to avoid focus on the address bar, with \`xkeysnail\`'s \`[config.py](http://config.py/)\` you might do:
    
    \`\`\`
    
    \# ~/.config/xkeysnail/[config.py](http://config.py/)
    
    from xkeysnail.transform import \*
    
    define\_keymap(re.compile("Firefox|Google-chrome"), {
    
        # Rebind ctrl-t to ctrl-. so it can be rebound
    
        K("C-t"): K("C-."),
    
    }, "Firefox and Chrome")
    
    \`\`\`
    
    \`\`\`
    
    \# ~/.config/tridactyl/tridactylrc
    
    bind --mode=browser <C-.> tabopen
    
    \`\`\`
    
    **\## Visual mode**
    
    As with insert mode, visual mode is entered and left automatically. This happens when text is selected or deselected and can be controlled with \`:set visual{enter,exit}auto\`.
    
    **\## N-mode mode**
    
    This is a special "meta" mode. It accepts \`N\` key sequences, regardless of validity, in the underlying mode and then executes the final command provided. There is only one explicit bind in \`nmode\`: pressing \`<Esc>\` executes the final command immediately.
    
    E.g. \`:nmode \[underlying mode\] \[key sequences to accept\] \[final ex-string\]\`. For example, in ignore mode, \`<C-o>\` is bound to \`nmode normal 1 mode ignore\`, which allows you to execute one bind in normal mode before returning to ignore mode. In normal mode, \`<C-v>\` similarly runs \`:nmode ignore 1 mode normal\` which lets you pass a single key through to a website. I personally find this particularly useful on YouTube: \`<C-v>f\` toggles fullscreen video by using the default YouTube bind.
    
    **\# Mapping keys to keys for Tridactyl**
    
    You can map single characters to other characters within Tridactyl with \`keymap \[source\] \[dest\]\`.
    
    This is mostly useful for non-QWERTY users who want to be able to use Tridactyl binds without having to rebind lots of them manually. See the wiki for example usage for Cyrillic and bépo layouts: [https://github.com/tridactyl/tridactyl/wiki/Internationalisation.](https://github.com/tridactyl/tridactyl/wiki/Internationalisation.)
    
    **\# Getting the command line back**
    
    There's nothing in Tridactyl that prevents you from unbinding \`:\`, the key which lets you access the command line. If this happens to you, you can get it back easily by using the Firefox address bar to run \`tri reset :\`. In general \`tri \[ex-command\]\` is mostly equivalent to running the supplied ex-command in the command line and is very handy in a pinch.
    
    **\# Viewing binds**
    
    You can see binds with bind completions (e.g. \`:bind --mode=visual\`) or, en masse, with \`:viewconfig \[name of bind store\]\`. All of these "store" names end with the word \`maps\`. For sentimental reasons the most common modes have irregular names. These are:
    
    \-   normal mode: \`nmaps\`
    
    \-   insert mode: \`imaps\`
    
    \-   visual mode: \`vmaps\`
    
    Every other mode, including custom modes, follows the convention \`\[mode name\]maps\`. For example, ignore mode has the store \`ignoremaps\`.
    
    So to view the ignore mode bindings you can run \`:viewconfig ignoremaps\`. If you wish to only view the bindings that you have set, run \`:viewconfig --user ignoremaps\`.
    
    For normal mode you can also do \`:help \[key sequence\]\`.
    
    There is currently a bug in Tridactyl where the help for ex-strings for other modes, e.g. \`hint.\` is not available. Follow [https://github.com/tridactyl/tridactyl/issue/3626](https://github.com/tridactyl/tridactyl/issue/3626) and [https://github.com/tridactyl/tridactyl/issue/2926](https://github.com/tridactyl/tridactyl/issue/2926) for updates.
    
    **\# Shadowing**
    
    If you try to bind to a key sequence for which there already exists a bind to a prefix of that key sequence, you will get a warning and you will be unable to use the bind (although it will still be made).
    
    For example, if you have a bind for \`j\` and add a bind \`jk\`, you will get a warning that \`jk\` is shadowed by \`j\` - you won't be able to execute \`jk\` as the bind for \`j\` will immediately be executed when you press \`j\`. However, you would be able to bind to \`,jk\` and execute that bind. If you wished to be able to use \`jk\` you would first need to run \`:unbind j\`.
    
    **\# Custom modes**
    
    Creating a new mode is very straightforward: simply add a bind with \`:bind --mode=\[new modename\]\`. It's wise to make this first bind be a way to return to normal mode, e.g. \`:bind --mode=mynewmode <esc> mode normal\`. You can enter the mode with \`:mode \[new modename\]\`. You might want to run this from a bind or in an autocmd, e.g. \`:autocmd DocStart ^[https://mysite.com](https://mysite.com/) mode mysitemode\`.</esc>
    
    Custom modes can serve a similar purpose to \`:bindurl\`, but are easier to apply to multiple sites or across parts of a site. For example, you might want a special \`video\` mode that you trigger on \`:autocmd FullscreenEnter\`.
    
    **\## Inheritance**
    
    Custom modes are often existing modes plus a few extra binds - by default, for example, \`visual\` mode is based on \`normal\` mode and \`input\` mode (where you can press \`<Tab>\` to cycle through text boxes) is based on \`insert\` mode.
    
    We have made this marginally less painful by adding a special optional \`🕷🕷INHERITS🕷🕷\` field to the bind stores, which tells a mode that it should add its bindings on top of the specified mode. For now, only default bindings are inherited - bindings you make to modes are not inherited - but we'd like to fix that someday.
    
    You can set the field with \`set \[mode name\]maps.🕷🕷INHERITS🕷🕷 \[mode name to inherit from\]maps\`. E.g. \`set youtubemaps.🕷🕷INHERITS🕷🕷 ignoremaps\` if I had made a \`youtube\` mode. NB: the \`\[mode name\]maps\` follow the naming conventions specified in the "Viewing binds" section.
    
    **\# Final remarks**
    
    The next tips and tricks newsletter will be on the native messenger, but the next newsletter you will receive will be the quarterly newsletter. I'll probably finish that within a week or two. And apologies once again for the lateness of this newsletter!
    
    Thanks for your support, bovine3dom
    
-   Welcome to the third tips & tricks newsletter for donors!
    
    To really unlock the power of Tridactyl, you'll want to write your own ex-commands to automate actions that you do frequently. This clearly is a very broad topic, so in this tutorial I'm just going to cover how to create an ex-command that accepts arguments, \`:composite\` for combining ex-commands, and how to use \`:js\` and \`:jsb\` to create more complex commands.
    
    ### **\# Ex-aliases: naming commands**
    
    \`:command \[alias\] \[ex string\]\` is a very simple way of creating your own ex-command for convenience. Once an alias is set, any time that alias is used as an ex-command it is replaced with the ex string that it represents, with any subsequent arguments left unmodified. For example, \`:command tbb tabpen -b\` would mean that \`:tbb [news.bbc.co.uk](http://news.bbc.co.uk/)\` would open BBC news in a background tab. Aliases automatically get completions for their underlying ex-command.
    
    ### **\# Stringing commands together with \`:composite\`**
    
    If you want to use multiple commands you can use \`:composite \[ex string\]; \[ex string\] ...\` to chain them together. A classic example is the default \`D\` bind of \`:composite tabclose; tabprev\` which closes a tab and then takes you to the tab to the left rather than the default Firefox behaviour of going to the right.
    
    In some circumstances ex-commands return useful values. These can be passed as strings as the last argument to the next ex-string in the sequence by separating the commands with pipes, \`|\`, rather than semi-colons. Very few default ex-commands do this - \`:current\_url\` is one, as is \`:shellescape\` - but it is quite common for custom commands that use \`:js\` or :\`jsb\` to do this.
    
    For example, the following two lines are equivalent:
    
    \`\`\`
    
    composite current\_url | fillcmdline\_notrail open
    
    composite js document.location.href | fillcmdline\_notrail open
    
    \`\`\`
    
    \*\*NB:\*\* \`:composite\` steals semi-colons from \`:js\`, etc. If you need to use a semi-colon in \`:js\`, simply make it into a \`:command\` first and use that instead.
    
    ### **\# \`:js\` and \`:jsb\` for more flexibility**
    
    But what if you want to supply arguments to an ex-string in a place other than the start? This is where you need to each for \`:js\` or its counterpart for the background script (more on that later), \`:jsb\`. These commands execute scripts in JavaScript in the current tab or background script respectively.
    
    There are two ways to supply an argument to a \`:js{,b}\` command: you may provide a \`-p\` flag, which accepts a single argument and stores it in the magic variable \`JS\_ARG\`, or \`-d\[char\]\` where you supply a terminating character which you will use in your script, and then space separated arguments are stored in a magic \`JS\_ARGS\` array. Note that both of these flags only make sense if you don't execute them immediately; the most common usage is via an ex-alias of \`:command js -p ...\`, which merely stores the ex string for later execution.
    
    Here are a couple of examples:
    
    \`\`\`
    
    :command loudecho\_oneword js -p window.alert(JS\_ARG)
    
    :loudecho\_oneword LOUD
    
    :command loudecho\_morewords js -dŐ window.alert(JS\_ARGS.join(" "))Ő
    
    :loudecho\_morewords THIS IS LOUD
    
    \`\`\`
    
    I don't want to get into too much detail about what things are available with \`:js\` and \`:jsb\`. If you want to explore it you'll find most interesting things are available on the \`tri\` and \`browser\` objects. Run \`:js console.log(tri)\` and look in the Firefox web console to see it interactively.
    
    Particularly of note is \`tri.excmds\` which contains all of the ex-commands in Tridactyl. For example, the following lines are identical:
    
    \`\`\`
    
    :tabopen search meaning of life
    
    :js tri.excmds.tabopen("search", "meaning", "of", "life")
    
    \`\`\`
    
    If you need to write an async function in \`:js\` simply use a closure:
    
    \`\`\`
    
    :js (async () => {...})()
    
    \`\`\`
    
    \`:composite\` automatically awaits the result of any promises returned, so you can pipe the results into other ex-commands if you wish.
    
    ### **\# Content \`:js\` versus background \`:jsb\`**
    
    To understand the difference between \`:js\` and \`:jsb\` you unfortunately are going to have to learn more about the architecture of WebExtensions than you may have otherwise wished. \`:js\` runs in Tridactyl's content script in the current active tab. \`:jsb\` runs in Tridactyl's background script.
    
    The content script has access to the page you are on - with a real \`window\` object - but very few \`browser\` functions, such as those for opening new tabs. Tridactyl provides a \`tri.browserBg\` proxy that allows you to access almost all of these. Additionally, all ex-commands are accessible via \`tri.excmds\` in both content and background scripts. However, \`:js\` requires Tridactyl to be running in the active tab - so running things in \`:js\` from your RC file, which often runs before Tridactyl has loaded in any tabs, is a bad idea. Errors and logs from the content script appear in the normal Firefox Web Console, accessible by pressing ctrl-shift-k.
    
    The background script has access to many more \`browser\` functions and is much longer lived that the content scripts, which typically reload with every page navigation, but it has no direct access to any web pages. If you need to pass information between \`:js\` and \`:jsb\`, simply use \`:composite\`. Errors and output from the background script only appears in the Browser Console, accessible via \`about:debugging\` and clicking on "Inspect" next to Tridactyl on the "This Firefox" tab.
    
    There is an extra caveat here in that content scripts on Tridactyl's own pages - the new tab page, the help pages etc. - have access to many of the objects that are otherwise only available in the background script. This can be useful - it means you can explore the objects available in the background scripts without having to open \`about:debugging\` to access the Browser Console in Tridactyl's background context - but more often it just catches people out who craft \`:js\` commands which only work on the new tab pages. I'd suggest firmly that you develop your scripts on "real" pages therefore.
    
    ### **\# Getting further help**
    
    The best place to find information on how to use the WebExtension API is the [MDN website](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions). Usually simply searching for e.g. "create tab MDN" on your favourite search engine will be enough to get you to the right page.
    
    Otherwise, \`:help composite\`, \`:help command\` and \`:help js\` all contain useful information.
    
    ### **\# Final thoughts**
    
    I hope this tutorial was useful. I'm hoping to add custom completions for custom ex-commands within the next few months but I can't promise anything yet.
    
    The next tips & tricks newsletter is going to be on modes and key binds; the one after that will be on using the native messenger. After those two the future of this newsletter is a little uncertain - I'm going to have to seriously consider whether it's the best use of my time. Tridactyl donations have actually fallen from a peak of 800 EUR a month to about 200 EUR a month currently; if that continues to the case I'll have to reduce the amount of time I spend on Tridactyl. I suspect writing these newsletters is one of the least productive things I can do for Tridactyl so it probably makes sense to cut back on these rather than other more directly important things such as bug fixes. I'll tell you all what I've decided as soon as I've decided it.
    
    Feedback as usual is welcome (desired, even!) - you can contact me at [oliver@blanthorn.com](mailto:oliver@blanthorn.com) or on Matrix.
    
    Thanks as always for your continued support, bovine3dom
    
    Welcome to the third tips & tricks newsletter for donors!
    
    To really unlock the power of Tridactyl, you'll want to write your own ex-commands to automate actions that you do frequently. This clearly is a very broad topic, so in this tutorial I'm just going to cover how to create an ex-command that accepts arguments, \`:composite\` for combining ex-commands, and how to use \`:js\` and \`:jsb\` to create more complex commands.
    
    ### **\# Ex-aliases: naming commands**
    
    \`:command \[alias\] \[ex string\]\` is a very simple way of creating your own ex-command for convenience. Once an alias is set, any time that alias is used as an ex-command it is replaced with the ex string that it represents, with any subsequent arguments left unmodified. For example, \`:command tbb tabpen -b\` would mean that \`:tbb [news.bbc.co.uk](http://news.bbc.co.uk/)\` would open BBC news in a background tab. Aliases automatically get completions for their underlying ex-command.
    
    ### **\# Stringing commands together with \`:composite\`**
    
    If you want to use multiple commands you can use \`:composite \[ex string\]; \[ex string\] ...\` to chain them together. A classic example is the default \`D\` bind of \`:composite tabclose; tabprev\` which closes a tab and then takes you to the tab to the left rather than the default Firefox behaviour of going to the right.
    
    In some circumstances ex-commands return useful values. These can be passed as strings as the last argument to the next ex-string in the sequence by separating the commands with pipes, \`|\`, rather than semi-colons. Very few default ex-commands do this - \`:current\_url\` is one, as is \`:shellescape\` - but it is quite common for custom commands that use \`:js\` or :\`jsb\` to do this.
    
    For example, the following two lines are equivalent:
    
    \`\`\`
    
    composite current\_url | fillcmdline\_notrail open
    
    composite js document.location.href | fillcmdline\_notrail open
    
    \`\`\`
    
    \*\*NB:\*\* \`:composite\` steals semi-colons from \`:js\`, etc. If you need to use a semi-colon in \`:js\`, simply make it into a \`:command\` first and use that instead.
    
    ### **\# \`:js\` and \`:jsb\` for more flexibility**
    
    But what if you want to supply arguments to an ex-string in a place other than the start? This is where you need to each for \`:js\` or its counterpart for the background script (more on that later), \`:jsb\`. These commands execute scripts in JavaScript in the current tab or background script respectively.
    
    There are two ways to supply an argument to a \`:js{,b}\` command: you may provide a \`-p\` flag, which accepts a single argument and stores it in the magic variable \`JS\_ARG\`, or \`-d\[char\]\` where you supply a terminating character which you will use in your script, and then space separated arguments are stored in a magic \`JS\_ARGS\` array. Note that both of these flags only make sense if you don't execute them immediately; the most common usage is via an ex-alias of \`:command js -p ...\`, which merely stores the ex string for later execution.
    
    Here are a couple of examples:
    
    \`\`\`
    
    :command loudecho\_oneword js -p window.alert(JS\_ARG)
    
    :loudecho\_oneword LOUD
    
    :command loudecho\_morewords js -dŐ window.alert(JS\_ARGS.join(" "))Ő
    
    :loudecho\_morewords THIS IS LOUD
    
    \`\`\`
    
    I don't want to get into too much detail about what things are available with \`:js\` and \`:jsb\`. If you want to explore it you'll find most interesting things are available on the \`tri\` and \`browser\` objects. Run \`:js console.log(tri)\` and look in the Firefox web console to see it interactively.
    
    Particularly of note is \`tri.excmds\` which contains all of the ex-commands in Tridactyl. For example, the following lines are identical:
    
    \`\`\`
    
    :tabopen search meaning of life
    
    :js tri.excmds.tabopen("search", "meaning", "of", "life")
    
    \`\`\`
    
    If you need to write an async function in \`:js\` simply use a closure:
    
    \`\`\`
    
    :js (async () => {...})()
    
    \`\`\`
    
    \`:composite\` automatically awaits the result of any promises returned, so you can pipe the results into other ex-commands if you wish.
    
    ### **\# Content \`:js\` versus background \`:jsb\`**
    
    To understand the difference between \`:js\` and \`:jsb\` you unfortunately are going to have to learn more about the architecture of WebExtensions than you may have otherwise wished. \`:js\` runs in Tridactyl's content script in the current active tab. \`:jsb\` runs in Tridactyl's background script.
    
    The content script has access to the page you are on - with a real \`window\` object - but very few \`browser\` functions, such as those for opening new tabs. Tridactyl provides a \`tri.browserBg\` proxy that allows you to access almost all of these. Additionally, all ex-commands are accessible via \`tri.excmds\` in both content and background scripts. However, \`:js\` requires Tridactyl to be running in the active tab - so running things in \`:js\` from your RC file, which often runs before Tridactyl has loaded in any tabs, is a bad idea. Errors and logs from the content script appear in the normal Firefox Web Console, accessible by pressing ctrl-shift-k.
    
    The background script has access to many more \`browser\` functions and is much longer lived that the content scripts, which typically reload with every page navigation, but it has no direct access to any web pages. If you need to pass information between \`:js\` and \`:jsb\`, simply use \`:composite\`. Errors and output from the background script only appears in the Browser Console, accessible via \`about:debugging\` and clicking on "Inspect" next to Tridactyl on the "This Firefox" tab.
    
    There is an extra caveat here in that content scripts on Tridactyl's own pages - the new tab page, the help pages etc. - have access to many of the objects that are otherwise only available in the background script. This can be useful - it means you can explore the objects available in the background scripts without having to open \`about:debugging\` to access the Browser Console in Tridactyl's background context - but more often it just catches people out who craft \`:js\` commands which only work on the new tab pages. I'd suggest firmly that you develop your scripts on "real" pages therefore.
    
    ### **\# Getting further help**
    
    The best place to find information on how to use the WebExtension API is the [MDN website](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions). Usually simply searching for e.g. "create tab MDN" on your favourite search engine will be enough to get you to the right page.
    
    Otherwise, \`:help composite\`, \`:help command\` and \`:help js\` all contain useful information.
    
    ### **\# Final thoughts**
    
    I hope this tutorial was useful. I'm hoping to add custom completions for custom ex-commands within the next few months but I can't promise anything yet.
    
    The next tips & tricks newsletter is going to be on modes and key binds; the one after that will be on using the native messenger. After those two the future of this newsletter is a little uncertain - I'm going to have to seriously consider whether it's the best use of my time. Tridactyl donations have actually fallen from a peak of 800 EUR a month to about 200 EUR a month currently; if that continues to the case I'll have to reduce the amount of time I spend on Tridactyl. I suspect writing these newsletters is one of the least productive things I can do for Tridactyl so it probably makes sense to cut back on these rather than other more directly important things such as bug fixes. I'll tell you all what I've decided as soon as I've decided it.
    
    Feedback as usual is welcome (desired, even!) - you can contact me at [oliver@blanthorn.com](mailto:oliver@blanthorn.com) or on Matrix.
    
    Thanks as always for your continued support, bovine3dom
    
-   Hi, and welcome to the second Tridactyl tips and tricks newsletter. This is the first paywalled one going out to sponsors paying 10$ a month or more, so thanks!
    
    **\# Custom themes**
    
    Themes have a lot of control over Tridactyl's appearance - just try \`:colours halloween\` versus \`:colours shydactyl\` and \`:colours quake\` to see what I mean. (Protip: press Ctrl-Enter with a completion selected to execute it without closing the command line to test out themes quickly.)
    
    Unfortunately, themes have long been a poorly documented and slightly bizarre part of Tridactyl. While writing this guide, I ended up going back to Tridactyl and simplifying how themes are made and written several times rather than try to explain and justify our idiosyncrasies.
    
    NB: this is for the current Tridactyl Beta or yet-to-be-released stable 1.21.0+. Themes in Tridactyl Stable are still confusing : )
    
    **\# Loading custom themes**
    
    When you run \`:colours \[themename\]\`, if \`themename\` is not a built-in theme, Tridactyl uses \`:native\` to try to read \`themes/themename/themename.css\` from the same directory where your RC file is located. If you don't have an RC file Tridactyl will throw an error. It then stores this CSS file as a string in your Tridactyl configuration as \`customthemes.\[themename\]\`. Regardless of whether the theme is built-in or not, it then runs \`:set theme \[themename\]\` which tells Tridactyl to refresh the theme on the current page. If loading the theme from disk doesn't work, Tridactyl tries to load the theme from its internal storage instead.
    
    Similarly to reading themes from disk, you can run \`:colours --url \[url\] \[theme name\]\` to download and install a theme from the internet with no need for \`:native\`. After you have downloaded it once you can switch back to the theme with \`:colours \[theme name\]\`.
    
    **\# Writing your own theme**
    
    There are many tutorials online on how to use CSS to style web pages. Styling Tridactyl is very similar.
    
    The one key difference is that our default theme uses lots of variables specifically designed to make theming Tridactyl simpler. These variables set the colour of various elements of Tridactyl which are similar. For example, \`--tridactyl-bg\` sets the background colour of most parts of Tridactyl. You can find these variables and their default settings in the default theme, located in the \[Tridactyl themes folder\]([https://github.com/tridactyl/tridactyl/tree/1d9380d183679e09d9db83d62e6a01b5d3b210e3/src/static/themes/default/default.css).](https://github.com/tridactyl/tridactyl/tree/1d9380d183679e09d9db83d62e6a01b5d3b210e3/src/static/themes/default/default.css).) The default theme is loaded into every page so every other theme can fall back to it if there is nothing defined for a variable.
    
    One simple theme, then, is to just change the colours of a few things in Tridactyl, like this excerpt from the default \`greenmat\` theme does:
    
    \`\`\`
    
    :root {
    
        --tridactyl-fg: #00eb00;
    
        --tridactyl-bg: #001500;
    
        --tridactyl-cmdl-fg: #00eb00;
    
        --tridactyl-cmdl-bg: #001500;
    
    }
    
    \`\`\`
    
    Simply put that in a file in the folder specified earlier, e.g. \`~/.config/tridactyl/themes/mydark/mydark.css\` and run \`:colours mydark\` in Tridactyl to set it.
    
    We strongly recommend you use the CSS variables we provide where possible as it means that if we add a new element to Tridactyl, it is very likely that it will have colours that fit with your theme with no need for you to update it.
    
    If you want to change Tridactyl's appearance more drastically, the best way to learn more is to look at the included default themes, for example the quakelight theme: [https://github.com/tridactyl/tridactyl/blob/master/src/static/themes/quakelight/quakelight.css.](https://github.com/tridactyl/tridactyl/blob/master/src/static/themes/quakelight/quakelight.css.) The base Tridactyl theme is located at \`src/static/css/\` in the \[Tridactyl source\]([https://github.com/tridactyl/tridactyl/tree/1d9380d183679e09d9db83d62e6a01b5d3b210e3/src/static/css)](https://github.com/tridactyl/tridactyl/tree/1d9380d183679e09d9db83d62e6a01b5d3b210e3/src/static/css)) and is always loaded into every page as a base theme.
    
    ... and that's pretty much it for this newsletter, I think!
    
    I don't want to get deep into how you can use CSS for controlling how elements are displayed - there are plenty of tutorials online for doing that. \[MDN's tutorial\]([https://developer.mozilla.org/en-US/docs/Learn/CSS/First\_steps/Getting\_started)](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/Getting_started)) is good.
    
    **\# Final thoughts**
    
    I hope no-one feels shortchanged from this shorter tutorial - a lot of time went into making creating and installing new themes less weird. If anyone has any specific questions I'd be delighted to answer them.
    
    Thank you all for your support as always. Next months' tutorial will probably be on creating custom ex-commands.
    
    Cheers,
    
    bovine3dom
    
    Hi, and welcome to the second Tridactyl tips and tricks newsletter. This is the first paywalled one going out to sponsors paying 10$ a month or more, so thanks!
    
    **\# Custom themes**
    
    Themes have a lot of control over Tridactyl's appearance - just try \`:colours halloween\` versus \`:colours shydactyl\` and \`:colours quake\` to see what I mean. (Protip: press Ctrl-Enter with a completion selected to execute it without closing the command line to test out themes quickly.)
    
    Unfortunately, themes have long been a poorly documented and slightly bizarre part of Tridactyl. While writing this guide, I ended up going back to Tridactyl and simplifying how themes are made and written several times rather than try to explain and justify our idiosyncrasies.
    
    NB: this is for the current Tridactyl Beta or yet-to-be-released stable 1.21.0+. Themes in Tridactyl Stable are still confusing : )
    
    **\# Loading custom themes**
    
    When you run \`:colours \[themename\]\`, if \`themename\` is not a built-in theme, Tridactyl uses \`:native\` to try to read \`themes/themename/themename.css\` from the same directory where your RC file is located. If you don't have an RC file Tridactyl will throw an error. It then stores this CSS file as a string in your Tridactyl configuration as \`customthemes.\[themename\]\`. Regardless of whether the theme is built-in or not, it then runs \`:set theme \[themename\]\` which tells Tridactyl to refresh the theme on the current page. If loading the theme from disk doesn't work, Tridactyl tries to load the theme from its internal storage instead.
    
    Similarly to reading themes from disk, you can run \`:colours --url \[url\] \[theme name\]\` to download and install a theme from the internet with no need for \`:native\`. After you have downloaded it once you can switch back to the theme with \`:colours \[theme name\]\`.
    
    **\# Writing your own theme**
    
    There are many tutorials online on how to use CSS to style web pages. Styling Tridactyl is very similar.
    
    The one key difference is that our default theme uses lots of variables specifically designed to make theming Tridactyl simpler. These variables set the colour of various elements of Tridactyl which are similar. For example, \`--tridactyl-bg\` sets the background colour of most parts of Tridactyl. You can find these variables and their default settings in the default theme, located in the \[Tridactyl themes folder\]([https://github.com/tridactyl/tridactyl/tree/1d9380d183679e09d9db83d62e6a01b5d3b210e3/src/static/themes/default/default.css).](https://github.com/tridactyl/tridactyl/tree/1d9380d183679e09d9db83d62e6a01b5d3b210e3/src/static/themes/default/default.css).) The default theme is loaded into every page so every other theme can fall back to it if there is nothing defined for a variable.
    
    One simple theme, then, is to just change the colours of a few things in Tridactyl, like this excerpt from the default \`greenmat\` theme does:
    
    \`\`\`
    
    :root {
    
        --tridactyl-fg: #00eb00;
    
        --tridactyl-bg: #001500;
    
        --tridactyl-cmdl-fg: #00eb00;
    
        --tridactyl-cmdl-bg: #001500;
    
    }
    
    \`\`\`
    
    Simply put that in a file in the folder specified earlier, e.g. \`~/.config/tridactyl/themes/mydark/mydark.css\` and run \`:colours mydark\` in Tridactyl to set it.
    
    We strongly recommend you use the CSS variables we provide where possible as it means that if we add a new element to Tridactyl, it is very likely that it will have colours that fit with your theme with no need for you to update it.
    
    If you want to change Tridactyl's appearance more drastically, the best way to learn more is to look at the included default themes, for example the quakelight theme: [https://github.com/tridactyl/tridactyl/blob/master/src/static/themes/quakelight/quakelight.css.](https://github.com/tridactyl/tridactyl/blob/master/src/static/themes/quakelight/quakelight.css.) The base Tridactyl theme is located at \`src/static/css/\` in the \[Tridactyl source\]([https://github.com/tridactyl/tridactyl/tree/1d9380d183679e09d9db83d62e6a01b5d3b210e3/src/static/css)](https://github.com/tridactyl/tridactyl/tree/1d9380d183679e09d9db83d62e6a01b5d3b210e3/src/static/css)) and is always loaded into every page as a base theme.
    
    ... and that's pretty much it for this newsletter, I think!
    
    I don't want to get deep into how you can use CSS for controlling how elements are displayed - there are plenty of tutorials online for doing that. \[MDN's tutorial\]([https://developer.mozilla.org/en-US/docs/Learn/CSS/First\_steps/Getting\_started)](https://developer.mozilla.org/en-US/docs/Learn/CSS/First_steps/Getting_started)) is good.
    
    **\# Final thoughts**
    
    I hope no-one feels shortchanged from this shorter tutorial - a lot of time went into making creating and installing new themes less weird. If anyone has any specific questions I'd be delighted to answer them.
    
    Thank you all for your support as always. Next months' tutorial will probably be on creating custom ex-commands.
    
    Cheers,
    
    bovine3dom
    
-   Hello,
    
    Welcome to the sixth quarterly Tridactyl newsletter. As a gentle reminder, the second (and first paywalled) Tridactyl top-tips newsletter will be going out in the next few days. If you'd like to receive it, simply up your monthly pledge to 10 USD or more on GitHub sponsors (preferred, as I get ~30%+ more of your money after taxes and transaction fees) or Patreon. I really appreciate every penny you send - it directly affects how long I can afford to work on Tridactyl. This next tips newsletter will be on making custom themes.
    
    If you don't feel like you can afford the extra newsletter, don't worry about it too much. I find that when I start documenting how crazy parts of Tridactyl it is often easier to re-write how it works in Tridactyl rather than suffer the embarrassment of communicating it; so writing the tips newsletters benefits everyone. I'd also like to turn the newsletters into public wiki pages - I'll probably do that about 3 months after each one goes out.
    
    \## Highlighted new features
    
    \### Native messenger a bit quicker
    
    The big change this quarter is that we've rewritten the native messenger - the little programme that lets Tridactyl interact with your computer, for example to read your files from your filesystem or restart Firefox - in Nim, a small compiled language previously called Nimrod. Compared to the previous Python version, Nim starts up much faster leading to around speed-ups of 2-100x depending on the command and your system. Windows users who were using the cross-compiled Python executables should notice a particularly large speedup; it is very obvious when using the editor on \`<C-i>\` in a text-box if you haven't manually set \`:editorcmd\`. At the time of writing this newsletter, the native messenger wasn't quite ready for release on OSX (a lack of testing) or Windows (reimplementing \`:restart\` is non-trivial). On Linux the messenger should update automatically in the latest betas if you already have native installed - just run \`:native\` to check. \`0.2.0\` is the first Nim version of the messenger. Use \`:nativeupdate\` to update it if it hasn't updated itself.
    
    \### Other stuff
    
    Quite a few minor things have been added to Tridactyl, too. As always, I'll detail a few highlights here.
    
    \`:tabclose\` now accepts \`window\_[number.tab](http://number.tab/)\_number\` arguments, meaning that Shift-Delete works to close tabs even in other windows on \`:taball\` completions. The selected completion on \`:taball\` doesn't currently move to the next option as you would expect. I'm hoping I'll get round to implementing that soon.
    
    Three new hint modes were added: \`;x\` and \`;X\` "emergency" hint modes added if you have the native messenger and \`xdotool\` installed: these actually move the mouse and click on the element you select, so no amount of JS-shenanigans will break it. \`;K\` reversible element-"kill" hint mode added with \`:elementunhide\` to resurrect elements. \`;Y\` image-to-clipboard hint mode added.
    
    Just for fun, \`g!\` jumbles all the text on the page, leaving the start and end of each word in the same place. Give your brain some exercise.
    
    As a small quality-of-life improvement, we've changed how the clipboard commands (\`yy\`, etc) work under-the-bonnet to use a newer clipboard API. They're quite a bit quicker than they were and throw fewer errors now.
    
    We've added a few treats for advanced users, too: a \`UriChange\` event added for \`:autocmd\` for use as a last resort on modern single-page application (SPA) sites where \`DocLoad\` events don't fire. Unfortunately it uses a little bit of extra power, so don't turn it on unless you need it. Additionally, \`:js\` accepts a flag \`-d\` and an EOF character, which will then give you \`JS\_ARGS\` array to use of space-separated arguments, making it easier to make more complex ex-commands.
    
    \## Neat bug fixes
    
    \### Fewer race conditions on user input in the command line
    
    In the command line, we now wait for completions to load before processing any commands that interact with the completions. In practice this means that if you have a website that you regularly visit, you can build up muscle memory to quickly go to and select that site - say, for example, you visit \`[news.bbc.co.uk](http://news.bbc.co.uk/)\` a lot, you can access it by typing \`tne<Tab><Enter>\`.
    
    There's a caveat here in that you have to wait for the command line to have loaded at least a bit before you continue to type, but once the input box has appeared you can type as quickly as you like.
    
    With this fix, I'm personally much happier using Tridactyl than I was. For me, it is a big step towards being a reliable tool I enjoy using and away from being a janky thing that I simply put up with.
    
    \### Other stuff
    
    Help and tutor pages now follow your theme. \`:editor\` is quicker on Windows (even without the new native messenger) as we no longer check for Linux terminals which are vanishingly unlikely to exist. And that's pretty much it ... I think we must have added and then fixed lots of bugs in the beta which aren't really worth mentioning in these newsletters.
    
    \## Plans for next few months
    
    I'll keep making the tips & tricks newsletters and maybe try to advertise them a little more. We currently have 12 donors across all platforms that will receive them. In monetary terms that is getting towards the "worth it" line, I think. We'll see whether it becomes too exhausting writing them each month, especially if I start tidying them up for the wiki too.
    
    I'm still toying with the idea of looking seriously into a paid-for Chrome port, but I think I've found more things that I want to fix in Tridactyl first. I'm going to take another look at rewriting the completions code - updating the all-window-tab completions because they missed something that the one-window-tab completions had was unpleasant because there was so much duplicated code.
    
    Finally, I expect I'll spend much of the next quarter fixing bugs I didn't spot in the new native messenger : )
    
    As always, thanks for your generous support,
    
    bovine3dom and the rest of the Tridactyl developers
    
    Hello,
    
    Welcome to the sixth quarterly Tridactyl newsletter. As a gentle reminder, the second (and first paywalled) Tridactyl top-tips newsletter will be going out in the next few days. If you'd like to receive it, simply up your monthly pledge to 10 USD or more on GitHub sponsors (preferred, as I get ~30%+ more of your money after taxes and transaction fees) or Patreon. I really appreciate every penny you send - it directly affects how long I can afford to work on Tridactyl. This next tips newsletter will be on making custom themes.
    
    If you don't feel like you can afford the extra newsletter, don't worry about it too much. I find that when I start documenting how crazy parts of Tridactyl it is often easier to re-write how it works in Tridactyl rather than suffer the embarrassment of communicating it; so writing the tips newsletters benefits everyone. I'd also like to turn the newsletters into public wiki pages - I'll probably do that about 3 months after each one goes out.
    
    \## Highlighted new features
    
    \### Native messenger a bit quicker
    
    The big change this quarter is that we've rewritten the native messenger - the little programme that lets Tridactyl interact with your computer, for example to read your files from your filesystem or restart Firefox - in Nim, a small compiled language previously called Nimrod. Compared to the previous Python version, Nim starts up much faster leading to around speed-ups of 2-100x depending on the command and your system. Windows users who were using the cross-compiled Python executables should notice a particularly large speedup; it is very obvious when using the editor on \`<C-i>\` in a text-box if you haven't manually set \`:editorcmd\`. At the time of writing this newsletter, the native messenger wasn't quite ready for release on OSX (a lack of testing) or Windows (reimplementing \`:restart\` is non-trivial). On Linux the messenger should update automatically in the latest betas if you already have native installed - just run \`:native\` to check. \`0.2.0\` is the first Nim version of the messenger. Use \`:nativeupdate\` to update it if it hasn't updated itself.
    
    \### Other stuff
    
    Quite a few minor things have been added to Tridactyl, too. As always, I'll detail a few highlights here.
    
    \`:tabclose\` now accepts \`window\_[number.tab](http://number.tab/)\_number\` arguments, meaning that Shift-Delete works to close tabs even in other windows on \`:taball\` completions. The selected completion on \`:taball\` doesn't currently move to the next option as you would expect. I'm hoping I'll get round to implementing that soon.
    
    Three new hint modes were added: \`;x\` and \`;X\` "emergency" hint modes added if you have the native messenger and \`xdotool\` installed: these actually move the mouse and click on the element you select, so no amount of JS-shenanigans will break it. \`;K\` reversible element-"kill" hint mode added with \`:elementunhide\` to resurrect elements. \`;Y\` image-to-clipboard hint mode added.
    
    Just for fun, \`g!\` jumbles all the text on the page, leaving the start and end of each word in the same place. Give your brain some exercise.
    
    As a small quality-of-life improvement, we've changed how the clipboard commands (\`yy\`, etc) work under-the-bonnet to use a newer clipboard API. They're quite a bit quicker than they were and throw fewer errors now.
    
    We've added a few treats for advanced users, too: a \`UriChange\` event added for \`:autocmd\` for use as a last resort on modern single-page application (SPA) sites where \`DocLoad\` events don't fire. Unfortunately it uses a little bit of extra power, so don't turn it on unless you need it. Additionally, \`:js\` accepts a flag \`-d\` and an EOF character, which will then give you \`JS\_ARGS\` array to use of space-separated arguments, making it easier to make more complex ex-commands.
    
    \## Neat bug fixes
    
    \### Fewer race conditions on user input in the command line
    
    In the command line, we now wait for completions to load before processing any commands that interact with the completions. In practice this means that if you have a website that you regularly visit, you can build up muscle memory to quickly go to and select that site - say, for example, you visit \`[news.bbc.co.uk](http://news.bbc.co.uk/)\` a lot, you can access it by typing \`tne<Tab><Enter>\`.
    
    There's a caveat here in that you have to wait for the command line to have loaded at least a bit before you continue to type, but once the input box has appeared you can type as quickly as you like.
    
    With this fix, I'm personally much happier using Tridactyl than I was. For me, it is a big step towards being a reliable tool I enjoy using and away from being a janky thing that I simply put up with.
    
    \### Other stuff
    
    Help and tutor pages now follow your theme. \`:editor\` is quicker on Windows (even without the new native messenger) as we no longer check for Linux terminals which are vanishingly unlikely to exist. And that's pretty much it ... I think we must have added and then fixed lots of bugs in the beta which aren't really worth mentioning in these newsletters.
    
    \## Plans for next few months
    
    I'll keep making the tips & tricks newsletters and maybe try to advertise them a little more. We currently have 12 donors across all platforms that will receive them. In monetary terms that is getting towards the "worth it" line, I think. We'll see whether it becomes too exhausting writing them each month, especially if I start tidying them up for the wiki too.
    
    I'm still toying with the idea of looking seriously into a paid-for Chrome port, but I think I've found more things that I want to fix in Tridactyl first. I'm going to take another look at rewriting the completions code - updating the all-window-tab completions because they missed something that the one-window-tab completions had was unpleasant because there was so much duplicated code.
    
    Finally, I expect I'll spend much of the next quarter fixing bugs I didn't spot in the new native messenger : )
    
    As always, thanks for your generous support,
    
    bovine3dom and the rest of the Tridactyl developers
    
-   Hi!
    
    Welcome to the first Tridactyl Tips & Tricks newsletter, as mentioned in the previous Tridactyl newsletter. This newsletter is very experimental so any feedback you have would be appreciated.
    
    This first edition is going out to all sponsors on GitHub and Patreon. Later editions will only go out to sponsors on tiers \*\*10 USD a month and higher\*\*; I'm trying to raise a bit more revenue since GitHub will no longer double donations. I'll probably make each newsletter public after a couple of months as I don't like restricting knowledge needlessly, but I want there to be some incentive other than warm fuzzy feelings for people to donate money to Tridactyl. My initial plan is to write a chunky guide like this about once a month - planned topics include custom ex-commands with \`:js\` and \`:jsb\`, \`:composite\` and custom themes - and once I run out of big ideas I'll send out shorter emails with more random tips & tricks more often.
    
    In my experience, most people who use Tridactyl know a lot about computers in general, but don't know much about web technologies. These guides therefore will assume very little knowledge about JavaScript or the working of websites. They may assume some rudimentary knowledge of programming terminology. Please do let me know if I'm getting the balance right!
    
    I wasn't sure where to start with the tips so I've gone for one of the features of Tridactyl I use most frequently: custom hint modes that use custom CSS selectors to only show the most relevant hints on your favourite websites; for example, on a search engine you might only want search results to be hinted. Essentially, we'll learn how to create lines like the following ones from my RC file.
    
    \`\`\`
    
    " Only hint search results on Google and DDG
    
    bindurl [google.com](http://www.google.com/) f hint -Jc .rc > div > a
    
    bindurl [google.com](http://www.google.com/) F hint -Jbc .rc > div > a
    
    bindurl ^[https://duckduckgo.com](https://duckduckgo.com/) f hint -Jc \[class=result\_\_a\]
    
    bindurl ^[https://duckduckgo.com](https://duckduckgo.com/) F hint -Jbc \[class=result\_\_a\]
    
    " Comment toggler for Reddit, Hacker News and [Lobste.rs](http://lobste.rs/)
    
    bind ;c hint -Jc \[class\*="expand"\],\[class="togg"\],\[class="comment\_folder"\]
    
    \`\`\`
    
    ![](https://c10.patreonusercontent.com/3/eyJyb3RhdGUiOjAsInciOjgyMH0%3D/patreon-media/p/post/45225463/db7593bc33b34f88982190727400da0c/1.png?token-time=1622419200&token-hash=9fyjlZIWbkD3l3N2Qpw7n9mCSzcYA4oEGDLsy0ouwAA%3D)
    
    We'll cover quite a lot of ground here so bear with me:
    
    1\. What a CSS selector does and why it's useful for hint modes
    
    2\. How to craft a CSS selector that only contains the links you want
    
    3\. Using this CSS selector in various hint modes
    
    4\. Binding these hint modes to keys
    
    5\. Binding these hint modes to keys only on certain websites
    
    If you already know how to do any of those steps you can just skip the corresponding section.
    
    Without further ado:
    
    **1: Introduction to CSS selectors and why they're useful for hint modes**
    
    CSS - "cascading style sheets" - control how a web page is displayed. Here is a simple CSS snippet:
    
    \`\`\`css
    
    p {
    
        color: pink;
    
    }
    
    \`\`\`
    
    This file would make all the paragraphs (the \`<p>\` tags) on the page pink.
    
    Why do we care about this? The bit before the curly bracket - \`p\` - is a CSS selector. It tells the browser which parts of the page to apply the following styles to. Tridactyl can use this same technology to pick which elements of a page to hint with the syntax \`:hint -c \[CSS selector\]\`. For reasons of backwards compatibility, this also includes hints for any elements for which the page is listening for mouse click events with JavaScript; you can turn this off with the \`J\` flag so in practice you will usually see this invoked as \`:hint -Jc \[CSS selector\]\`. Selectors can be combined with some but not all hint modes - we will cover them in section 3.
    
    MDN has an excellent tutorial on CSS selectors here: [https://developer.mozilla.org/en-US/docs/Learn/CSS/Building\_blocks/Selectors](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors) . I highly recommend that you take the time to go through it.
    
    **2: How to craft a CSS selector that only contains the elements you want**
    
    In this section we'll make use of the Firefox web console to help us to find an initial CSS selector that selects the elements we want to hint and then improve it.
    
    If you skipped the MDN tutorial above, you can get by in this section by knowing that websites generally denote "types" of element with classes, e.g. \`<p class="advertorial">\` might denote text that has been written by a sponsor. CSS selectors select classes with a leading dot, e.g. \`.advertorial\`. Tags are selected simply with the name of the tag and can be combined with other selectors, e.g. \`p.advertorial\`. The next important thing to know is that you can select direct children of other selectors with the child operator, \`>\`. So, if there were any \`<a>\` tags (i.e. links) within the advertorial, we can select them with \`p.advertorial>a\`. In sum, then, a hint mode for clicking on links within advertorials would be \`:hint -Jc p.advertorial>a\`.
    
    With that out of the way, let's look at how to use the Firefox developer tools to craft the best CSS selector for your elements. For this example, I'll pretend that I want to hint the main articles on the \[English Wikipedia homepage\]([https://en.wikipedia.org/wiki/Main\_Page).](https://en.wikipedia.org/wiki/Main_Page).) Right click on one of the elements you want to hint and click "Inspect Element". A panel should appear; you want to look at the HTML panel and see if there is any discernible pattern to the tags surrounding the element you are interested in. Right click another element you want to hint and check that it is the same. For example, for me, the HTML looks a bit like this:
    
    \`\`\`
    
    <p>
    
        <b>
    
            <a href="/wiki/James\_Humphreys\_(pornographer)" title="James Humphreys (pornographer)">James Humphreys</a>
    
        </b>
    
    ...
    
    <li>
    
    ::marker
    
        <b>
    
            <a href="/wiki/Hurricane\_Iota" title="Hurricane Iota">Hurricane Iota</a>
    
        </b>
    
    ...
    
    \`\`\`
    
    ![](https://c10.patreonusercontent.com/3/eyJyb3RhdGUiOjAsInciOjgyMH0%3D/patreon-media/p/post/45225463/afb1b7a6bac943469e4a150c513ab1ff/1.png?token-time=1622419200&token-hash=PvDCRCY0_4mIS-E9g-OqKouJFBCD0kz3ViTj9b_Kdak%3D)
    
    It looks like the links I want to hint are always directly enclosed by a \`<b>\` (bold) tag. The CSS selector we want is therefore \`b>a\`, that is links (\`a\` tags) which are immediate children of bold tags. We can check that this works in Tridactyl by giving focus to the webpage again, and typing \`:hint -c b>a\` - and, if it works, we're done!
    
    ![](https://c10.patreonusercontent.com/3/eyJyb3RhdGUiOjAsInciOjgyMH0%3D/patreon-media/p/post/45225463/95f0e74f957345539ffc5433bb5abe27/1.png?token-time=1622419200&token-hash=f5QFQQoZGvm3oNNiq5A7mUn--E4RY09njEITZ6DRfYo%3D)
    
    However, what if it didn't work? What if there were too many links hinted or not enough? I have found that the best way to proceed is to go to the Firefox console. On the panel that displays the HTML, click the "console" tab. In this tab, type
    
    \`\`\`
    
    document.querySelectorAll("\[your selector here\]")
    
    \`\`\`
    
    and press enter. So, for me, \`document.querySelectorAll("b>a")\`. You should see that a \`NodeList\` has been returned. If you click the little arrow/triangle next to this, it will expand and you can see all the elements that your selector matches (including ones not visible in the viewport).
    
    If your selector has not matched the elements you want - and you can see which is which easily by hovering over them with the mouse and they will be highlighted in the viewport - you need to return to the previous step and make your CSS selector less restrictive. For example, we might change our selector from \`b>a\` to \`a\` - removing the restriction that \`a\` tags have to be inside \`b\` tags and instead selecting all \`a\` tags.
    
    If instead your selector has matched too many elements, we need to tighten our CSS selector. If you can see a pattern that the elements you want follow but the elements that you don't want do not, use it. Let's say that on the Wikipedia page I don't want to hint any of the important links that go to external pages.
    
    My NodeList looks like this:
    
    \`\`\`
    
    NodeList(57)
    
    0: <a class="" href="/wiki/James\_Humphreys\_(pornographer)" title="James Humphreys (pornographer)">
    
    1: <a class="" href="/wiki/James\_Humphreys\_(pornographer)" title="James Humphreys (pornographer)">
    
    ...
    
    55: https://en.wikivoyage.org/">
    
    56: https://en.wiktionary.org/">
    
    \`\`\`
    
    ![](https://c10.patreonusercontent.com/3/eyJyb3RhdGUiOjAsInciOjgyMH0%3D/patreon-media/p/post/45225463/f3fece163fdd4e439cef22cffd770776/1.png?token-time=1622419200&token-hash=zR0dtw7uBzSxOKdBoEaV9KOsdORtVUAh7RgKowiW3JQ%3D)
    
    where the first two links are ones I want and the last four are ones I want to exclude.
    
    There are two patterns that I can spot: the links we want always have their hrefs start with \`/wiki/\`, and the links we don't want have \`class="external text"\`.
    
    At this point it's helpful to have a working knowledge of the more advanced CSS selectors. Particularly, we will use \[attribute selectors\]([https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute\_selectors).](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors).)
    
    Since there are two patterns which completely specify the items we want and don't want, there are two possible CSS selectors. The first is relatively straightforward: \`b>a\[href^='/wiki/'\]\`, meaning any \`a\` tags whose hrefs start with "/wiki/" and are the immediate children of \`b\` tags. The second is a little more complex as it requires a negation: \`b>a:not(\[class^="external"\])\` - it matches all \`a\` tags whose classes don't start with "external" and are immediate children of \`b\` tags. We can verify that these work again with \`:hint -c \[CSS selector\]\` in Tridactyl or \`document.querySelectorAll("\[CSS selector\]")\` in the Firefox console.
    
    For the special case where there is a single link that you would like to hint, you can use Tridactyl to create a unique selector automatically. Simply run \`hint -F e => tri.excmds.fillcmdline("hint -Jc " + tri.dom.getSelector(e))\` and Tridactyl will return a hint command for you to run or edit.
    
    Finally, we will cover what to do if there appears to be no difference between the elements you want and the elements don't want in your \`NodeList\`: you need to look at the tags surrounding the elements. To do that, you can click on the "crosshair" like icon to the right of each element. This will take you back to the HTML representation of the page with your element selected. You then need to repeat the step we did initially, looking to see if you can spot any patterns. You can click the "console" tab to get back to the \`NodeList\` and look at other elements. If you're still stuck after all this, feel free to ask us on Matrix; there's usually a way to do it.
    
     **3. Using CSS selectors in more hint modes**
    
    There are a couple of gotchas to using anything other than the standard \`:hint -c\` hint mode. It can currently only be used on the default, foreground tab (\`-t\`), background tab (\`-b\`) and custom callback (\`-F\`) hintmodes.
    
    The main caveat is that you can't put any spaces in the CSS selector if your mode also takes other arguments. E.g. \`:hint -Fc b > a console.log\` will not work: you need \`:hint -Fc b>a console.log\`. This means that CSS selectors that require spaces can't be used with these hint modes unless you start the hint mode via \`:js\` (which will be covered in a later newsletter ; )). If the mode takes other arguments, the selector always comes first.
    
    **4\. Binding the hint mode to keys**
    
    I imagine most people reading this newsletter will already know how to bind to keys. I include it here for completeness.
    
    \`:bind \[key sequence\] hint -c \[CSS selector\]\`, so for our Wikipedia example, we might choose \`:bind ,f hint -c b>a\`. See \`:help bind\` in Tridactyl for more information on key sequences.
    
    **5\. Binding hint modes to keys only on certain websites**
    
    Custom hint modes like the ones we have covered here are usually specific to a single website. It therefore often makes sense to only bind the modes to keys when you are on these websites. Tridactyl has a \`:bindurl\` command for situations exactly like these.
    
    The full syntax is \`:bindurl \[URL regex\] \[key sequence\] \[ex-command\]\`. If you are unfamiliar with JavaScript regex, you may find \[this MDN page\]([https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular\_Expressions)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions)) useful. Note that \`:bindurl\` converts the regex string to a regex, i.e. you should not surround your regex with slashes, so \`\\.xml$\` rather than \`/\\.xml$/\`. However, most of the time you don't really need to worry about bindurl using a regex. \`:bindurl [google.com](http://www.google.com/) ,c tabclose\` will match "[google.com](http://www.google.com/)" fine, but it will also match any URL that contains "[google.com](http://www.google.com/)" and the dots \`.\` can actually match any letter, e.g. "wwwagooglezcom" would also match. In the real world this doesn't matter much, but if you are concerned about it you can use \`^http(s)?://www\\.google\\.com\` which will only match literal dots and only URLs that start with \`[google.com](http://google.com/)\`.
    
    So, for our Wikipedia example, we might use
    
    \`\`\`
    
    bindurl http(s)?://en\\.wikipedia\\.org/wiki/Main\_Page ,f hint -c b>a\`
    
    bindurl http(s)?://en\\.wikipedia\\.org/wiki/Main\_Page ,F hint -bc b>a\`
    
    \`\`\`
    
    where we have bound the new modes to \`,f\` and \`,F\`. If we wanted to "replace" the normal hint modes on these pages, we would just bind to \`f\` and \`F\` instead.
    
    **Conclusion**
    
    I hope you have enjoyed this first tips & tricks newsletter. Please do send me feedback - whether it's via Matrix, GitHub issues or email - so I can get an idea on how useful this was. Was it too long? Was the topic interesting? Was it too easy, or too hard? How frequently do you think they should be sent?
    
    Cheers, bovine3dom
    
    Hi!
    
    Welcome to the first Tridactyl Tips & Tricks newsletter, as mentioned in the previous Tridactyl newsletter. This newsletter is very experimental so any feedback you have would be appreciated.
    
    This first edition is going out to all sponsors on GitHub and Patreon. Later editions will only go out to sponsors on tiers \*\*10 USD a month and higher\*\*; I'm trying to raise a bit more revenue since GitHub will no longer double donations. I'll probably make each newsletter public after a couple of months as I don't like restricting knowledge needlessly, but I want there to be some incentive other than warm fuzzy feelings for people to donate money to Tridactyl. My initial plan is to write a chunky guide like this about once a month - planned topics include custom ex-commands with \`:js\` and \`:jsb\`, \`:composite\` and custom themes - and once I run out of big ideas I'll send out shorter emails with more random tips & tricks more often.
    
    In my experience, most people who use Tridactyl know a lot about computers in general, but don't know much about web technologies. These guides therefore will assume very little knowledge about JavaScript or the working of websites. They may assume some rudimentary knowledge of programming terminology. Please do let me know if I'm getting the balance right!
    
    I wasn't sure where to start with the tips so I've gone for one of the features of Tridactyl I use most frequently: custom hint modes that use custom CSS selectors to only show the most relevant hints on your favourite websites; for example, on a search engine you might only want search results to be hinted. Essentially, we'll learn how to create lines like the following ones from my RC file.
    
    \`\`\`
    
    " Only hint search results on Google and DDG
    
    bindurl [google.com](http://www.google.com/) f hint -Jc .rc > div > a
    
    bindurl [google.com](http://www.google.com/) F hint -Jbc .rc > div > a
    
    bindurl ^[https://duckduckgo.com](https://duckduckgo.com/) f hint -Jc \[class=result\_\_a\]
    
    bindurl ^[https://duckduckgo.com](https://duckduckgo.com/) F hint -Jbc \[class=result\_\_a\]
    
    " Comment toggler for Reddit, Hacker News and [Lobste.rs](http://lobste.rs/)
    
    bind ;c hint -Jc \[class\*="expand"\],\[class="togg"\],\[class="comment\_folder"\]
    
    \`\`\`
    
    ![](https://c10.patreonusercontent.com/3/eyJyb3RhdGUiOjAsInciOjgyMH0%3D/patreon-media/p/post/45225463/db7593bc33b34f88982190727400da0c/1.png?token-time=1622419200&token-hash=9fyjlZIWbkD3l3N2Qpw7n9mCSzcYA4oEGDLsy0ouwAA%3D)
    
    We'll cover quite a lot of ground here so bear with me:
    
    1\. What a CSS selector does and why it's useful for hint modes
    
    2\. How to craft a CSS selector that only contains the links you want
    
    3\. Using this CSS selector in various hint modes
    
    4\. Binding these hint modes to keys
    
    5\. Binding these hint modes to keys only on certain websites
    
    If you already know how to do any of those steps you can just skip the corresponding section.
    
    Without further ado:
    
    **1: Introduction to CSS selectors and why they're useful for hint modes**
    
    CSS - "cascading style sheets" - control how a web page is displayed. Here is a simple CSS snippet:
    
    \`\`\`css
    
    p {
    
        color: pink;
    
    }
    
    \`\`\`
    
    This file would make all the paragraphs (the \`<p>\` tags) on the page pink.
    
    Why do we care about this? The bit before the curly bracket - \`p\` - is a CSS selector. It tells the browser which parts of the page to apply the following styles to. Tridactyl can use this same technology to pick which elements of a page to hint with the syntax \`:hint -c \[CSS selector\]\`. For reasons of backwards compatibility, this also includes hints for any elements for which the page is listening for mouse click events with JavaScript; you can turn this off with the \`J\` flag so in practice you will usually see this invoked as \`:hint -Jc \[CSS selector\]\`. Selectors can be combined with some but not all hint modes - we will cover them in section 3.
    
    MDN has an excellent tutorial on CSS selectors here: [https://developer.mozilla.org/en-US/docs/Learn/CSS/Building\_blocks/Selectors](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors) . I highly recommend that you take the time to go through it.
    
    **2: How to craft a CSS selector that only contains the elements you want**
    
    In this section we'll make use of the Firefox web console to help us to find an initial CSS selector that selects the elements we want to hint and then improve it.
    
    If you skipped the MDN tutorial above, you can get by in this section by knowing that websites generally denote "types" of element with classes, e.g. \`<p class="advertorial">\` might denote text that has been written by a sponsor. CSS selectors select classes with a leading dot, e.g. \`.advertorial\`. Tags are selected simply with the name of the tag and can be combined with other selectors, e.g. \`p.advertorial\`. The next important thing to know is that you can select direct children of other selectors with the child operator, \`>\`. So, if there were any \`<a>\` tags (i.e. links) within the advertorial, we can select them with \`p.advertorial>a\`. In sum, then, a hint mode for clicking on links within advertorials would be \`:hint -Jc p.advertorial>a\`.
    
    With that out of the way, let's look at how to use the Firefox developer tools to craft the best CSS selector for your elements. For this example, I'll pretend that I want to hint the main articles on the \[English Wikipedia homepage\]([https://en.wikipedia.org/wiki/Main\_Page).](https://en.wikipedia.org/wiki/Main_Page).) Right click on one of the elements you want to hint and click "Inspect Element". A panel should appear; you want to look at the HTML panel and see if there is any discernible pattern to the tags surrounding the element you are interested in. Right click another element you want to hint and check that it is the same. For example, for me, the HTML looks a bit like this:
    
    \`\`\`
    
    <p>
    
        <b>
    
            <a href="/wiki/James\_Humphreys\_(pornographer)" title="James Humphreys (pornographer)">James Humphreys</a>
    
        </b>
    
    ...
    
    <li>
    
    ::marker
    
        <b>
    
            <a href="/wiki/Hurricane\_Iota" title="Hurricane Iota">Hurricane Iota</a>
    
        </b>
    
    ...
    
    \`\`\`
    
    ![](https://c10.patreonusercontent.com/3/eyJyb3RhdGUiOjAsInciOjgyMH0%3D/patreon-media/p/post/45225463/afb1b7a6bac943469e4a150c513ab1ff/1.png?token-time=1622419200&token-hash=PvDCRCY0_4mIS-E9g-OqKouJFBCD0kz3ViTj9b_Kdak%3D)
    
    It looks like the links I want to hint are always directly enclosed by a \`<b>\` (bold) tag. The CSS selector we want is therefore \`b>a\`, that is links (\`a\` tags) which are immediate children of bold tags. We can check that this works in Tridactyl by giving focus to the webpage again, and typing \`:hint -c b>a\` - and, if it works, we're done!
    
    ![](https://c10.patreonusercontent.com/3/eyJyb3RhdGUiOjAsInciOjgyMH0%3D/patreon-media/p/post/45225463/95f0e74f957345539ffc5433bb5abe27/1.png?token-time=1622419200&token-hash=f5QFQQoZGvm3oNNiq5A7mUn--E4RY09njEITZ6DRfYo%3D)
    
    However, what if it didn't work? What if there were too many links hinted or not enough? I have found that the best way to proceed is to go to the Firefox console. On the panel that displays the HTML, click the "console" tab. In this tab, type
    
    \`\`\`
    
    document.querySelectorAll("\[your selector here\]")
    
    \`\`\`
    
    and press enter. So, for me, \`document.querySelectorAll("b>a")\`. You should see that a \`NodeList\` has been returned. If you click the little arrow/triangle next to this, it will expand and you can see all the elements that your selector matches (including ones not visible in the viewport).
    
    If your selector has not matched the elements you want - and you can see which is which easily by hovering over them with the mouse and they will be highlighted in the viewport - you need to return to the previous step and make your CSS selector less restrictive. For example, we might change our selector from \`b>a\` to \`a\` - removing the restriction that \`a\` tags have to be inside \`b\` tags and instead selecting all \`a\` tags.
    
    If instead your selector has matched too many elements, we need to tighten our CSS selector. If you can see a pattern that the elements you want follow but the elements that you don't want do not, use it. Let's say that on the Wikipedia page I don't want to hint any of the important links that go to external pages.
    
    My NodeList looks like this:
    
    \`\`\`
    
    NodeList(57)
    
    0: <a class="" href="/wiki/James\_Humphreys\_(pornographer)" title="James Humphreys (pornographer)">
    
    1: <a class="" href="/wiki/James\_Humphreys\_(pornographer)" title="James Humphreys (pornographer)">
    
    ...
    
    55: https://en.wikivoyage.org/">
    
    56: https://en.wiktionary.org/">
    
    \`\`\`
    
    ![](https://c10.patreonusercontent.com/3/eyJyb3RhdGUiOjAsInciOjgyMH0%3D/patreon-media/p/post/45225463/f3fece163fdd4e439cef22cffd770776/1.png?token-time=1622419200&token-hash=zR0dtw7uBzSxOKdBoEaV9KOsdORtVUAh7RgKowiW3JQ%3D)
    
    where the first two links are ones I want and the last four are ones I want to exclude.
    
    There are two patterns that I can spot: the links we want always have their hrefs start with \`/wiki/\`, and the links we don't want have \`class="external text"\`.
    
    At this point it's helpful to have a working knowledge of the more advanced CSS selectors. Particularly, we will use \[attribute selectors\]([https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute\_selectors).](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors).)
    
    Since there are two patterns which completely specify the items we want and don't want, there are two possible CSS selectors. The first is relatively straightforward: \`b>a\[href^='/wiki/'\]\`, meaning any \`a\` tags whose hrefs start with "/wiki/" and are the immediate children of \`b\` tags. The second is a little more complex as it requires a negation: \`b>a:not(\[class^="external"\])\` - it matches all \`a\` tags whose classes don't start with "external" and are immediate children of \`b\` tags. We can verify that these work again with \`:hint -c \[CSS selector\]\` in Tridactyl or \`document.querySelectorAll("\[CSS selector\]")\` in the Firefox console.
    
    For the special case where there is a single link that you would like to hint, you can use Tridactyl to create a unique selector automatically. Simply run \`hint -F e => tri.excmds.fillcmdline("hint -Jc " + tri.dom.getSelector(e))\` and Tridactyl will return a hint command for you to run or edit.
    
    Finally, we will cover what to do if there appears to be no difference between the elements you want and the elements don't want in your \`NodeList\`: you need to look at the tags surrounding the elements. To do that, you can click on the "crosshair" like icon to the right of each element. This will take you back to the HTML representation of the page with your element selected. You then need to repeat the step we did initially, looking to see if you can spot any patterns. You can click the "console" tab to get back to the \`NodeList\` and look at other elements. If you're still stuck after all this, feel free to ask us on Matrix; there's usually a way to do it.
    
     **3. Using CSS selectors in more hint modes**
    
    There are a couple of gotchas to using anything other than the standard \`:hint -c\` hint mode. It can currently only be used on the default, foreground tab (\`-t\`), background tab (\`-b\`) and custom callback (\`-F\`) hintmodes.
    
    The main caveat is that you can't put any spaces in the CSS selector if your mode also takes other arguments. E.g. \`:hint -Fc b > a console.log\` will not work: you need \`:hint -Fc b>a console.log\`. This means that CSS selectors that require spaces can't be used with these hint modes unless you start the hint mode via \`:js\` (which will be covered in a later newsletter ; )). If the mode takes other arguments, the selector always comes first.
    
    **4\. Binding the hint mode to keys**
    
    I imagine most people reading this newsletter will already know how to bind to keys. I include it here for completeness.
    
    \`:bind \[key sequence\] hint -c \[CSS selector\]\`, so for our Wikipedia example, we might choose \`:bind ,f hint -c b>a\`. See \`:help bind\` in Tridactyl for more information on key sequences.
    
    **5\. Binding hint modes to keys only on certain websites**
    
    Custom hint modes like the ones we have covered here are usually specific to a single website. It therefore often makes sense to only bind the modes to keys when you are on these websites. Tridactyl has a \`:bindurl\` command for situations exactly like these.
    
    The full syntax is \`:bindurl \[URL regex\] \[key sequence\] \[ex-command\]\`. If you are unfamiliar with JavaScript regex, you may find \[this MDN page\]([https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular\_Expressions)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions)) useful. Note that \`:bindurl\` converts the regex string to a regex, i.e. you should not surround your regex with slashes, so \`\\.xml$\` rather than \`/\\.xml$/\`. However, most of the time you don't really need to worry about bindurl using a regex. \`:bindurl [google.com](http://www.google.com/) ,c tabclose\` will match "[google.com](http://www.google.com/)" fine, but it will also match any URL that contains "[google.com](http://www.google.com/)" and the dots \`.\` can actually match any letter, e.g. "wwwagooglezcom" would also match. In the real world this doesn't matter much, but if you are concerned about it you can use \`^http(s)?://www\\.google\\.com\` which will only match literal dots and only URLs that start with \`[google.com](http://google.com/)\`.
    
    So, for our Wikipedia example, we might use
    
    \`\`\`
    
    bindurl http(s)?://en\\.wikipedia\\.org/wiki/Main\_Page ,f hint -c b>a\`
    
    bindurl http(s)?://en\\.wikipedia\\.org/wiki/Main\_Page ,F hint -bc b>a\`
    
    \`\`\`
    
    where we have bound the new modes to \`,f\` and \`,F\`. If we wanted to "replace" the normal hint modes on these pages, we would just bind to \`f\` and \`F\` instead.
    
    **Conclusion**
    
    I hope you have enjoyed this first tips & tricks newsletter. Please do send me feedback - whether it's via Matrix, GitHub issues or email - so I can get an idea on how useful this was. Was it too long? Was the topic interesting? Was it too easy, or too hard? How frequently do you think they should be sent?
    
    Cheers, bovine3dom
    
-   Hello,
    
    Welcome to the fifth quarterly Tridactyl newsletter.
    
    We've had another productive quarter. It hasn't been quite as transformative as the last quarter - the addition of browser-wide \`<C-,>\` and \`<C-6>\` was hard to beat (I've personally switched to using \`<C-,>\` instead of \`<Esc>\` and generally Tridactyl and I get along a lot better :)) - but we have added quite a few nice little things.
    
    **\## Highlighted new features**
    
    **\### For everyone**
    
    A few new features relating to completions have been added: \`<C-o>yy\` copies the currently selected completion to the clipboard, \`<S-Delete>\` executes \`:tabclose\` on a selected completion's arguments and \`<C-Enter>\` executes the highlighted completion keeping the command line open - particularly useful for, e.g. \`tabopen -b\`. The commands relating to those binds are \`ex.execute\_ex\_on\_completion{,\_args} \[ex command\]\`; the "args" variant means that the ex-command that triggered the completion is omitted from the final executed command.
    
    Next, a quality of life improvement for some of our users. The mode indicator can now be hidden in individual modes with \`:set modeindicatormodes.\[mode\] true|false\`. I hope this is useful for e.g. full screen applications and ignore mode; users often were frustrated by the appearance of the mode indicator on YouTube.
    
    My favourite feature of the quarter, from a contributor, is \`:jumble\`, bound to \`g!\` by default, which shuffles the characters in all text on the page while persrvineg the frist and last letetr of each word. Just for fun.
    
    **\### For power users**
    
    I added a callback hintmode with \`:hint -F elem => \[... do some stuff in JS ...\]\`. I don't know why we didn't add it earlier - it was easy to implement and allows you to do a lot of cool stuff. It just goes to show that Tridactyl still has some low-hanging fruit!
    
    autocommands now support \`WebRequest\` events - see \`:help autocmd\` for more details. It's especially useful for redirecting sites, like old reddit to new reddit, but comes with lots of caveats - rather than an ex-command, it runs a JavaScript snippet which must return an object with a specific format. There's no substitute for reading the help page on this one, I'm afraid.
    
    \`:js\` now accepts a flag, \`-d\`, to specify an EOF character which allows space-separated arguments to be given to it, stored in the array \`JS\_ARGS\`, meaning that people really can write their own ex-commands - the only thing left, really, is custom completions : ).
    
    \`:autocmd\` now provides magic variables for lots of events - see \`:help autocmd\` to see them all. It's useful for ensuring that an ex-command affects the right tab even if that tab is opened in the background.
    
    **\## Highlighted bug fixes**
    
    Tridactyl \_finally\_ should display the right version number on the new tab page and everywhere else, which means pretty version numbers for stable users. Beta users keep the current ugly version numbers : ).
    
    In a fairly big change - you probably noticed it because your config disappeared despite my best efforts - we have ditched automatic synchronisation with the Firefox Sync storage. It had always caused problems for a minority of our users, but the introduction of a strict storage quota by Mozilla meant it broke for almost everyone using a custom theme. We now just use the local storage; if you want to keep your settings in sync with another machine, just run \`:firefoxsync{pull,push}\` periodically. Currently, the settings do not merge and will just overwrite when you push/pull - if anyone really wants that feature they should ask me. I suspect most people will manage fine without it. I'm hoping that this change might have made our RC files more reliable, but so far I haven't heard any noises either way.
    
    We also fixed a bug that was particularly frustrating to new users: the little pop-up telling you the address of a link you are hovering over is now hidden when the command line is opened. We do this by putting focus on a fake empty link and then quickly deleting it - a trick we found in VVimpulation, [https://github.com/amedama41/vvimpulation](https://github.com/amedama41/vvimpulation),), a smaller vim-like browser project that actually has quite a few neat little features. Open source is nice sometimes.
    
    As a workaround to make \`<C-,>\` compatible with Tree Style Tab, \`:set escapehatchsidebarhack\` stops us from closing the sidebar. Unfortunately, that means that we can't get focus back from the address bar, so pick your poison.
    
    Finally, a bug that I personally found very distracting has been squashed: \`yy\` should no longer give spurious errors.
    
    **\## Other stuff + the near future**
    
    You might be interested to learn that I did an interview for a little tech newsletter, [https://console.substack.com/p/console-21](https://console.substack.com/p/console-21),), which was fun. Everyone loves talking about themselves.
    
    In the next quarter, GitHub will stop doubling donations via GitHub sponsors. They still won't charge any fees, so it's still a vastly better deal than PayPal or Patreon (if your donation is small, those platforms will eat about ~30% of it by the time it gets to our pockets). This leaves us with a slight conundrum as my state-of-the-art forecasts predict that I would still like to eat broadly the same amount of food even after GitHub stops doubling the donations. I think we have enough users (and certainly the potential to have enough users) that, together, they could afford to keep me fed and maybe even housed \[1\]. I have a few ideas for persuading them to do this:
    
    -   porting to Chrome and charging a fairly high yearly licence fee for it + big updates to it (~tens of pounds); security updates and major bug/compatibility fixes we'd probably offer for free for as long as we could reasonably manage. Firefox would remain free and all our code would continue to be FOSS - people could just build Tridactyl for Chrome themselves if they wanted.
    -   offering a paid-for weekly newsletter with Tridactyl tips and tricks (~a few pounds a month). Not sure how I'd manage the mechanics of it - would people who got this newsletter currently be fed up if one suddenly turned up once a month?
    -   asking slightly more prominently in Tridactyl and explaining why we need donations in a little more detail. I'd probably add a setting to disable this ... I don't want to turn into Wikipedia (but Wikipedia is rolling in cash, so maybe I do?). We'd need the setting for the Chrome port, anyway, so that we weren't nagging people who had already paid.
    
    In terms of features that are coming your way - I think I have finally been frustrated enough by our completion code that I am going to rewrite it to rely more heavily on configuration at runtime; I hope that will allow for more natural code re-use than the "you only have one parent" inheritance we currently use. It would also naturally allow users to write their own completions. I am optimistic that I will be able to merge the key-up binding PR in the next few months too - there's just one minor bug (that I know of) left to squash. The key-up bindings would allow for layers (e.g. hold \\ to make j and k scroll farther) and "videogame style" smooth scrolling where the scrolling happens only while the key is held.
    
    Thanks as ever for your support,
    
    bovine3dom and the rest of the Tridactyl developers
    
    \[1\]: NB - I am not in danger of starving or becoming homeless any time soon. However, there is a real risk that I would seek gainful employment if I was having to draw from my savings every month, which would mean less time spent on Tridactyl.
    
    Hello,
    
    Welcome to the fifth quarterly Tridactyl newsletter.
    
    We've had another productive quarter. It hasn't been quite as transformative as the last quarter - the addition of browser-wide \`<C-,>\` and \`<C-6>\` was hard to beat (I've personally switched to using \`<C-,>\` instead of \`<Esc>\` and generally Tridactyl and I get along a lot better :)) - but we have added quite a few nice little things.
    
    **\## Highlighted new features**
    
    **\### For everyone**
    
    A few new features relating to completions have been added: \`<C-o>yy\` copies the currently selected completion to the clipboard, \`<S-Delete>\` executes \`:tabclose\` on a selected completion's arguments and \`<C-Enter>\` executes the highlighted completion keeping the command line open - particularly useful for, e.g. \`tabopen -b\`. The commands relating to those binds are \`ex.execute\_ex\_on\_completion{,\_args} \[ex command\]\`; the "args" variant means that the ex-command that triggered the completion is omitted from the final executed command.
    
    Next, a quality of life improvement for some of our users. The mode indicator can now be hidden in individual modes with \`:set modeindicatormodes.\[mode\] true|false\`. I hope this is useful for e.g. full screen applications and ignore mode; users often were frustrated by the appearance of the mode indicator on YouTube.
    
    My favourite feature of the quarter, from a contributor, is \`:jumble\`, bound to \`g!\` by default, which shuffles the characters in all text on the page while persrvineg the frist and last letetr of each word. Just for fun.
    
    **\### For power users**
    
    I added a callback hintmode with \`:hint -F elem => \[... do some stuff in JS ...\]\`. I don't know why we didn't add it earlier - it was easy to implement and allows you to do a lot of cool stuff. It just goes to show that Tridactyl still has some low-hanging fruit!
    
    autocommands now support \`WebRequest\` events - see \`:help autocmd\` for more details. It's especially useful for redirecting sites, like old reddit to new reddit, but comes with lots of caveats - rather than an ex-command, it runs a JavaScript snippet which must return an object with a specific format. There's no substitute for reading the help page on this one, I'm afraid.
    
    \`:js\` now accepts a flag, \`-d\`, to specify an EOF character which allows space-separated arguments to be given to it, stored in the array \`JS\_ARGS\`, meaning that people really can write their own ex-commands - the only thing left, really, is custom completions : ).
    
    \`:autocmd\` now provides magic variables for lots of events - see \`:help autocmd\` to see them all. It's useful for ensuring that an ex-command affects the right tab even if that tab is opened in the background.
    
    **\## Highlighted bug fixes**
    
    Tridactyl \_finally\_ should display the right version number on the new tab page and everywhere else, which means pretty version numbers for stable users. Beta users keep the current ugly version numbers : ).
    
    In a fairly big change - you probably noticed it because your config disappeared despite my best efforts - we have ditched automatic synchronisation with the Firefox Sync storage. It had always caused problems for a minority of our users, but the introduction of a strict storage quota by Mozilla meant it broke for almost everyone using a custom theme. We now just use the local storage; if you want to keep your settings in sync with another machine, just run \`:firefoxsync{pull,push}\` periodically. Currently, the settings do not merge and will just overwrite when you push/pull - if anyone really wants that feature they should ask me. I suspect most people will manage fine without it. I'm hoping that this change might have made our RC files more reliable, but so far I haven't heard any noises either way.
    
    We also fixed a bug that was particularly frustrating to new users: the little pop-up telling you the address of a link you are hovering over is now hidden when the command line is opened. We do this by putting focus on a fake empty link and then quickly deleting it - a trick we found in VVimpulation, [https://github.com/amedama41/vvimpulation](https://github.com/amedama41/vvimpulation),), a smaller vim-like browser project that actually has quite a few neat little features. Open source is nice sometimes.
    
    As a workaround to make \`<C-,>\` compatible with Tree Style Tab, \`:set escapehatchsidebarhack\` stops us from closing the sidebar. Unfortunately, that means that we can't get focus back from the address bar, so pick your poison.
    
    Finally, a bug that I personally found very distracting has been squashed: \`yy\` should no longer give spurious errors.
    
    **\## Other stuff + the near future**
    
    You might be interested to learn that I did an interview for a little tech newsletter, [https://console.substack.com/p/console-21](https://console.substack.com/p/console-21),), which was fun. Everyone loves talking about themselves.
    
    In the next quarter, GitHub will stop doubling donations via GitHub sponsors. They still won't charge any fees, so it's still a vastly better deal than PayPal or Patreon (if your donation is small, those platforms will eat about ~30% of it by the time it gets to our pockets). This leaves us with a slight conundrum as my state-of-the-art forecasts predict that I would still like to eat broadly the same amount of food even after GitHub stops doubling the donations. I think we have enough users (and certainly the potential to have enough users) that, together, they could afford to keep me fed and maybe even housed \[1\]. I have a few ideas for persuading them to do this:
    
    -   porting to Chrome and charging a fairly high yearly licence fee for it + big updates to it (~tens of pounds); security updates and major bug/compatibility fixes we'd probably offer for free for as long as we could reasonably manage. Firefox would remain free and all our code would continue to be FOSS - people could just build Tridactyl for Chrome themselves if they wanted.
    -   offering a paid-for weekly newsletter with Tridactyl tips and tricks (~a few pounds a month). Not sure how I'd manage the mechanics of it - would people who got this newsletter currently be fed up if one suddenly turned up once a month?
    -   asking slightly more prominently in Tridactyl and explaining why we need donations in a little more detail. I'd probably add a setting to disable this ... I don't want to turn into Wikipedia (but Wikipedia is rolling in cash, so maybe I do?). We'd need the setting for the Chrome port, anyway, so that we weren't nagging people who had already paid.
    
    In terms of features that are coming your way - I think I have finally been frustrated enough by our completion code that I am going to rewrite it to rely more heavily on configuration at runtime; I hope that will allow for more natural code re-use than the "you only have one parent" inheritance we currently use. It would also naturally allow users to write their own completions. I am optimistic that I will be able to merge the key-up binding PR in the next few months too - there's just one minor bug (that I know of) left to squash. The key-up bindings would allow for layers (e.g. hold \\ to make j and k scroll farther) and "videogame style" smooth scrolling where the scrolling happens only while the key is held.
    
    Thanks as ever for your support,
    
    bovine3dom and the rest of the Tridactyl developers
    
    \[1\]: NB - I am not in danger of starving or becoming homeless any time soon. However, there is a real risk that I would seek gainful employment if I was having to draw from my savings every month, which would mean less time spent on Tridactyl.
    
-   Hello,
    
    Welcome to the fourth quarterly Tridactyl newsletter.
    
    We've got a lot done in the past few months, including some features which people have been asking for for a long time. My personal highlights are:
    
    \-   "passthrough" mode, bound to \`<C-v>\` in normal mode and \`<C-o>\` in ignore mode sends the next keypress or valid keysequence to ignore or normal mode respectively.
    
    \-   focus-element hint mode, bound to \`;;\`, can now be used to choose which part of the page to scroll - just focus an element contained within that part of the page.
    
    \-   we now support browser-wide binds (with lots of restrictions and caveats) with \`bind --mode=browser\` that can be pressed anywhere in the browser and in all modes.
    
       -   we have two browser-wide binds by default: \`<C-,>\` which is bound to \`:escapehatch\` as an all-purpose "get me back to Tridactyl" button, which works on privileged pages, Flash-style video players, the address bar and just about anything else you throw at it; and \`<C-6>\` which is bound to \`:tab #\` (i.e. switch to previously-used tab), as it used to be in most modes, but it now works everywhere, including PDF pages which I used to get trapped on a couple of times a day.
    
    \-   hints corresponding to elements with JavaScript events are now a different colour - grey - to normal hints. If an element has both, the normal one is almost always the right one. Alongside this, hint tags can no longer overlap.
    
    \-   our end-to-end tests are now very reliable - we haven't had a spurious failure in days where previously about 3/5 attempts would fail without good reason.
    
    As for bug fixes, my highlights are:
    
    \-   \`:tabopen\` no longer focuses the address bar,
    
    \-   the command line history and \`:repeat\` work fantastically reliably now, to the point where I actually use them,
    
    \-   the locks library was causing Tridactyl to use a lot of energy; we've now binned it entirely, and
    
    \-   our internal configuration updater can no longer spin forever if something goes wrong (it just gives up instead).
    
    I think it is fair to say that a big part of the reason why we have made so much progress this quarter is that I've started to work on Tridactyl for the equivalent of a day or two a week. (This is not to rubbish the contributions of other contributors - I think about half of my six highlighted features at least had large parts of them written by other contributors). I'm not sure how long I can keep this up, partly for financial reasons, and partly because I like maths and there fundamentally isn't very much maths in Tridactyl, but it has been quite rewarding in the last few months - it has been nice to see Tridactyl get better at things that had annoyed me on a daily basis.
    
    All of the progress above is currently in the Tridactyl Betas. I will do a stable release soon once I'm more sure that there aren't any show stopping bugs such as \[#2636\]([https://github.com/tridactyl/tridactyl/issues/2636).](https://github.com/tridactyl/tridactyl/issues/2636).)
    
    Looking to the future, we've made a bit of progress behind the scenes on moving Tridactyl towards a place where supporting other browsers wouldn't be too much extra effort. The idea is that we would get warnings at lint-time when we do things that aren't compatible with all the browsers we support. Initially, we would just try to officially support Firefox ESR and Firefox stable at the same time. In the future we may port Tridactyl to Chrome and the other Chromium-based browsers. We can't promise that we'll release it on the relevant stores as we might not pass review - Google is particularly famous for being mercurial.
    
    Thanks for your support,
    
    bovine3dom and the rest of the Tridactyl developers
    
    Hello,
    
    Welcome to the fourth quarterly Tridactyl newsletter.
    
    We've got a lot done in the past few months, including some features which people have been asking for for a long time. My personal highlights are:
    
    \-   "passthrough" mode, bound to \`<C-v>\` in normal mode and \`<C-o>\` in ignore mode sends the next keypress or valid keysequence to ignore or normal mode respectively.
    
    \-   focus-element hint mode, bound to \`;;\`, can now be used to choose which part of the page to scroll - just focus an element contained within that part of the page.
    
    \-   we now support browser-wide binds (with lots of restrictions and caveats) with \`bind --mode=browser\` that can be pressed anywhere in the browser and in all modes.
    
       -   we have two browser-wide binds by default: \`<C-,>\` which is bound to \`:escapehatch\` as an all-purpose "get me back to Tridactyl" button, which works on privileged pages, Flash-style video players, the address bar and just about anything else you throw at it; and \`<C-6>\` which is bound to \`:tab #\` (i.e. switch to previously-used tab), as it used to be in most modes, but it now works everywhere, including PDF pages which I used to get trapped on a couple of times a day.
    
    \-   hints corresponding to elements with JavaScript events are now a different colour - grey - to normal hints. If an element has both, the normal one is almost always the right one. Alongside this, hint tags can no longer overlap.
    
    \-   our end-to-end tests are now very reliable - we haven't had a spurious failure in days where previously about 3/5 attempts would fail without good reason.
    
    As for bug fixes, my highlights are:
    
    \-   \`:tabopen\` no longer focuses the address bar,
    
    \-   the command line history and \`:repeat\` work fantastically reliably now, to the point where I actually use them,
    
    \-   the locks library was causing Tridactyl to use a lot of energy; we've now binned it entirely, and
    
    \-   our internal configuration updater can no longer spin forever if something goes wrong (it just gives up instead).
    
    I think it is fair to say that a big part of the reason why we have made so much progress this quarter is that I've started to work on Tridactyl for the equivalent of a day or two a week. (This is not to rubbish the contributions of other contributors - I think about half of my six highlighted features at least had large parts of them written by other contributors). I'm not sure how long I can keep this up, partly for financial reasons, and partly because I like maths and there fundamentally isn't very much maths in Tridactyl, but it has been quite rewarding in the last few months - it has been nice to see Tridactyl get better at things that had annoyed me on a daily basis.
    
    All of the progress above is currently in the Tridactyl Betas. I will do a stable release soon once I'm more sure that there aren't any show stopping bugs such as \[#2636\]([https://github.com/tridactyl/tridactyl/issues/2636).](https://github.com/tridactyl/tridactyl/issues/2636).)
    
    Looking to the future, we've made a bit of progress behind the scenes on moving Tridactyl towards a place where supporting other browsers wouldn't be too much extra effort. The idea is that we would get warnings at lint-time when we do things that aren't compatible with all the browsers we support. Initially, we would just try to officially support Firefox ESR and Firefox stable at the same time. In the future we may port Tridactyl to Chrome and the other Chromium-based browsers. We can't promise that we'll release it on the relevant stores as we might not pass review - Google is particularly famous for being mercurial.
    
    Thanks for your support,
    
    bovine3dom and the rest of the Tridactyl developers
    
-   Hello,
    
    Welcome to the third quarterly Tridactyl newsletter.
    
    It has been an eventful quarter. We received our first payout from GitHub sponsors (it was real, they really did double your donations!). Visual mode has landed in Tridactyl stable. We weren't accepted on to Google Summer of Code. I finally got round to adding a \`setnull\` command which lets you remove default settings, e.g. \`setnull [searchurls.google](http://searchurls.google/)\` allows you to \`open google\` and search for "google" with your default search engine.
    
    I (bovine3dom) have now hit the cap for doubling for GitHub sponsors as I managed to get paid for some commercial open source work through it. If you would still like your donation to be doubled you can sponsor Tridactyl through glacambre's page - [https://github.com/sponsors/glacambre](https://github.com/sponsors/glacambre)) - we'll still put your money into a central Tridactyl pot. No pressure if you don't want to do that :).
    
    In terms of Tridactyl bugs, I tried really hard to fix the "Tridactyl sometimes doesn't execute all the lines in my RC file" bug, even implementing our own locks library to try to eradicate some race conditions. Instead, it mostly just broke some people's configurations in beta, so we swiftly reverted it. The locks are currently used in Tridactyl beta and stable to try to make command line history more reliable ... which works about 50% of the time; the same seems to apply to \`repeat\`, which is a great improvement on the approximately 5% of the time it used to work. We have a bit of a plan to fix this - see issue #2208 [https://github.com/tridactyl/tridactyl/pull/2208](https://github.com/tridactyl/tridactyl/pull/2208))) - but it would be unwise to promise that it will happen any time soon, given our track record.
    
    On to the main event of the past few months. The novel coronavirus. One of the reasons we ask for donations is to fund retreats for the developers of Tridactyl to meet up and work on Tridactyl together, somewhere a bit nice. This clearly cannot happen again for a while. Personally, I am of the view that it would be immoral to encourage international travel until the virus is beaten or endemic in all of the countries involved. I don't see that happening for at least a year.
    
    The question, then, is what to do with the funds in the meantime. Another aspect of this pandemic is that it may take a while for me (bovine3dom) to find a job and that my savings have taken a hammering. After talking about it with the rest of the Tridactyl developers, at the end of March I started to take the majority of Tridactyl's income as my own. If anyone isn't comfortable with that, please feel free to contact me or any of the other developers and we can make sure that all of your money stays in the central pot.
    
    I hope that the next quarter is better for us all than the last. I have to move house in the middle of June, so I may be a little unresponsive around that time.
    
    We hope you and your families are keeping well,
    
    bovine3dom and the rest of the Tridactyl developers
    
    Hello,
    
    Welcome to the third quarterly Tridactyl newsletter.
    
    It has been an eventful quarter. We received our first payout from GitHub sponsors (it was real, they really did double your donations!). Visual mode has landed in Tridactyl stable. We weren't accepted on to Google Summer of Code. I finally got round to adding a \`setnull\` command which lets you remove default settings, e.g. \`setnull [searchurls.google](http://searchurls.google/)\` allows you to \`open google\` and search for "google" with your default search engine.
    
    I (bovine3dom) have now hit the cap for doubling for GitHub sponsors as I managed to get paid for some commercial open source work through it. If you would still like your donation to be doubled you can sponsor Tridactyl through glacambre's page - [https://github.com/sponsors/glacambre](https://github.com/sponsors/glacambre)) - we'll still put your money into a central Tridactyl pot. No pressure if you don't want to do that :).
    
    In terms of Tridactyl bugs, I tried really hard to fix the "Tridactyl sometimes doesn't execute all the lines in my RC file" bug, even implementing our own locks library to try to eradicate some race conditions. Instead, it mostly just broke some people's configurations in beta, so we swiftly reverted it. The locks are currently used in Tridactyl beta and stable to try to make command line history more reliable ... which works about 50% of the time; the same seems to apply to \`repeat\`, which is a great improvement on the approximately 5% of the time it used to work. We have a bit of a plan to fix this - see issue #2208 [https://github.com/tridactyl/tridactyl/pull/2208](https://github.com/tridactyl/tridactyl/pull/2208))) - but it would be unwise to promise that it will happen any time soon, given our track record.
    
    On to the main event of the past few months. The novel coronavirus. One of the reasons we ask for donations is to fund retreats for the developers of Tridactyl to meet up and work on Tridactyl together, somewhere a bit nice. This clearly cannot happen again for a while. Personally, I am of the view that it would be immoral to encourage international travel until the virus is beaten or endemic in all of the countries involved. I don't see that happening for at least a year.
    
    The question, then, is what to do with the funds in the meantime. Another aspect of this pandemic is that it may take a while for me (bovine3dom) to find a job and that my savings have taken a hammering. After talking about it with the rest of the Tridactyl developers, at the end of March I started to take the majority of Tridactyl's income as my own. If anyone isn't comfortable with that, please feel free to contact me or any of the other developers and we can make sure that all of your money stays in the central pot.
    
    I hope that the next quarter is better for us all than the last. I have to move house in the middle of June, so I may be a little unresponsive around that time.
    
    We hope you and your families are keeping well,
    
    bovine3dom and the rest of the Tridactyl developers
    
-   Hello,
    
    Welcome to the second quarterly Tridactyl newsletter.
    
    Since the last newsletter, we resolved our dispute with the Mozilla add-on reviewers and have been relisted on the AMO. If you like graphs, you can clearly see our time in the wilderness where the AMO did not collect statistics for us here: [https://addons.mozilla.org/en-US/firefox/addon/tridactyl-vim/statistics/?last=365](https://addons.mozilla.org/en-US/firefox/addon/tridactyl-vim/statistics/?last=365)
    
    We've recently added quite a few long-demanded features to the Tridactyl beta, which we'll enumerate in the following paragraphs. The features will be included in Tridactyl stable 1.18.0 which will be released "soon".
    
    There is now a basic "visual" mode which is by default entered whenever non-text-area text is selected and left whenever it is deselected (":set visual{enter,exit}auto {true,false}" to modify this behaviour). Basic movement keys are supported in addition to "s" to search for the highlighted string and "y" to yank it to the clipboard. See ":help vmaps" to see all the binds. To make it easier to enter this mode, "v" and ";h" enter a "highlight element" hint mode.
    
    We have also added an ":apropos" command which searches through all help pages and finds relevant commands and settings. We've already found commands and settings that we had forgotten about. Unfortunately, this doesn't work on all machines for reasons which are unclear.
    
    Another long-awaited feature is that our RC files can now contain escaped newlines with backslashes thanks to saulrh. This makes writing long :js snippets much more palatable. We can't wait to see what you all do with it.
    
    Our final note on changes to Tridactyl is that our smooth scrolling is now actually quite good thanks to Spindlyskit (a first-time contributor). If you had avoided using it before because you didn't like our implementation, you might want to try it out again with ":set smoothscroll true".
    
    On a personal note, bovine3dom completed his PhD in late December and from now until he gets a job has more time to spend on Tridactyl. If there is any issue or feature you desperately want, now is the time to ask. Just bump or create an issue on GitHub and he'll look at it.
    
    In a similar vein, Tridactyl is considering applying to be a host organisation for "Google Summer of Code". If successful and we managed to attract a student, in Summer 2020 Google would pay a student to work on Tridactyl. The deadline for us to apply to this is February 5th. If you have any ideas for projects - please let us know on the issue we just opened: [https://github.com/tridactyl/tridactyl/issues/2107.](https://github.com/tridactyl/tridactyl/issues/2107.)
    
    Finally, if you're sponsoring us on Patreon or via PayPal, you might want to consider switching to GitHub sponsors as they will double any donations received until roughly November 2020: [https://github.com/sponsors/bovine3dom/](https://github.com/sponsors/bovine3dom/) (NB: donations to this page are donations to Tridactyl, not just bovine3dom). With a bit of luck, we'll get our first payout from GitHub Sponsors within the next week.
    
    Thanks as ever for your support,
    
    (Dr!) bovine3dom and the rest of the Tridactyl developers
    
    Hello,
    
    Welcome to the second quarterly Tridactyl newsletter.
    
    Since the last newsletter, we resolved our dispute with the Mozilla add-on reviewers and have been relisted on the AMO. If you like graphs, you can clearly see our time in the wilderness where the AMO did not collect statistics for us here: [https://addons.mozilla.org/en-US/firefox/addon/tridactyl-vim/statistics/?last=365](https://addons.mozilla.org/en-US/firefox/addon/tridactyl-vim/statistics/?last=365)
    
    We've recently added quite a few long-demanded features to the Tridactyl beta, which we'll enumerate in the following paragraphs. The features will be included in Tridactyl stable 1.18.0 which will be released "soon".
    
    There is now a basic "visual" mode which is by default entered whenever non-text-area text is selected and left whenever it is deselected (":set visual{enter,exit}auto {true,false}" to modify this behaviour). Basic movement keys are supported in addition to "s" to search for the highlighted string and "y" to yank it to the clipboard. See ":help vmaps" to see all the binds. To make it easier to enter this mode, "v" and ";h" enter a "highlight element" hint mode.
    
    We have also added an ":apropos" command which searches through all help pages and finds relevant commands and settings. We've already found commands and settings that we had forgotten about. Unfortunately, this doesn't work on all machines for reasons which are unclear.
    
    Another long-awaited feature is that our RC files can now contain escaped newlines with backslashes thanks to saulrh. This makes writing long :js snippets much more palatable. We can't wait to see what you all do with it.
    
    Our final note on changes to Tridactyl is that our smooth scrolling is now actually quite good thanks to Spindlyskit (a first-time contributor). If you had avoided using it before because you didn't like our implementation, you might want to try it out again with ":set smoothscroll true".
    
    On a personal note, bovine3dom completed his PhD in late December and from now until he gets a job has more time to spend on Tridactyl. If there is any issue or feature you desperately want, now is the time to ask. Just bump or create an issue on GitHub and he'll look at it.
    
    In a similar vein, Tridactyl is considering applying to be a host organisation for "Google Summer of Code". If successful and we managed to attract a student, in Summer 2020 Google would pay a student to work on Tridactyl. The deadline for us to apply to this is February 5th. If you have any ideas for projects - please let us know on the issue we just opened: [https://github.com/tridactyl/tridactyl/issues/2107.](https://github.com/tridactyl/tridactyl/issues/2107.)
    
    Finally, if you're sponsoring us on Patreon or via PayPal, you might want to consider switching to GitHub sponsors as they will double any donations received until roughly November 2020: [https://github.com/sponsors/bovine3dom/](https://github.com/sponsors/bovine3dom/) (NB: donations to this page are donations to Tridactyl, not just bovine3dom). With a bit of luck, we'll get our first payout from GitHub Sponsors within the next week.
    
    Thanks as ever for your support,
    
    (Dr!) bovine3dom and the rest of the Tridactyl developers
    
-   Hi!
    
    It's been an eventful few months for Tridactyl. We were [delisted from the AMO](https://github.com/tridactyl/tridactyl/issues/1800) and have been slowly trying to get listed again. We're currently waiting to hear back from a reviewer on a query of ours before we submit what we will hope be our final revision which will be accepted. To have a hope of being relisted we have had to do some stuff we didn't want to do, namely editing \`user.js\` for some users without their consent - that issue details it all.
    
    In light of this, the maintainer for our Arch Linux builds switched to a method which means that Mozilla does not have to sign Tridactyl - so they no longer get a say in what Arch Linux can or cannot provide for its users. If you're using Arch, I'd suggest you switch to these builds for peace of mind: \`pacman -S firefox-tridactyl\`.
    
    There are some new features in Tridactyl 1.17.0 too: you can now use \`source --url\` to source an RC file from a URL without using the native messenger and \`extoption\` allows you to open the option pages of other extensions. We will probably release 1.18.0 soon which, hopefully, will make \`source\` a little more reliable which has been a perennial request from users with complex RC files.
    
    A major reason that I'm writing this post is because [bovine3dom has been accepted on to GitHub Sponsors](https://github.com/users/bovine3dom/sponsorship). This initiative is a little like Patreon but Microsoft will match (i.e. double) any donations you make until October 2020 and charge no fees. You may wish to consider switching to this - simply follow this link: [https://github.com/users/bovine3dom/sponsorship](https://github.com/users/bovine3dom/sponsorship)
    
    Thanks as ever for your support,
    
    bovine3dom and the rest of the Tridactyl developers
    
    Hi!
    
    It's been an eventful few months for Tridactyl. We were [delisted from the AMO](https://github.com/tridactyl/tridactyl/issues/1800) and have been slowly trying to get listed again. We're currently waiting to hear back from a reviewer on a query of ours before we submit what we will hope be our final revision which will be accepted. To have a hope of being relisted we have had to do some stuff we didn't want to do, namely editing \`user.js\` for some users without their consent - that issue details it all.
    
    In light of this, the maintainer for our Arch Linux builds switched to a method which means that Mozilla does not have to sign Tridactyl - so they no longer get a say in what Arch Linux can or cannot provide for its users. If you're using Arch, I'd suggest you switch to these builds for peace of mind: \`pacman -S firefox-tridactyl\`.
    
    There are some new features in Tridactyl 1.17.0 too: you can now use \`source --url\` to source an RC file from a URL without using the native messenger and \`extoption\` allows you to open the option pages of other extensions. We will probably release 1.18.0 soon which, hopefully, will make \`source\` a little more reliable which has been a perennial request from users with complex RC files.
    
    A major reason that I'm writing this post is because [bovine3dom has been accepted on to GitHub Sponsors](https://github.com/users/bovine3dom/sponsorship). This initiative is a little like Patreon but Microsoft will match (i.e. double) any donations you make until October 2020 and charge no fees. You may wish to consider switching to this - simply follow this link: [https://github.com/users/bovine3dom/sponsorship](https://github.com/users/bovine3dom/sponsorship)
    
    Thanks as ever for your support,
    
    bovine3dom and the rest of the Tridactyl developers