# Introduction

```ansi
*=========================================================================*
-            ALTSNAP for Windows NT4/2000/XP/Vista/7/8.x/10/11            *
- Modified by Raymond Gillibert from original AltDrag by Stefan Sundin   *
-                    release 1.61 (September 1, 2023)                     *

*-------------------------------------------------------------------------*
- Download MEGA: https://mega.nz/folder/mW5ExCCT#gI8DQICICk-y4FIjxaqtGg   *
- Download GitHub: https://github.com/RamonUnch/AltSnap/releases/         *
- Original Stefan Sundin: https://stefansundin.github.io/AltDrag/         *
*=========================================================================*
```

AltSnap gives you the ability to move and resize your windows in a new way.
When AltSnap is running, you can simply hold down the Alt key and then click
and drag any window.

This behavior already exists in Linux and other operating systems,
and AltSnap was made with the mission to copy that behavior to the
Windows platform.

## Move Window

You can Move a Window by pressing Alt and using (by default) the left mouse
button. If you double-click it will maximize/restore the window, and if you
hold Shift while double-clicking, it will roll/unroll the window on its
title bar.

## Resize Window

You can use (by default) the right mouse button to resize windows.
Imagine the window divided into nine squares, and you will resize the
corner nearest to where you press. The corners are slightly bigger
than the middle regions by default (adjust using AltSnap.ini).

```ansi
 **________________________________________**
/ @ Title bar   |            |         _ O X \
|===============+============+===============|
|    top        |    top     |        top    |
|    left       |            |      right    |
|---------------+------------+---------------|
|               |            |               |
|    left       |   center   |      right    |
|               |            |               |
|---------------+------------+---------------|
|               |            |               |
|    bottom     |            |     bottom    |
|    left       |   bottom   |      right    |
|***____________|____________|__*__________**|
```

If you double-click (double right click) these regions, the window will be
moved to the respective corner on your screen (like Aero Snap), so you can
quickly arrange your windows to fit on the screen. If you press Shift in
addition, the respective window side will be extended to the monitor side.
Finally if you press Ctrl and double-click on the center region it will
maximize/restore the window.
The center region can be configured to behave differently (see options).

## Other Actions

AltSnap can be configured quite finely You can set any button to perform
any action among a list: Move, Resize, Close, Minimize, Maximize, Lower,
AlwaysOnTop, Borderless, Center, Roll, Menu, Kill and Nothing.

By default, the middle mouse button is configured for the Maximize action,
that maximizes/restores the window. Press Shift to minimize.

## Tricks You Should Know About

- AltSnap will not bring windows to front by default. Press Ctrl to bring the
  window to front, or configure AltSnap to do that automatically.
- AltSnap will mimic Aero Snap by default, so try dragging windows to the
  edges of your monitor. Corners work too!
- If you use multiple monitors, you can hold Ctrl or Shift while dragging to
  trap the window within the current monitor. This is particularly useful if
  you want to Aero Snap at edges between monitors.
- While dragging, windows borders will snap to each-other. This behavior can
  be changed in the config. If you disable it you can still press Shift while
  dragging to force windows borders to snap to each other.
- If you have automatic snapping enabled, you can temporarily disable it by
  pressing the space bar while dragging.
- If you are moving a window you can press the right mouse button to toggle
  the maximized state.
- If you use the scroll wheel to change the volume, you can hold shift to
  increase the rate the volume is changed. If you use the scroll wheel to
  change the transparency, you can hold shift to decrease the rate the
  transparency is changed.
- If you have Scroll inactive windows enabled, you can hold the Shift key to
  scroll horizontally. Note that this relies on that the program has support
  for normal horizontal mouse wheel scrolling, which not all programs have.
- If you can't move a particular window, try elevating AltSnap.
  Normal programs can't interact with programs that are started with
  administrator privileges.
- If you need to <kbd>Alt</kbd>+<kbd>Click</kbd> on a program and do not want to blocklist the
  program, you can use the <kbd>Win</kbd> instead of Alt. If this is not enough
  or if you do not want to use the <kbd>Win</kbd>, you can hit Ctrl and release it
  while keeping Alt pressed and then click.
- A key combo can be used in order to activate AltSnap, this allows using
  <kbd>Alt</kbd>+<kbd>Win</kbd> to drag windows and leaves alone the <kbd>Win</kbd>+<kbd>Click</kbd> and the <kbd>Alt</kbd>+<kbd>Click</kbd>
  that some programs may require.
- Try to add the Shift modifier key for any action, usually it has an effect.

## Configuration

To change the configuration from default, double-click on the tray icon, and
you will be presented with a lot of choices.

If you want to go further into the configuration, open the AltSnap.ini file
by middle-clicking on the tray icon. You will see all the option there with
a short description.

## Languages

AltSnap is fully translated in French, Italian and mostly translated in many
other languages. All translations are simple ini files encoded in UTF-16 LE.
If you want to create or improve a translation, just add or modify the
associated ini file in the languages directory, and no not forget to send it to
me via a GitHub pull request/issue or PM me, so that everyone can enjoy your
translation. You can use "languages\_en_US baseline.txt" as a starting point if
you want to translate everything to a new language.

## Update

To avoid useless bloat and potential vulnerability AltSnap no longer
auto-updates. You can check for new versions on the GitHub page
If you want automation, install altsnap via the chocolatey package.

- Install with > `choco install altsnap`
- Update with > `choco update altsnap`
- Uninstall with > `choco uninstall altsnap`

You can do the same with `winget`. Note that the `chocolatey`/`winget` package
may take a few days before getting updated.

## Blocklist

Sometimes an AltSnap action interacts with a window you do not want.
For example if you use <kbd>Alt</kbd>+<kbd>Click</kbd> on a specific window, and you do not want
AltSnap to move the window you can add the window name to the windows
blocklist. more details below:
All the list are coma separated and take no spaces before the coma.
A space can be present in the item itself or before the item.

- Process blocklist: List of programs names for which move/resize from
  AltSnap as well as the scroll actions are disabled. Example: Notepad.exe
- Windows blocklist: List of windows with the title|class format for which
  move/resize actions from AltSnap will be disabled
  Example: `Program Manager|Progman,|Shell_TrayWnd,*|Notepad`
- Windows that should ignore the scroll action: List of windows with the
  title|class format that for which the scroll action of AltSnap will not
  apply. Example: `*|Photoshop`
- MDIs not to be treated as such: List of windows for which AltSnap will not
  try to find MDI subwindow. This only applies if the Support MDI is enabled
  and by default contains `*|PPTFrameClass,*|MMCMainFrame` which correspond to
  the PowerPoint window and all the Microsoft Management application such as
  the `services.msc` windows or the device drivers window.
- Process not to be paused or killed: Only applies for the Pause and kill
  action when enabled on <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>Pause</kbd> of Ctrl+<kbd>Alt</kbd>+F4,
  this are program names.

  Program names are pretty straightforward to find. However, a finer control can
  be done using the window's title|class information; they can be found for a
  specific window using the small target in the identify window section of the
  Blocklist tab. You can include all the possible names by using the *|class
  format. This is useful for most programs that have a non-constant title, for
  example Notepad's title is actually the name of the file you are currently
  editing.
  The other way around can be used, and you can specify `title|*` which means that
  all the windows that have this title regardless of their class name will be
  blacklisted. This is a much less common usage.

  The title can also be empty for example: `|Shell_TrayWnd` corresponds to the
  Windows task bar and has an empty title.

  Finally more blacklists can be found in the AltSnap.ini file:
- Snaplist: List of windows with the name|class format to which other windows
  should snap. By default, windows that have no borders cannot be snapped to.
- MMBLower: List of windows that should not be lowered with mouse middle-click on the title bar.
- Default: `CASCADIA_HOSTING_WINDOW_CLASS` that corresponds to the Windows Terminal window.

### Usage

Extract to any folder, and double click on `AltSnap.exe`

Enjoy dragging windows...

You will see a new Icon in the tray

- Right-click on the Tray Icon to see the option menu
- Left-click on the Tray Icon to enable/disable
- Go to the "Configure" menu entry for basic options
- Middle-click on the Tray Icon to open config file AltSnap.ini (advanced)
- You can hide the icon if you want. To show it again relaunch AltSnap.exe

AltSnap Wiki: <https://github.com/RamonUnch/AltSnap/wiki>

Note that this version has some more feature.

## Changelog

### AltSnap 1.61

- Added the Focus Window action. #408
- Add the **Edit snap layout** tray menu entry that re-opens all the windows
   fom the currently selected layout for easier edition. #407
- You can now set RezTimer=3 in the [Performance] section of the .ini file
   to combine a timer based resizing with the usual MoveRate and ResizeRate
   multiplication factors. See #451 and #452 for more details.
- Fix Action without click #455, #456. (huge regression, sorry for that).
- Always focus the window on Always On Top toggle #442
- Fixed: Allow `xxbutton` as hot-click (1.55 regression). #433
- Fixed: the send Original click option must be shown on hotclick,
   not just for the titlebar action.
- Fixed: AltSnap hotkeys not working properly when using AltSnap elevated
   with a non admin account (make use of the ChangeWindowMessageFilterEx()
   function when running on Windows 7 and later). #428
