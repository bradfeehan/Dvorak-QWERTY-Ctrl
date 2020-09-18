Dvorak-QWERTY-Ctrl
==================

A Windows counterpart to the Mac OS X "Dvorak - QWERTY ⌘" keyboard layout

What?
-----

A keyboard layout for Windows which behaves the same as the Dvorak
Simplified Keyboard for normal typing, but when `Ctrl` is held down, it
behaves like a normal QWERTY layout.

Why?
----

When I started using the [Dvorak Simplified Keyboard][1] layout, I found
that the hardest part was adjusting to the different keyboard shortcuts.
For example, the shortcuts for cut, copy, and paste (`Ctrl` + `X`, `C`,
and `V`, respectively) are conveniently at the bottom-left of a QWERTY
keyboard, allowing for the left hand to perform these commands while the
right hand remains on the mouse. However, using the Dvorak layout, these
three keys are scattered towards the right-hand side of the keyboard,
resulting in uncomfortable stretches to perform many common keyboard
shortcuts (including Close Window, Refresh, New Tab, Save, Find, Undo,
Cut, Copy, and Paste, to name a few of the more annoying ones).

Mac OS X provides a keyboard layout called "[Dvorak - QWERTY ⌘][2]",
which attempts to address this issue. While typing normally, this layout
is identical to the standard Dvorak Simplified Keyboard. However, when
pressing a keyboard shortcut which includes the Command key, the layout
behaves as a QWERTY keyboard would. This means that all shortcuts
involving the Command key are the same on this layout as on a QWERTY
layout -- and on Mac OS X, most common keyboard shortcuts involve the 
Command key. However, Windows doesn't have any similar keyboard layout.

Using the [Microsoft Keyboard Layout Creator][3], I created this custom
keyboard layout to emulate the behaviour of the Dvorak - QWERTY ⌘
layout. Of course, since there'sno Command key in Windows, this layout
switches when using the `Ctrl` key instead.

How?
----

The Microsoft Keyboard Layout Creator allows you to use an existing
keyboard layout as a starting point for your own custom layout. However,
instead of the obvious choice of starting with a Dvorak layout and
setting a different value for each key in the `Ctrl` shift state (which
didn't work), I started with a QWERTY layout and changed all the key
scan codes, using the following procedure:

1. Start with any key, e.g. the bottom-left of the keyboard (which is 
   `Z` on QWERTY)
2. Find what key is in the corresponding physical location on the 
   Dvorak layout (semi-colon, for this key)
3. Find where *that* key is on a QWERTY keyboard (to the left of the
   `Enter` key)
4. Grab the key-code of that key, 28 in this case (having another
   untouched instance of MKLC open is useful for this)
5. Change the scan code of the original key (bottom-left key on the
   keyboard) to this scan code (from `2c` to `28`)
6. Repeat this process for all keys -- you can skip those that are the
   same on both layouts (`A`, `M`, the numbers, `\` and <code>`</code>)
7. Validate the layout, (**Project** > **Validate Layout**) making sure
   there's no duplicate scan codes or other errors/warnings
8. Export the DLL and setup package, then install it

I needed to restart after these steps, for it to finally work, but YMMV.

This Git repo contains the final DLLs and installers, as well as the
.klc file (if you don't want to trust my binaries).

Installation
------------

Copy the full repo somewhere and run `usdvqwct/setup.exe`.

Or, download MKLC from [here][3] (as of Sep 18 2020, the download is no longer avaliable) 
and open `Dvorak-QWERTY-Ctrl.klc`,
then go to **Project** > **Build DLL and Setup package**. Click "Yes"
when it offers to open the output directory, and run `setup.exe`.

- if you are on pre-windows 10 computer,
  This will add the "United States-Dvorak (QWERTY-Ctrl)" layout in
  **Control Panel** > **Languages**.
- If on windows 10, go to 
  **Setting** > **Time & Language** > **Language** > **Prefered languages**, 
  select **English** then click **Options**, under keyboard, you will see **United Stats-Davorak (QWERTY-Ctrl)**

Then restart your computer to load the configuration


[1]: <http://en.wikipedia.org/wiki/Dvorak_Simplified_Keyboard>
[2]: <http://en.wikipedia.org/wiki/Dvorak_Simplified_Keyboard#Mac_OS>
[3]: <http://msdn.microsoft.com/en-au/goglobal/bb964665.aspx>