- Partially fixed window resizing when going to a monitor with a
   different DPI. #413
- Fixed French translation, thanks to @TroudhuK
- Updated Japanese translation, thanks to @kakakaya
- Updated Korean translation, thanks to @1kko-ahnlabio
- Add Finish Translation by @6sto based on AltDrag 1.0, see
   <https://github.com/stefansundin/AltDrag/issues/170>

### AltSnap 1.60

- Added the `ZSnapMode` option in the `[Zones]` section of the ini file,
   to change the strategy for choosing the zone on which the dragged
   windows will snap. #405
   Set to 0 to snap to the pointed zones (default, old behavior).
   Set to 1 to snap to the zone which center is the nearest from cursor.
   The second mode will be needed if you want to use overlapped zones.
- The Test Window will now also display the mouse events.
- The test Window will now have a full-screen mode (toggle with F11).
- Added the `MenuShowEmptyLabelWin` Advanced option to display the windows
   with empty titles inside the Windows list menu. #401 @mbartlett21
- Add **All windows list** action that will behave like the
   Window list action but will even display windows outside the
   current monitor. Thanks to @mbartlett21 for this. #384
- You can now set `IgnoreMinMaxInfo` option in the Advanced section
   of the ini file if you want to ba able to resize Windos beyond their
   usual limits, Set to 0 (default) to always disable, set to 1 to ignore
   the minimum size, 2 to ignore maximum size and 3 to ignore both. #374
- You can set the `MenuShowOffscreenWin=1` in the [Advanced] section
   of the ini file to still display windows in a windows menu even
   if they are outside any monitors. Thanks to @mbartlett21. #384
- The *clear AltSnap state* key can now be set to any other key, using
   the `ESCkeys` key list in the [Input] section of the ini file. Default
   value is `1B` (ESCAPE), like with previous AltSnap versions. #386
- Fixed inconsistent key state leading to drag-free actions not working
   and to blocked LMB in some cases. #392, #388.
- Fixed: Now FancyZones snapped Windows will be restored to their proper
   dpi-scaled size. If this causes any issues for you, you can always set
   `FancyZone=2` in the [Zones] section to prevent scaling.
- Updated Chinese translation, thanks to @yatli,
   Updated Polish translation, thanks to @xeophyte,
   Updated German translation, thanks to @Ichisich
   Updated French and Italian translations.

### AltSnap 1.59

- Now AltSnap will respect the system drag threshold. Use `DragThreshold`
   value in the [Advanced] section of the ini file to determine when the
   threshold will be respected. Possible values are:
   0: disabled, like old AltSnap versions,
   1: Enabled when restoring snapped window (default),
   2: Always wait the drag threshold before moving the window,
   3: Same than 2 but also applies to the resize action. #365
- Generalized combo actions: Now you can select any action that will apply
   if a move or a resize action was started. You can configure them in the
   Mouse tab of the config dialog by selecting the **While moving** and
   **While resizing** radio buttons. Those options are available via the
   ini file in the [Input] section using the `M` and `R` suffixes.
   ie: `MMBR=ExtendTNEdge`. Also, an extra `B` suffix can be added for
   alternate action (only available via ini). #217, #362.
- Multiple *snap layouts* are now supported... #232
- New `IScroll` blocklist in the `[Blocklist]` section of the ini file
   That only applies to the Inactive scroll option. #351
- Added the **Move/Extend to next edge** action, That will extend the next
   edge from a snapped window, also available as keyboard shortcuts. #368
- Added the `--help` option, also available as `-help` or `-?` or `/?`.
   It will display a very short summary of available commands. #370
- Fixed: Now a hot-click will not always be blocked, It will be forwarded
   in case no action was done. If you want a hot-click to always be blocked
   set `AblockHotclick=1` in the `[Advanced]` section of the ini file.
- Fixed: Next/Previous stacked window keyboard shortcut no longer depends
   on cursor position, unless you enabled **use pointed window**. #372
- Added the missing Next/Previous laser stacked window. #362
- Fix delay when forwarding a click in some cases. #352
- Fix button up being improperly blocked sometime. #355
- Fixed occasional crash when editing the config dialog.
- Updated German, Korean, French and Italian translations.

### AltSnap 1.58

- Tray icon theme support was added, put an icon theme in the Themes\
   folder and then set `Theme=ThemeName` in the [General] secion of the ini
   file. A theme is a folder containing three tray icons named: tray-off.ico,
   tray-on.ico, tray-sus.ico. Thanks to @erasmion for supplying a theme,
   You can try it with `Theme=erasmion`. #31
- The maximum width in characters of an item in a window list menu can now
   be set from 0-255 by the user using the `MaxMenuWidth` option in the
   [Advanded] section of the ini file. Use 0 for unlimited, default is 80.
   Thanks to @mbartlett21 for the pull request #341.
- Side fraction can now be set independently of the center fraction for more
   flexible configuration. Have a look at the test window and play with those
   values, accessible through the Advanced tab of the config dialog. #318
- Blocklist were improved to allow a mix of both exe names and title|class.
   You can now specify `exename.exe:title|class`. If you omit the ':' and '|'
   the format is assumed to be an exe name only. If you only specify '|',
   the exe check will be omitted and the format will be assumed to be
   title|class, like it was the case before. Example: You want to blocklist
   the `*|CabinetWClass` windows only if they are from explorer.exe, use:
   `explorer.exe:*|CabinetWClass`.
- New **Open ini file** option was added to the tray menu for easy access.
- New: `MaxKeysNum` option can be set to specify the maximum number of
   keys that can be pressed in order to activate AltSnap. This does not
   apply to the keys that are pressed after activation, use the KillKeys
   for this. Default value is 0 (unlimited). #324
- Fixed hot-clicks not behaving properly for left and right mouse buttons
   Now you can configure AltSnap to Move/Resize window with right click while
   still being able to left-click without drag. #340
- Fix Tray icon not displaying properly in some cases #315.
- Fix: No lines drawn in the test window when CenterFraction=0. #319
- Fix lockup when using hot-click on blacklisted window. Part of #334
- Styling options were fixed and AltSnap can now be build with `-std=c99`
   `-Wpedantic` flags.
- `TCHAR` is now preferred over `wchar_t` so that code is more portable and
   future-proof
- Optimizations for ini file loading, this should reduce start time on
   Slow media such as old HDD/CD-ROM/floppy.
- Updated German, French and Italian translations.

### AltSnap 1.57

- New keyboard  actions to move the window in steps to each direction.
   You have the choice between large steps and small steps. To configure the
   size of the steps in pixels, use the `KBMoveStep` and `KBMoveSStep`
   values in the [Advanced] section of the .ini file.
   Default is 100 for large steps and 10 for small steps. #304
- Now the *Restore Window* action is available as a mouse action and will
   let you restore AltSnapped windows to their original size with a single
   click. Setup as a title-bar action it can be used to better integrate
   in the native snapping experiment. #292
- Now the right mouse button can be used inside a menu item of a  window
   list to minimize the corresponding window. The middle mouse button will
   close the window. The menu will remain opened. #290
- Now the `NumberMenuItems` option can be set to 1 in the `[Advanced]`
   section of the .ini file in order to number menu elements from 0-9
   instead of A-Z. This applies to all windows list menu.
- New: Window list action that list all windows on your monitors. It can
   be an alternative to <kbd>Alt</kbd>+Tab. #298
- New Laser stacked windows list action is now available as a mouse and
   keyboard action previously it was only available with the shift modifier
   on the Stacked windows list action.
- New: You now have a *Send original click* option in the action menu
   if you triggered it from the title bar. #302
- New: You now have the **Movement Disabled** entry on the action menu
   that will prevent AltSnap movement from happening in the window.
   The flag can be enabled and disabled as desired for any window. #283
- Now any keyboard shortcut can be setup to suspend/resume Altsnap. #283
- New: AltSnap actions can now be Invoked from the command line. Actions
   will behave like the corresponding keyboard action. AltSnap
   must already be launched and the allow multiple instance option must be
   disabled. Then you can Launch AltSnap:
   `AltSnap.exe -apACTION` to perform the ACTION on the Pointed window
   `AltSnap.exe -afACTION` to perform the ACTION on the Foreground window
   example: AltSnap.exe -afAlwaysOnTop will toggle the topmost flag on the
   foreground window. #285
- Now title or class blocklist item can match start or end with a `*`
   ie: `*ttl|class*` or `*ttl|*class` or `ttl*|*class` or `ttl*|class*`
   You cannot have a star at both ends of an item though. Previously
   matching was limited to the `*ttl|class*` form. #305
- Now with the `EndSendKey` option in the [Input] section of the ini file,
   you can specify which key will be sent at the end of a movement to
   prevent menu being selection or the window menu from popping up
   The default value is `EndSendKey=11` that corresponds to the Ctrl
   key that is used since ever in AltSnap and AltDrag. #309
- Try as much as possible to Maximize/restore windows asynchronously to
   avoid mouse locking.
- Fixed Stacked windows menu font is now the current system menu font
   instead of the dialog font. #284
- Fixed: Crash in the Stacked window list. #284
- Fixed: Pressing ESC when cancelling a stack window menu will no longer
   focus the first window of the list. #284
- Fixed: Some crashes in low memory situation.
- Fixed: The `hooks.dll`file will only be loaded from AltSnap's directory.
- Fixed: #239 Window transparency would sometime not be restored when
   using the Opacity while moving option.
- Fixed: #295, Windows Terminal will no longer minimizes when selecting
   the Minimize all other windows option.
- Fixed: Removes the topmost indicator or display the context menu when
   the click is released instead of down for more consistent UI experience.
   This will also allow to handle drags in the future if needed.

### AltSnap 1.56

- Fixed Move windows with long left click option (1.55 regression).
- GUI: Minor adjustments to avoid clipping of the topmost indicator option
   in the Advanced tab.
- Adjustments to the French translation by @TroudhuK

### AltSnap 1.55

- New action, you can now pop up a **Stacked window list** that will show
   the list of windows that are stacked with the pointed window. You can
   then select the window you want and it will be set to the foreground.
   Shift extends the stack to all windows that are under the mouse pointer.
- New action: **Next/Prev stacked window**, available as mouse action and
   as wheel action. Again add shift to extend the stack.
- New: Now an indicator for windows that were set AlwaysOnTop can be set.
   Check  the **Show an indicator on always on top windows** option in the
   Advanced tab. The indicator will also show a list of other AlwaysOnTop
   windows when right-clicked. You can also set the `PinColor` option in
   the [Input] section of the .ini and the `PinRate` option in the
   [Performance] section of the .ini can be used to set the color of the
   indicator and the rate at which it gets refreshed.
- New: You can now configure any keyboard shortcut for any action.
   Note that this creates system level keyboard shortcuts, and you will be
   unable to configure a shortcut that already existed (this is a good thing).
   Go to the Keyboard tab of the config dialog, select the option for which
   you want to configure a shortcut, then edit it manually or click the
   Pick keys button and press your shortcut, then hit the Save button.
   You can decide whether those keyboard-only actions should apply to the
   pointed or to the focused window. #264, #268
   You will need to reconfigure Kill on Ctrl+<kbd>Alt</kbd>+F4 and such.
- New keyboard-only actions to move/extend the window to the surrounding
   zones in the snap layout.
- New: Now you can set up `MoveUpT` and `ResizeUpT` actions to be
   performed when the click was performed inside the title-bar.
   CHECK YOUR CONFIG, as those options did not exist before and
   will default to Nothing. The options were also added to the GUI.
- New: Two Zoom window action that can be setup for a mouse wheel.
   The first one will resize only vertically/horizontally when the
   mouse points at the pure side sectors, and the second one will
   always zoom proportionally instead. In addition, you can adjust
   the fraction by which the window is zoomed using the `ZoomFrac`
   and `ZoomFracShift` options. #239
- New: To fix menu not getting canceled in some cases, you can add the
   `DragSendsAltCtrl` option in the [Advanced] section of the ini. #255
- New now you can set the value of `BLUpperBorder` in the `[Advanced]`
   section of the `.ini` file, and it will select in the same fashion as
   `BLCapButtons` but this time only for the top resizing border. Default
   value is also 3 to prevent left and right button to trigger AltSnap in
   the top resizing borders. `BLCapButtons` now concerns only the caption
   buttons and no longer the top resizing border.
- Now you can customize the action menu by adding or removing menu items
   using the `ACMenuItems` option in the `[Advanced]` section of the .ini
   file. Default value is -1 for all menu entry. #240
- Updated German translation thanks to @Ichisich
- GUI: Now the `SnapGap` option is available through the GUI. #200
- Fixed #150: The top owner window is now used for the always on top
   action. This avoids some parts of the program not being affected.
- Fixed #235: Inconsistent focusing of windows.
- Fixed #274: The window is now refocused when the action menu is canceled.
- Fixed: More reliable prevention of menu activation and/or start menu
   popping up problems.
- Fixed: Window maximum and minimum sized would be ignored in center
   resizing mode, leading to window running outside the screen when
   resizing it beyond their maximum size.
- Fixed: Focus windows when dragging not working in some cases. #250
- Fixed: The title-bar Action menu not disappearing on defocusing in some
   cases. #263.
- Fixed now if the owner window has an empty RECT it will no longer be
   used to hold the topmost indicator (ie: ForceToolkit main window).

### AltSnap 1.54

- New: You can now set `UseZones=9` in the `[Zones]` section of the .ini
   file and Windows will snap to the layout without having to press Shift.
   Pressing shift or hitting space will disable zone-snapping instead. #219
- Now if you use Zones, and disable the **Toggle maximize state with the
   resize button while moving** advanced option, then Zone snapping will be
   toggled by any secondary buttons, like with FancyZones. #219
- New: Now you can set the opacity of the hollow rectangle (0-255) used
   when the show window content while dragging option is disabled or when
   FullWin=0. to do this you must modify the `TransWinOpacity` value in the
   `[Performance]` section of the .ini file. #223
- New now you can set the value of `BLCapButtons` in the `[Advanced]`
   section of the .ini file to choose for each mouse button if the titlebar
   action will be or not extended to the caption buttons and the top
   resizing border. Use `BLCapButtons=0` if you want all buttons to
   consider the extended caption and use -1 for none of them. The default
   value is 3 to avoid the extended caption for the left and right mouse
   buttons so that AltSnap avoids interaction with minimize, maximize
   and close caption buttons (`[_]`, `[O]`, `[X]`). If you are unsure stick to
   the default value if you want less title-bar detection use -1. #236
- Now a checkmark in the action menu will indicate the always on top state
   of the pointed window. Same for Maximized and Borderless flags (#184).
- Changed: Now when auto Snapping is enabled at the maximum level, then
   pressing shift will disable snapping instead of doing nothing.
- Changed: Now several keys can be selected for the alternate action
   ie: the `ModKey` value in the `[Input]` section is a key list and works
   like the Hotkeys value. Same was applied to `HScrollKey`. (#207)
- Fixed: Now smarter aero-snapping will be properly re-enabled when you
   release Shift. (#211)
- Fixed: Snapping to the layout  will no longer ignore the Max snapping
   speed option. (#218)
- Fixed multiple Action menu popping up in some cases. (#213
- Fixed some stuck mouse buttons in some cases when using the Move
   Windows with a long left click option.
- Fixed #220, Mimic aero snapping is no longer necessary for Snapping
   to the snap layout (Zones).
- Fixed: Modifying the config will no longer reset the `UseZones` value.
- Fixed #226, #229: Now the `DWMWA_CAPTION_BUTTON_BOUNDS` rectangle is
   used to ensure that we are inside a title-bar and not caption buttons.
   This fixes an annoying Windows 10 bug.
- Fixed, now the common french e dans l'o `�` character is available in
   the default extended character menu (LATIN SMALL/CAPITAL LIGATURE OE).
- Updated Chinese translation, thanks to @yatli.

### AltSnap 1.53

- New: An extra key menu can now be enabled in the Keyboard tab of the
   config and a popup menu with additional characters will show up when
   you press a key from A-Z for a long time. This is similar to the way
   Android and MacOS behave. The menu entry can be selected by pressing
   the accelerator key (first column), or using the usual arrows/mouse.
   The menu can be configured individually for each language (#181).
- New: Now any key can be mapped to mouse button 6-20, this is useful if
   you have more than 5 mouse buttons and want to use your extra buttons with
   AltSnap. You can first bind your extra mouse buttons to keys that you
   would never use ie F13-F24, or some multimedia keys or even in some cases
   to undefined virtual-keys codes, then add those virtual key codes in the
   `XXButtons` key list (space separated hexadecimal values). Then those key
   will be turned in MB6, 7, 8... events in the order of the list, finally
   you can map an action to the corresponding mouse button, in the [input]
   section of the .ini file. I advise to also add those buttons to the
   `Hotclicks` key list. Finally keep in mind that any keys added to the
   `XXButtons` list will be unusable outside AltSnap.
   Check issue #175 for the feature development and more tricks.
- New: the `Bottommost` list was added to the `[Blocklist]` section of the
   ini file. When AltSnap lowers a window, it will try to keep it above all
   those Bottommost windows. Default value is `*|RainmeterMeterWindow` for
   the Rainmaker skin windows (fixes #189).
- New: You can now replace the all directions center resize mode by the
   **Closest side** mode that picks the closest side resizing mode instead.
   The test window will be updated accordingly (see issue #193).
- New: Now pressing Ctrl+N in a test window will open a New one.
- Fixed: Now maximizing a window with the Action without click option will
   no longer prevent further movement.
- Fixed: The long click move option now works when left and right buttons
   are swapped, it will also no longer interact with blacklisted windows.
- Fixed MDI ancestor detection to avoid AltSnap freezing on WinTabber.
- Fixed: `MinAlpha` and `AeroSpeedTau` being ignored (1.52 regression).
- Fixed: #183 Titlebar move action would not work properly when no primary
   action was selected.
- Fixed: #179 Smarter aero snapping mode will always consider the current
   window size/position and ignore the original AltSnapping.
- Fixed: Now it will remain possible to snap to windows that were made
   borderless using AltSnap (partially fixes #185).
- Changed: minor code refactoring, inducing even more exe size reduction.
- Updated German translation thanks to @Ichisich, updated Korean translation
   thanks to @1kko.

### AltSnap 1.52

- New: Now a help message is added to the test window to indicate how to
   setup snap layout (zones).
- Changed: some code refactoring and unification inducing size reduction.
- Fixed: Lag when dragging and resizing some programs (issue #160)
- Fixed: #172, drag was locked down when combining and action and hotclick.
   Also, now if a hot-click is combined with the Move or Resize action then a
   long click will be forwarded to the pointed program is no drag occurred.
   This long click will not even be necessary if you enabled the
   **Avoid blocking <kbd>Alt</kbd>+<kbd>Click</kbd>** option in the General tab of the config.
- Fixed: #124, A window will be restored to its original position when
   using the Move+Resize click combo without a drag.
- Fixed: bugs in rolling and snapping code.
- Updated French and Italian translations
- Updated German translation, thanks to @Ichisich.

### AltSnap 1.51

- Fixed regression that would make it impossible to select alternate action
   for mouse button 4 and 5.
- Fixed: Now the LongClick Move will no longer trigger if the cursor is
   pointing toward a system menu or a scroll bar or any of the caption
   buttons `[?][_][O][X]`, in the titlebar.

### AltSnap 1.50

- New: Major changes in the title bar handling. A set of specific actions
   can be configured for each mouse button to apply when clicking on the
   title bar. Those actions can be configured to be used without pressing
   the hotkey if you want. This replaces all special title bars options:
   `LowerWithMMB`, `RollWithTBScroll`, `NormRestore`, `TitlebarMove`,
   now removed. **CHECK YOUR CONFIG** when you install this update...
- New: Now, if you perform a long <kbd>Alt</kbd>+<kbd>Click</kbd>, the click will be forwarded
   to the pointed program, simulating a normal <kbd>Alt</kbd>+<kbd>Click</kbd>. You can also check
   the **Avoid blocking <kbd>Alt</kbd>+<kbd>Click</kbd>** option (General tab) and the Click will
   always be redirected, this will also disable all double-click actions.
- New: A specific action can be configured when the Move or Resize action
   is release without performing a drag, so for example you can set
   `MoveUp=Minimize` in the `[Input]` section of the ini file and then
   <kbd>Alt</kbd>+Move+drag will just move the window as normal, but <kbd>Alt</kbd>+Move+Release
   will minimize the window. By default, it needs to be a long click but if
   you check the avoid blocking <kbd>Alt</kbd>+<kbd>Click</kbd> option then any click will work.
   Same for the resize action using `ResizeUp` option. You also have the
   Alternate versions for each one with the B sufix. Also, if you Hold Ctrl
   while releasing the click the action will not be performed.
- New: Now the Resize+Move click combo will snap the window to the
   corresponding corner (similar to Move+Resize => Maximize).
- New: Mute sounds action to toggle mute state on Win2k+.
- New: Snap to side/corner action is available, and is equivalent to the
   double-right-click aero-snapping.
- New: The `RezTimer` option was added to the `[Performance]` section of
   the ini file and permits to move the cursor only at the default event
   time resolution (every 16ms). It can be combined with `FullWin=0` and is
   very low on resource consumption. It is an advised mode if your monitor
   refresh rate is only 60Hz. If the option is used then all the other
   rates are ignored.
- French, Italian, translations are up-to-date. Thanks to @1kko for
   Korean translation and @Ichisich for German translation.
- Fixed: now the config dialog will show up in the corner your cursor is
   when you click on the tray icon.
- Fixed: now the borderless action will save the old window style.
   Also Windows that have been set borderless by AltSnap will still be
   considered resizable.
- Fixed: Colors of the *Test Window* now depends on system colors.
- Fixed: Now the `RefreshRate` delay is almost millisecond accurate, it used
   to be 16 ms accurate, rendering it useless on high-spec computers.
- Fixed: the show window content while dragging will no longer be ignored
   on newer Windows versions. The `FullWin` option in the `[Performance]`
   section of the .ini file can be set to 1: force on, 0: Force hollow,
   and 2: Autodetect based on Windows setting.
   The color of the hollow rectangle can be set in hex RGB via the
   `FrameColor` option in the [Input] section, default is 80 00 80.
- Fixed: <kbd>Alt</kbd>+Shift will be blocked, by sending Ctrl, if an action occurred.
   This avoids unwanted keymap changes.
- Fixed: Volume action now simply sends the multimedia key events.
   It should work on Win2k+, and will show a visual indicator on Win10.
- Fixed: Sometime a maximized window could become impossible to restore
   with AltSnap.

### AltSnap 1.49

- New: New way of arranging your windows: Grid mode. It replaces the snap
   layout with a simple grid than can be configured in the ini file. You can
   Set `UseZones=3` in the [Zones] section of the .ini file to enable grid
   mode then you can set the number of grid lines/columns using the
   `GridNx/GridNy` options. Gor Grid mode I suggest to set UseZones=7 (3+4)
   so that the window get extended without having to press Ctrl.
- New option to disable AltSnap on Maximized windows (advanced tab)
   You can also use the `BLMaximized` option in the .ini file.
- New: AltSnap can now be activated with a long mouse click, check the
   corresponding option at the bottom of the Mouse tab. Default long click
   delay is the system double-click delay, it can also be manually set via
   the `LongClickMove` option in the ini file. Only the left click for
   movement is supported, it was suggested by @actforjason.
- GUI: `Smarter Aero Snap dimensions` and `Never restore AltSnapped windows`
   options were added to the GUI so they can be configured easily.
- Fix: When using the Kill Action on a suspended window, AltSnap will send
   the WM_CLOSE message and the terminate confirmation should appear. For now,
   it is impossible to really kill the process via AltSnap because its
   window is Ghosted as soon as windows detects the process is hung.
- Fix: Never restore AltSnapped windows option can be combined with Smart
   aero snap dimensions, and perform properly (#133)
- Fix: Now all keys from A-Z are in the Killkeys list to avoid interaction
   with system shortcuts that might put AltSnap in an inconsistent state
   ie: <kbd>Win</kbd>+L, <kbd>Win</kbd>+V...
- Fix: The Close Action now behaves correctly on Excel.
- Fix: Maximum number of zones in the snap layout was raised to 2048.
- Updated German and Chinese translations.

### AltSnap 1.48

- New action: Minimize all other windows, similar to aero-shake, but available
  as a mouse action, and in the action menu.
- New: Now when using the **Lower windows by middle-clicking on title bars**
  option Ctrl+Middle-click in the title bar will toggle the Always on top
  state and so will Middle-click on the Min/Max/Close buttons.
- New: `SnapGap` value can be set into the `[Advanced]` section of the ini
  file and will set an additional gap between snapped windows/monitor sides.
  You can put a negative value if you want an overlap. Default is 0
- New: `Shiftkeys` keys list was added in the `[input]` section of the `.ini` file,
  to configure another key instead of the Shift key. The default is `A0 A1`,
  for left and right shift but this is now a customizable key list.
- New: `ShiftSnaps` option was added in the `[Advanced]` section of the ini
  in order to enable/disable the border-border snapping activation with the
  shift key (default is 1).
- Fixed: Now when resizing several windows at the same time the DeferPos
  windows functions are used to minimize flicker.
- Fixed: Now when disabling window to window snapping with space while
  dragging, the smart window snapping will also be disabled.
- Fixed AltSnap would block <kbd>Alt</kbd>+Space if no drag occurred, this was a problem
  when using **Action without click**.
- Fixed: smart aero-snapping only taking into account windows snapped on the
  other side of the monitor.
- Fixed: non-resizable windows will longer be maximized with right click
  while moving.
- Fixed Maximize Vertically action that would erase the old restore state.
- Fixed some crash when launching again AltSnap with a previous instance.
- Fixed Tray icon handling under Win10.
- Changed: Now when the space key is pressed for a movement the snap state
  will be toggled between no snapping and all border-borders snapping.

### AltSnap 1.47

- Project was renamed from **AltDrag__ to __AltSnap** to avoid conflict with
  Original AltDrag from **Stefan Sundin**. Old choco package will no longer be
  updated and will be given back as soon as Stefan asks for it.
  I advise to all users to uninstall AltDrag and install AltSnap.
- **New:** Support of Snap Layouts, also called Zones. All associated settings
  are in the `[Zones]` section of the `.ini` file **read carefully**:

  1) Check the **Snap to layout** option (`UseZones=1` in the .ini).
  2) Configure your layout by opening several *Test Windows* from the tray.
  3) Arrange those windows across all of your monitors as you wish.
  4) Go again to the tray menu and hit **Save test windows as snap layout**
  5) A confirmation dialog will ask you if you want to save, hit yes.

  Now you will be able using the Shift key to snap the window you move to the
  pointed zone, Add the Ctrl key and drag the cursor to extend the windows
  across several zones. If the cursor is close from two or more zones then
  the window will also be extended to several zones. Use the `InterZone`
  value to adjust this threshold distance in pixels (default 32).
- **New:** Added the **Restore FancyZones snapped windows** option in the
  Advanced tab and `FancyZone` option in the `[Zones]` section of the ini.
  set it to 1 if you want AltSnap to be able to restore windows that were
  snapped using PowerToys' FancyZones. This only applies to x86_64 builds
  of AltSnap. I highly recommend this to FancyZones users.
- **New:** Added a `AResize` whitelist in the `[Blocklist]` section of the .ini
  file in order to force AltDrag to resize windows that do not have the
  `WS_THICKFRAME` style, when the Resize all windows option is disabled.
- **New:** Added the option to move windows via AltDrag without hotkey,
  by clickling on the titlebar. It is similar to the **hooks windows**
  feature that was present in the original AltDrag and can be activated
  via the `TitlebarMove` option in the `[Advanced]` section of the .ini.
- **New:** Now a **modifier key** can be set instead of the invert Move/resize
  key in order to use an alternate set of customizable actions for all
  buttons. They can be configured in the Mouse tab of the config dialog,
  or manually in the `.ini`, using a B suffix for buttons e.g., `LMBB=Resize`.
- **New:** Maximize Vertically action, use Shift to maximize horizontally.
- Changed default `RefreshRate` to 0 to favor the smoothest movement instead
  of performances also default is now `MoveRate=1` and `ResizeRate=2`.
- Restore information for snapped windows are now stored in Windows
  properties. This simplifies the code, and allows AltDrag to be restarted
  without loosing restore info, also restore information shared
  between different AltSnap instances.
- Updated to tdm-gcc-10.3 for i386 and x86_64 builds with one compiler.
- Updated Chinese translation by *Yatao Li* (`zh_CN.ini`).
- Updated German translation by *Ichisich* (`de_DE.ini`).
- Fixed: Sometimes mouse-up would trigger a menu after an action.
- Fixed: potential crash using the config panel.
- Fixed: display maximize/restore animations when using the maximize action
- Fixed: avoid to play the minimize/restore animations when unrolling
  a maximized-rolled window.
- Fixed: Now cloaked windows will no longer be snapped to, this also
  prevents windows from snapping to others through different virtual
  desktops under Win10.
- Fixed: When disabling the "Resize all windows" option, then windows would
  no longer snap properly, even if they were resizeable.

### AltDrag 1.46

- Fix `-elevate` command line parameter being ignored. this also fixes the
  **Elevate to administrator privilege** option for autostart.
- Fix major bug: AltDrag would capture the wheel input when Alt Was pressed
  even if `Nothing` was selected as wheel action.
- Minor code tuneup

### AltDrag 1.45

- New: Now the `ScrollLockState` option in the `[Input]` section of the ini
  file can be set to 3 to enable AltDrag only when <kbd>Scroll Lock</kbd> is off.
- Fixed: Now the `SWP_NOSIZE` and flag is used when simply moving a window.
  This prevents rolled windows from partially unrolling. Also, the
  `SWP_ASYNCWINDOWPOS` flag was added where applicable and this fixes
  an ugly Win 10 bug that would change the borders of some moved window.
- Fixed: When using maximizing a window by snapping to the top,
  it would sometime prevent further movement when `FullWin=0`.
- Fixed a last minute bug introduced in 1.44 that would restore rolled
  windows as soon as you moved them.
- Fixed: Now when AltDrag is suspended with the Scroll lock state option,
  The notification icon will change.
- Fixed some stuck alt bugs thanks to **scx**.

### AltDrag 1.44

- **Smart aero dimensions** was added in the General Tab of the config.
  With this option checked (default) AltDrag will adjust the dimensions of
  the snapped window to the other snapped windows that were resized.
  Also snapped windows will still be restored by the move action even after
  having been resized. This was suggested by @KoleckOLP. MDI also work.
- New important feature: The **Resize other snapped windows with Shift**
  option was added in the General tab of the config. If it is checked, then
  any window snapped or touching to sides of the currently resized window
  will be resized to remain stuck to the current window when you press the
  Shift key. If you want to always resize the touching windows, then you
  can manually set `StickyResizing=2` in the [General] tab in AltDrag.ini.
  In this case, pressing shift will prevent the "sticky resizing".
  MDI windows are also supported.
- New setting to enable/disable AltDrag based on **Scroll Lock** state.
  see in the Keyboard Tab.
- Now an action can be selected for both scroll wheels independently.
- New action for scroll wheel: Horizontal scroll.
- New now the '*' joker can be used at the end of the class or at the
  beginning of the title, in the form: `*end of title|class start*`
  Example: `*|Winamp*`. This may be useful to make better rules.
  Note that the processes blacklists are not concerned by this.
- New: If the first element of a blocklist is `*|*`, then all windows that
  are not listed will be considered as part of the blocklist. This turns
  the blocklist into a whitelist ie: list of windows for which AltDrag
  will be enabled. It can be useful if you only want to use AltDrag on
  very few programs, then you just enable it on those programs.
  Both title|class and processes.exe styles are supported.
  Example: `Processes=*|*, explorer.exe, notepad.exe` will enable AltDrag
  only on the explorer and the notepad windows.
- New setting: UseCursor=4 in the [Advanced] section of AltDrag.ini,
  in order to use the ResizeAll cursor for movement instead of the Hand.
- New: Now more info are displayed in the Identify window section in the
  options to help debugging.
- New: Now the key used to transform scroll in Horizontal scroll can be
  chosen using the `HScrollKey` option in the `[Input]` section of
  AltDrag.ini. Default is 10, you can set an empty value to remove the
  ability of scrolling modification. Note that It only applies when the
  **Scroll inactive windows** option is checked.
- Fixed: When snapping to the top of the monitor in maximize mode, dragging
  the window to a corner would make a maximize-resized window instead of a
  snapped window.
- Fixed: now the snapping region when using Mimic Aero snap option will no
  longer extend beyond aero-threshold distance in the corners.
- Fixed: the **Lower windows with middle-clicking on title bars** as well
  as the **Roll/Unroll windows with <kbd>Alt</kbd>+<kbd>Scroll</kbd> on title bars** now work
  better and lets user closes the tabs on Sumatra PDF with middle click.
  The options also apply properly to MDI windows now.
- Fixed: now the center action will no longer apply to Maximized windows.
- Fixed Process blocklist not working on Windows 8.1
- Fixed: the cursor at the End of a movement would force the repaint of
  a 256x256 pixels around it. This is no longer the case.
- Fixed: Hotkeys list would not be read properly sometime.
- Fixed: Now windows focusing will work properly inside MDI windows.
  Also advanced mouse actions now work properly inside MDI.
- Fixed: now the `MMBLower` blocklist will only apply to the middle-click in
  the title bar and the normal restore option.
- Maximized-rolled window will now be restored to the pre-maximized state.
  Rolled-maximized-rolled-unrolled windows, will be restored to the first
  rolled state with the memory of the rolled state, as expected.
- Now the config dialog box no longer instantly applies the settings.
  This simplifies the code and is more desirable in my opinion. You now
  need to click OK or Apply in order to apply the settings. This also
  avoids useless confusion when compared to a normal property sheet.
- Fixed: Now Ctrl+<kbd>Alt</kbd>+<kbd>Click</kbd> will focus windows without needing to move
  them or to press Ctrl after the click.
- Fixed: Now the Max Aero Speed will also apply to top snapping.
- Fixed: now the application icon will display properly when <kbd>Alt</kbd>+Tabbing.
- Fixed: the Shift key was not working properly to enable snapping when
  all snapping was disabled.
- Fixed: a Rolled then double-clicked-snapped window will now be restored
  to its pre-rolled state, as expected.
- Fixed: The AltDrag icon is now properly displayed in <kbd>Alt</kbd>+Tab window.
- Better monitor handling on old windows.
- Other minor fixes and code improvement, leading to smaller exe.

### AltDrag 1.43

- New Wiki for AltDrag usage: <https://github.com/RamonUnch/AltDrag/wiki>
- New: An option to make the window translucent while dragging was added.
  See MoveTrans in the [General] section of `AltDrag.ini`. You can change it
  via the Advanced tab, using the opacity while moving option, from 1 to 254.
  Use 255, 0 or an empty value to disable (default).
- Now the `AeroMaxSpeed` calculus is based on a timer rather than the number
  of mouse frames. The time intervals for the measurement can be specified
  using the AeroSpeedTau variable in milliseconds in the [Advanced] section
  of AltDrag.ini (default 32ms). The max speed can now be specified in the
  Advanced tab of the config. Good values are around 10-100px/32ms. Use
  65535 or an empty value to disable (default). recommended: 64px/32ms.
- New: `SSizeMove` blocklist was added in the [Blocklist] section of the ini.
  Any windows added in this list will NOT receive the `WM_ENTERSIZEMOVE` and
  `WM_EXITSIZEMOVE` messages when moved or resized. This is useful for some
  buggy applications such as iTunes (default value is *|iTunes).
- New: AltDrag.xml file that can be imported from the Task Scheduler in
  order to setup auto start in elevated mode.
- Updated **Spanish** translation by **Carlos Sanchez**.
- Now an AMD64 build of AltDrag, can be compiled. builds are not provided
  because there are no real benefits for now (use mk64.bat).
- Removed dependency to `msvcrt.dll`. This avoids some mess and reduces the
  suspiciousness of the `AltDrag.exe` file to antiviruses. This also reduces
  the size of the exe.
- Fixed: Windows borders will now properly snap to taskbar on the second
  monitor. Instead of looking for the taskbars, I chose to look for the
  `rcWork` field of the monitor info that directly contains the area in which
  windows should be snapped. This also simplifies the code.
- Fixed: a snapped, then maximized window will be restored to its original
  size when alt-dragging it out of maximized state. If a windows like this
  is restored by double-click, then it will be restored to the previously
  snapped state and its normal position will be restored only when moving
  it out of its maximized state like expected.
- Fixed: Now the ESC key will always release Ctrl and Shift.
- Fixed: Added  the DEL key (2E) to the default Killkeys list.
- Fixed strange cropping bug that occasionally occurred with Chromium based
  Programs such as several Browsers and VSCode.
- Fixed potential segmentation fault in the `Enum` code.
- Fixed potential division by zero.
- Now all the memory should be unallocated when unloading hooks.dll. This
  avoids memory leaks of a couple of KB when disabling/enabling AltDrag.
- Fixed some occasional problem with snapping in older windows versions.
- Fixed: Now spaces can be added after a coma in a blocklist.
- Added StartMenuExperienceHost.exe,SearchApp.exe to the default process
  blocklist, thanks *@LittleboyHarry*.
- Added *|classFoxitReader to the default MDI blocklist.
- Minor code cleanup.

### AltDrag 1.42

- Now <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>Double-Left-Click</kbd> will minimize the pointed window.
- Avoid some more 'Stuck alt' bugs by better checking the key state.
- WARNING: The hot-click values have changed, check your configuration if you
  use mouse button to activate AltDrag.
- Now the Killkeys list also contains tle 'L' key (`4C`) by default, this will
  fix AltDrag problem if you use Win as a hotkey and use <kbd>Win</kbd>+L
- The MDIs blocklist was also updated with *|classFoxitReader.
- Improved the Roll/Unroll window action: now the file explorer windows will
  be really reduced to the title bar under Win10, until the user moves it.
- Re-introduced left and right control option in the GUI keyboard tab.
- Fixed: Process blacklists, now compatible with all versions of PSAPI.DLL.
- Fixed: The LowLevelMouseProc@12 should never have been exported by
  `hooks.dll`because it is only internally used. It does not change anything
  for the user but fixes potential vulnerabilities.
- Fixed: The scroll action is no more disabled on non-fullscreen windows
  when they have no system menu. It fixes problems with VS Code and Discord.
- Fixed: The cursor will no longer be unconditionally unclipped when
  releasing Shift or Ctrl keys.

### AltDrag 1.41

- Fixed compilation flags in the release build and Switched to NSIS 2.46
  and `TDMGCC`. to avoid false positives with some antiviruses. This also
  results in even smaller exe and dll.
- Minor dialog adjustment to help with russian language.
- More translation corrections and improvements from *Alexandr Smolnikov*,
  *Yatao Li* and myself.

### AltDrag 1.40

- NEW: Action menu can now be selected as a mouse action and will pop up
  a menu that let you chose a list of others actions.
  Thanks to *Yatao Li* (yalti) for implementing this action.
- New a kill action was added and can be activated with Ctrl+<kbd>Alt</kbd>+F4 or by
  using the Action menu, after activating the option. The Pause blocklist
  applies to this action.
- New Test Window that shows the resizing regions was implemented and is
  available in the Advanced tab (suggested by *redactedscribe*).
- Fixed: Some windows could not be created under older WinNT versions.
- Fixed: Now the windows registered by `hooks.dll`will be unregistered when
  unloading it (Under Win9x it was unnecessary, but we are under NT...).
- Fixed: Makefile mk.bat is now compatible with MingW's GCC 10.2
- More fixes to French Translation by *TroudhuK*.
- Russian translation improvement by *Alexandr Smolnikov* (bigcrush).
- Chinese translation improvement by *Yatao Li* (yalti).

### AltDrag 1.39

- New the LowerWithMMB option can now be set to 2 and you will need Alt to
  be pressed to lower the windows with middle click on title bar.
- New: An 'Enable on full screen windows' option was added in the advanced
  tab of AltDrag default is on like previous versions. A full screen window
  is a windows that fits exactly into the monitor and has no title bar.
- New/fix: A Killkeys list was added in the [Input] section of AltDragh.ini.
  It contains a list of key that will disable AltDrag when pressed down.
  Default value is 09 for the TAB key. This fixes a bug with DisplayFusion's
  <kbd>Alt</kbd>+Tab feature (Thanks *Daniele-f*).
- Fix: Made ESC key a bit more aggressive in disabling AltDrag.
- Minor refactoring and code cleanup, towards a more generic key mapping.
- Fixed French translation thanks *TroudhuK* and his very funny name...

### AltDrag 1.38

- GUI changed: Mouse and Keyboard are now separated tabs and contain more
  options. All the new options should be available. Have a look!
  Translation is supported but not updated outside of FR and IT.
- New: You can now invert the behavior of the shift key for double-right-
  click action (Resize) that aerosnaps or extends windows borders to monitor
  depending on the state of the Shift key. See the advanced tab.
- New: You can now set the Hotclicks variable in the [Input] section of the
  ini file to add the mouse buttons as hotkeys (hence the hot-click name).
  In the case the mouse button is also mapped to an action, the action will
  be performed on a single click. For example, you can set MB4=Move,
  MB5=Resize and Hotclicks=80 81 and the mouse 4/5 button will respectively
  Move/Resize the window without needing to press any other button or key.
  In all cases this click will not be usable for anything else than AltDrag.
  Action suggested by @displayerror.
- New Hotkey combo is now available. Set KeyCombo=1 in the [Input] section
  of AltDrag.ini and you will need to press two of the hotkeys in order to
  activate AltDrag. This was suggested by @MarqueIV.
- New: The keyboard can now be used to activate AltDrag without clicking.
  For example set GrabWithAlt=Move in the [Input] section of AltDrag.ini.
  Press Alt and the pointed window will directly be moved when moving the
  mouse without requiring a click. You can set any other action. I advise
  to use a hotkey combo for this feature or to use a very useless key on
  your keyboard. Action suggested by @pixelbase.
- New: A key can be set to toggle between move and resize action. it can be
  used in order to have a single click configuration that will turn into the
  other action when pressing this key. This later can be set with the
  ToggleRsMvKey in the [Input] section of AltDrag.ini. You can set it to A2
  for example and have Ctrl+<kbd>Alt</kbd>+LClick => Resize instead of Move. Leave it
  empty if you do not want this feature. Only one key can be specified.
  It can also be combined with a hotkey. You could for example use <kbd>Alt</kbd>+LClick
  to move and <kbd>Win</kbd>+LClick to resize with a single instance of AltDrag.
- New: The Ctrl key can be presses and released when a hotkey is on in order
  to prevent AltDrag from grabbing a window.
  Example: <kbd>Alt</kbd>+<kbd>Click</kbd> => Move window with AltDrag. <kbd>Alt</kbd>+Ctrl_down+Ctrl_up+<kbd>Click</kbd>
  Will be like a Simple <kbd>Alt</kbd>+<kbd>Click</kbd> without AltDrag running.
- Removed PearceDBClick option that was buggy and is now mostly unnecessary.
- Fixed: Now the doubleclick actions will check that the same button/key
  was used for both clicks.
- Fixed: Ctrl delay problem. Now <kbd>Alt</kbd>+Ctrl should not need to wait for the
  keyboard auto-repeat delay. It was a stupid bug sorry for that...
- Fixed potential bug in the hook chain.
- Changed the cursor window no longer capture the input as it should not
  be necessary and may lead to some bugs. The cursor code was also made a
  bit more conservative.

### AltDrag 1.37

- GUI New: now the Identify window option will show the program image name.
- GUI Fixed: re-introduction of the Advanced tab in the options with more
  options that previously required direct ini file edition. This should be
  helpful for all users. It is not yet translated though.
- Fixed: Now moveable full screen windows should be restored to full screen
  when changing monitor. This was not working properly in 1.36. Note that
  many full screen windows are really not moveable anyway.
  Under Windows 10 the file explorer will behave correctly, not Firefox.
- Fixed: the Scroll list was added in the [Blocklist] section of AltDrag.ini
  in order to disable the scroll action for any window. In addition the
  Processes blocklist will apply to scroll action as well.
- Fixed bug when the origin monitor was a NULL pointer in some cases under
  older windows versions.
- Fixed ini file: the proper name of the two settings about max aero speed
  are AeroMaxSpeed and AeroSpeedInt.
- Fixed: manifest file now fallback to per monitor dpi awareness version 1
  if version 2 is not available ie. Win 8.1 and Win10 before build 1703.
- More code cleanup, some code was moved to functions and potential NULL
  pointer dereferencing were fixed.
- GUI Fixed: Now the Snaplist has to be edited with the ini file and the
  Scroll blocklist is visible instead (much more useful). Snaplist is
  a quite advanced detail anyway.

### AltDrag 1.36

- Added MMMaximize option in the [General] section of `AltDrag.ini` in order to
  restore old AltDrag behavior (thanks brian6932):
  Set to 1 to maximize/restore on left+right click (default).
  Set to 2 to restore on a single left click instead of a drag.
  Set to 3 for both (like the original AltDrag).
  Set to 0 to disable any of those.
- Now the AeroMaxSpeed value can be set to put a speed limit beyond which the
  moved window will not be Aero-Snapped. This is useful to move windows
  between monitors without "flicker". You have to set AeroMaxSpeed and
  AeroSpeedInt in the [Advanced] section of AltDrag.ini.
  AeroMaxSpeed is in pixels/X frames (from 1-65535)
  AeroSpeedInt to specifies the number of frames (default 1) from 1-255.
  To set this value: (i) See the frequency of your mouse and set an
  AeroSpeedInt to average over 10ms or so, so if you have a 1kHz mouse,
  set it to 8-10, if you have a ~100Hz mouse (typical) keep it to 1 or 2.
  (ii) Set AeroMaxSpeed to a "high" value (like 50) and try to move fast
  a window between two monitors, if it get aero-snapped, decrease the value
  until it "just" no longer snaps. (iii) Check that the window does snap
  when you want it to sap, if the window tends to restore when you do not
  want, increase the AeroMaxSpeed value.
- Roll/Unroll action was added: It collapses the window in its title bar.
  It can also be used with the move action (<kbd>Alt</kbd>+<kbd>Shift</kbd>+DoubleLeftClick).
  You can also set RollWithTBScroll=1 in the [Input] section of your ini file
  to enable <kbd>Alt</kbd>+Wheel to roll/unroll window when pointing to their title bar.
  If not pointing to the title bar the normal Scroll action will be performed.
  If Ctrl is pressed the normal Scroll action will always be performed
- New: Now when using <kbd>Alt</kbd>+<kbd>Shift</kbd>+DoubleRightClick, the window will be extended
  to the corner/border of the monitor according to which area of the window
  was double clicked. <kbd>Alt</kbd>+DoubleRightClick works as before and Aero-snaps
  the window to the monitor sides/corners. Finally to Maximize a window you
  can use <kbd>Alt</kbd>+Ctrl+DBLeftClick on the center portion of the window (this is
  useful if you use a single button config with resize center set to "move".

- New: Now the AlphaDelta and AlphaDeltaShift value can be set into the
  [Advanced] section of AltDrag.ini to tune from -128 to +127 the step at
  which the transparency is changed when using the Transparency Action.
  Default is 64 and 8 with the Shift modifier. You can put negative values
  if you want to invert wheel Up/Down direction.
- Fixed/New: When Aero-snapping with AltDrag, the window can be restored
  via the title bar like normal. This is enabled if NormRestore=1 in the
  [General] section of AltDrag.ini.
- Fixed/New: Now a full screen window will be resized to full screen when
  moving it to a different monitor. If you want you can set ResizeAll=3
  to force move/resize of all full screen window. Keep in mind that some
  full screen windows are really not resizable (eg Firefox and Edge).
- Fixed: Now if MinAlpha is set to 0, it will be clamped back to 1, because
  setting to zero the alpha of a window disables any interaction with it.
  Everyone should also add ",Program Manager|Progman" to their windows
  blocklist (without the quotes).

- New: Improved the AltDrag.txt file, read it for some basic documentation.
- Fixed: cleaned up some code and corrected potential bugs, moved some more
  code into functions.
- Fixed: Now the AutoRemaximize option should always work.

### AltDrag 1.35

- Changed: to simplify the code and avoid bugs, the Ctrl is no longer
  suggested as a hotkey and if using it (using the ini file) other Ctrl
  functions will be unavailable (it was buggy in the first place anyway).
- Fixed a typo in the <kbd>Alt</kbd>+Tab scroll actions that lead to some bugs.
- Fixed: Ctrl in some cases does not work properly to retain window
  in current monitor and would be stuck sometime (thanks redactedscribe).
  To avoid those problems that are specific to Ctrl, the Shift key can now
  be used to restrict cursor to current monitor when dragging a window.
- Fixed: When adding a monitor, AltDrag needed a restart for Aero Snapping
  to work properly, this is no longer the case.
- Fixed .manifest file so that proper windows version can be obtained.
- GUI fixed: Now under Windows 10, the 'scroll inactive window' option will
  be grayed out unless it is activated, so that users do not enable it by
  mistake and to make it clear that it is useless for Win10.
- GUI Fixed: Now if desktop composition is enabled, it will no longer be
  possible to disable the Drag Full Window option (GDI Performances problem).

### AltDrag 1.34

- Added MMBLower in the [Blacklists] section of AltDrag.ini in order to
  disable the "Lower windows by middle clicking on the title bar" option
  for any window. use the name|class format.
  Example: MMBLower=*|CASCADIA_HOSTING_WINDOW_CLASS
  if you want to close tabs with middle click on Windows Terminal.
- Fixed: now the Lower action will deselect the lowered window if possible
  so that it can be reselected easily (thanks redactedscribe).
- Fixed: Now when a windows is snapped normally under windows,
  it will be restored properly if AltDragging it out. If a window is
  snapped with AltDrag, however it can only be restored with AltDrag.
- Fixed: Scroll Action was restored to the 1.29 version behavior (@kimks3).

### AltDrag 1.33

- Added a MinAlpha option in the [Advanded] section of AltDrag.ini, in order
  to adjust from 0 to 255 the minimum opacity of a windows (default is 8).
- Fixed AltDrag freezing when changing DPI scaling or going to sleep mode.
- Fixed Stupid bug that would restart AltDrag wen moving windows between
  monitors with different DPI scaling.
- Improved English on the snapping windows option (thanks redactedscribe).
- Now settings should be kept when updating AltDrag (thanks @Sund).

### AltDrag 1.32

- Added the PearceDBClick option in [Advanced] section of Altdrag.ini.
  Use 1 to disable the maximize on <kbd>Alt</kbd>+double-click. It only applies to
  the Move action for now, maybe more will come if needed.
- Added the UseCursor option in the [Advanced] section of AltDrag.ini
  Use 0 to disable any cursor handeling (not recommended).
  Use 1 to enable all cursors changes (default).
  Use 2 to disable only the Hand cursor when dragging a window (icyhoty2k).
  Use 3 to always use the default cursor, even when resizing.
  Note that none of those settings is expected to affect performances in
  any significant way.
- Now when pressing the SHIFT key while using doubleclick snapping on the
  center-top section of the window, this later will be maximized/restored,
  instead of being snapped to the top. This will be usefull when using
  the Move instead of resize-center option.
- Lower with Middle mouse button option will no longer ignore the window
  blocklist, this will avoid interactions with taskbar.
- Fixed Scroll inactive windows, hopefully for real this time.
- Avoid some more lookup in the case of very unresponsive windows by using
  PostMessage instead of SendMessage, when applicable.
- Fixed: Now doubleclick snapping will respect Aero(H/V)offset settings.
- Fixed some more minor drawing problems when using FullWin=0

### AltDrag 1.31

- Added option to replace the resize center mode with Move mode.
  GUI was adjusted accordingly
- Improved the non full windows dragging mode, it will no longer move the
  window when it snaps but only the transparent square and the window will
  be moved when click is released as expected.
- Simplified window database and removed useless code.
- Fixed slightly too large window when resizing from a maximized window
  inside an MDI.
- Fixed some annoying behavior in the in case of unresponsive windows.

### AltDrag 1.30

- Re-introduced the Aero snap at top to maximize a window. this behavior can
  be disabled with the AeroTopMaximizes option in the [Advanced] section of
  AltDrag.ini. The Shift key will also invert the behavior.
- Now when auto re-maximize option is on, the re-maximizing can be prevented
  by pressing the shift key before releasing the mouse.
- Fixed overcompensation of Win10 invisible borders in center mode in the
  case of double click Aero-snapping.
- Fixed horizontal double-click Aero-snapping maximization in the case of
  MDI windows.
- Fixed: Now the Volume action is not limited to Vista and later. This later
  will use the WINMM API on NT4/2000/XP to change the waveOut volume.
- Fixed the Scroll inactive windows option, that would prevent scrolling
  in all metro apps under Win 10. Note that I advise against using this
  option anyway because Win 10 does it already natively by default.
- Now "Start|Windows.UI.Core.CoreWindow" is in the default blocklist.
  This will avoid AltDrag interactions with Win10's Start menu.

### AltDrag 1.29

- Added Maximize scroll action that behaves as expected: wheel up maximize
  the pointed window, wheel down restore a maximized window and minimize to
  taskbar a normal window. This action was proposed by bluebird11.
- Now when Aero-snapping with double right-click, the window will be resized
  to full monitor width when double-clicking on the center of the window
  while pressing the shift key.
- The cursor is now properly limited to MDI client area when using Ctrl.
- Cleaned up some code by removing useless global variables.
- Lower action will no longer ignore the AutoFocus config flag.
- Minor refactoring, moved some code toward function and fixed some gcc's
  -Wsign-compare warnings.
- Fixed: Sometime when pressing escape while resizing, it would prevent
  further window move/resize.
- Rewrote the auto remaximize procedure. It is now much simpler and handier
  in my opinion. The window is now re-maximized when released on the current
  monitor, if it was maximized when move started AND was dragged to an other
  monitor. There is no more 1s delay option...
  Note this procedure was not working properly on previous releases.
- Fixed: Position of the mouse cursor relative to the restored windows
  should be always correct now, this was a stupid bug I introduced...
- Fixed: Desktop window is now properly ignored.
- Fixed: When using Ctrl, the cursor will be properly restricted to the
  current monitor.
- Removed unused variables and cleaned up some code.
- Remove hard dependency to ole32.dll, it will be loaded only when using
  the Volume action.

### AltDrag 1.28

- Added hardening flags for gcc.
- Added a RefreshRate in the [Performance] section of AltDrag.ini that
  allows you to set a minimum time in milliseconds between two Windows
  Redraw when FullWin=1, I recommend a value that corresponds to the
  refresh rate of your monitor ie: 60Hz => RefreshRate=16.
- Added Maximize action, it can be used to toggle the maximized state,
  combine with Shift to minimize. (Thanks to Jim Teunis for suggestion).
- Added the CenterFraction in the [General] section of AltDrag.ini to adjust
  The size of the region in percent that is used for the center resizing
  mode. Default is 24% meaning 38% for the sides. You can, for example set
  it to 0 to enable a 4 regions mode instead or the 9 default regions.
  You can also set CenterFraction=100 and combine with the ResizeCenter=0
  option in order to have a pure bottom right mode.
- Added AeroThreshold option in the [Advanced] options. Default value is 5.
  It corresponds to the threshold distance in pixels at which a window will
  be snapped automatically to the monitor (aero style). If you do not like
  windows snapping for a fraction of second when changing monitors, try to
  set this value to only 2, in such a case it will be necessary to use Ctrl
  to snap windows between monitors. On the other hand if you want you can
  increase this value and this will make snapping between monitors easier
  without Ctrl key...
- Removed dependency to Advapi32.dll from `hooks.dll`(it was unnecessary).
- Fixed: An Aero-snapped window will now require mouse movement before
  moving, instead of a simple <kbd>Alt</kbd>+<kbd>Click</kbd>.
- Fixed when a window is in full screen you will actually need to move the
  mouse in order to resize it.
- Fixed a remaining Win 10 invisible borders bug that would shrink slightly
  a window when resizing it from a full screen state.
- Fixed application hang when changing DPI scaling under Win10. Note that
  for the moment the solution is to restart AltDrag when receiving the
  WM_DPICHANGED message, I hope to have better solution in the future.
- Fixed bug in Transparency action where the windows transparency could no
  longer be modified in some cases.
- Misc. cleanup and code refactoring here and there + Fixed all warnings.
  using gcc -Wall parameter.
- Minor GUI improvement for WinNT4 and Win2000.

### AltDrag 1.27

- Added Elevate option to the tray menu as suggested by Loxaan Oxyde.
- Added Pause Process option, use <kbd>Alt</kbd>+<kbd>Shift</kbd>+<kbd>Pause</kbd> to pause the process
  of the windows under your cursor, press <kbd>Alt</kbd>+<kbd>Pause</kbd> to Resume.
  The Option AgressivePause must be set to 1 in [Input] config.
  Use the associated Pause blocklist. This function needs XP or later.
  Note 1: This is a very aggressive option use with caution.
  Note 2: The windows of the paused process will no longer be drawn leading
  to screen tearing on the windows itself.
  Note 3: If you use WIN as a hotkey, then you can still obtain the
  WIN+PAUSE System Properties by pointing first the cursor to the taskbar.
- Now when using Aero Snap, and resizing towards the top, the windows will
  be maximized vertically when the cursor will touch the top of the screen.
  Same behavior for the left. This behavior is ONLY for the top and left
  when using respectively the pure top and pure left resize modes.
- Actually fixed DPI scaling under Win10 with the .manifest I made a typo
  in the first place and never fixed it, because I was not using DPI scaling
  and I thought I was...
- Fixed the toggle borderless action under Windows 10, the window would
  not be properly refreshed because of buggy DWM.
- Fixed: Now the Transparency action will not ignore blacklists.
- Improved translation handling, now all translations are ini files in the
  "languages" subdirectory of AltDrag. This will simplify addition of new
  Locals, this also allow anyone with notepad to fix his own language.
  Finally you can remove languages that you donot need and if you want only
  english you can remove the whole "languages" directory.
- Updated zh_CN.ini (Chinese) with Zepp Lu's corrections
- More French and Italian corrections.

### AltDrag 1.25

- Fixed Memory leaks.

### AltDrag 1.24

- Fixed crash in the config dialog.
- Fixed: Some windows such as mplayer's windows can now be resized again.
- Fixed translations in French and Italian in particular.
- Fixed Incorrect snapping of windows in an MDI under Windows 10.
- Fixed: Now on a blocklist, an empty title will be considered as a really
  empty title instead of 'any' title. You should use '*|class' to include
  all windows from a given class instead of just |class. This gives a more
  fine control over blocklist to the user.
- Fixed minor drawing problems when using FullWin=0

### AltDrag 1.23

- Add option to disable resizing windows that are not resizable
  ie: No WS_THICKFRAME. Default is to resize everything.
- Fixed: Now config dialog can be used on NT4.
- Fixed: Now AeroSnap takes into account the taskbar on NT4.
- Fixed: Now when a window is not responding, move/resize will be disabled.
- Some optimizations were done.
- Fixed: Windows will be moved/resized in an independent thread avoiding any
  mouse delay/lockup when a window is very unresponsive. This is helpful for
  Slow video drivers on Win8/10, and for web browsers windows.

### AltDrag 1.22

- Added options to choose the Aero Snap ratio. You can now chose the position
  in percentage of screen size, where the AeroSnap corners will meet.
  Default is 50%:50% ie:
  AeroHoffset=50 ; Horizontal from left
  AeroVoffset=50 ; Vertical from top
  You could set for example AeroHoffset to 33, this mean that a windows
  snapped to the left will use only 33% of the screen and a window snapped
  to the right will use 67%. The same logic applies to AeroVoffset for the
  vertical direction. This will be appreciated by the widescreen users.
- Added toggle window title bar and border on/off Action (Igor Bochkariov)
  I used a different implementation though. If you want to just disable the
  titlebar and keep borders, press shift.
- Fixed Transparency action. Now when setting back the windows to an opaque
  state, the WS_EX_LAYERED attribute is removed as it should be. This will
  avoid useless performance issues when using this feature
- Fixed: Now under Windows 10, the DWM API will be used when available to
  obtain correct window rectangle and avoid gaps between snapping windows
- Fixed: now full screen windows that have a system menu will not be
  automatically blacklisted.
- Now a full screen window will not be restored unless the mouse is moved
  instead of a simple <kbd>Alt</kbd>+click as before. It was an annoying behavior.
- Double click will maximize a normal window and restore a maximized window.

### AltDrag 1.20

- Ability to drag only a square instead of the full windows (better perf.)
- Added an option to replace center resizing mode by bottom-right mode.
- Added MDIs blocklist: Windows for which MDI behavior will be disabled.
- No more HookWindows as (unstable and mixing 64 and 32 bit code)
- No more FocusOnTyping (too buggy).
- No more auto updates and internet connectivity.
- Fixed cursor performances problems, before the cursor windows used alpha
  blending which is very slow. I just told the windows to do nothing when
  it receive the `WM_PAINT` or `WM_ERASEBKGND` messages and that's it, this also
  means proper display for all windows versions instead of being limited to
  Windows 2000+
- Now compatible with Windows NT4 sp3+
- Removed dependencies to `shlwapi.dll`
- Removed dependency to `WININET.DLL`
- Dynamically import `PSAPI.DLL`in case it is missing (it is not much used)
- Fixed: Cursor windows now captures the mouse input (prevents some bugs).
- Fixed completely opaque blocklist reading procedure, it will be trivial to
  add or remove blacklists from now.
- Fixed some drawing problems (not all).
- Fixed .manifest information for high dpi awareness.
- Refactoring by putting some code into functions
- Use GetPrivateProfileInt instead of the 'String version for all int values.
- Avoid floating point arithmetic. Only integer math are used.
- Add `-nostdlib` flag to gcc to avoid useless bloat to the dll and exe.
- Avoid GUI locking when windows is very slow to resize (with FullWin=0 only)

## OS Requirement

AltDrag should work on NT4sp3+/2000/XP/2003/Vista/7/8.x/10/11.
Also works on ReactOS (little testing).

This program needs at least Windows NT4 service pack 3 or later.
This is because it relies on the 'LowLevel Keyboard/Mouse Proc' functions
that is only supported by the NT based Windows and from NT4 sp3. You will
note that the program also depends on 'SendInput()' that appeared at the
same time. This later dependency is not necessary but is convenient.

== END OF FILE ==