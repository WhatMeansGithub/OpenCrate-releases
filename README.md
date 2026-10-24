# OpenCrate user manual

OpenCrate (formerly Krate) is a DJ library manager for macOS and Windows. It reads your
**Rekordbox** and **Engine DJ** libraries, syncs playlists, cues and
beatgrids from Rekordbox to Engine DJ, and cleans up messy track info and
files so they work on every player.

> **Alpha version.** OpenCrate is early software. It backs up your libraries
> before every change, but please keep your own backups as well, and tell
> us about anything that looks wrong.

---

## Contents

1. [Installing](#installing)
2. [How OpenCrate keeps your library safe](#how-krate-keeps-your-library-safe)
3. [Getting started](#getting-started)
4. [Library: browsing your tracks](#library-browsing-your-tracks)
5. [Sync: Rekordbox to Engine DJ](#sync-rekordbox-to-engine-dj)
6. [Tidy: cleaning up your library](#tidy-cleaning-up-your-library)
7. [Backups: undoing changes](#backups-undoing-changes)
8. [Settings](#settings)
9. [The status bar](#the-status-bar)
10. [Not in OpenCrate yet](#not-in-krate-yet)
11. [Reporting problems](#reporting-problems)

---

## Installing

Download the file for your computer from the
[releases page](https://github.com/WhatMeansGithub/OpenCrate-releases/releases):

| Your computer | File |
|---|---|
| Mac with Apple Silicon (M1 or newer) | `OpenCrate_…_aarch64.dmg` |
| Mac with an Intel processor | `OpenCrate_…_x64.dmg` |
| Windows | `OpenCrate_…_x64-setup.exe` |

Not sure which Mac you have? Apple menu → **About This Mac**: "Chip: Apple
M…" means Apple Silicon, "Processor: Intel" means Intel.

These builds aren't signed yet, so the first launch needs one extra step:

- **macOS:** open the `.dmg` and drag **OpenCrate** into **Applications**. If
  macOS says OpenCrate can't be opened, go to **System Settings → Privacy &
  Security**, scroll down and click **Open Anyway**. (Or right-click OpenCrate
  in Applications → **Open**.) If macOS instead says OpenCrate "is damaged",
  open **Terminal** and run `xattr -cr /Applications/OpenCrate.app`, then open
  OpenCrate again.
- **Windows:** run the installer. If SmartScreen warns about an unknown
  app, click **More info → Run anyway**.

### Updating OpenCrate

OpenCrate updates itself. When a new version is out, a blue banner at the top
offers it: **Download update**, then **Restart and update**. Or choose
**Skip this version** or **Later**. **See what's new** in the banner shows
what changed in that version before you install it; the pop-up links to
the release on GitHub. After updating, a small banner says so, again with
**See what's new** (any time later: Settings → About → **What's new in
this version**). Updates are signed, and OpenCrate only
installs updates that come from OpenCrate's own releases. OpenCrate never restarts
by itself, and you can't restart while it's writing to a library. How OpenCrate
handles updates is set in [Settings](#settings).

(Keep OpenCrate in your Applications folder on a Mac; updates can't replace a
copy that's still on the disk image.)

---

## How OpenCrate keeps your library safe

- **Reading never changes anything.** OpenCrate reads your DJ libraries from a
  copy and never modifies them just by looking.
- **Backups before every write.** Before OpenCrate changes a DJ library
  (syncing, Tidy, restoring), it makes a backup and checks that the backup
  is complete. Before it changes an audio file's tags, it backs up that
  file's tags and artwork (or the whole file, see [Settings](#settings)).
- **Only while the DJ app is closed.** OpenCrate won't change Rekordbox's or
  Engine DJ's library while that app is open. The
  [status bar](#the-status-bar) shows when an app is open.
- **Checked after writing.** After writing to a library, OpenCrate checks the
  database is intact and the values read back correctly. If not, it puts
  the backup back automatically.
- **Your music is never deleted or re-encoded.** OpenCrate only edits tags
  (title, artist, …); the audio itself is never touched.
- **Everything can be undone** from the [Backups](#backups-undoing-changes)
  tab.

---

## Getting started

When you first open OpenCrate, it looks for your libraries in their usual
places:

- **Rekordbox** (6 and 7): your Rekordbox library on this computer.
- **Engine DJ**: the `Engine Library` folder in your Music folder.

Click **Import Rekordbox library** or **Import Engine DJ library** (later on, these buttons are at the top of the window). Under
**Other…** you can import a **Rekordbox XML** export or an Engine Library
folder somewhere else (for example on a USB drive).

You can import several libraries; pick one in the sidebar. Imported
libraries update themselves: every time OpenCrate starts, when you switch
back to OpenCrate's window, and after a sync, Tidy or restore, it re-reads
any library that changed.

Each time OpenCrate starts, it also looks for DJ libraries on this computer
that aren't in OpenCrate yet. If it finds one, a banner at the top offers to
add it (with several, tick the ones you want). **Not now** asks again next
time; tick **Don't ask again** to stop being asked about it. You can undo
that in Settings → General.

---

## Library: browsing your tracks

- The **sidebar** lists your imported libraries and their playlists and
  folders. The small number in front of a playlist is how many tracks it
  has. Click a playlist to show its tracks; click the library name for all
  tracks.
- **OpenCrate's own library** is always at the top of the sidebar, even
  before you import anything. It's where music comes in without Rekordbox
  or Engine DJ. Click the **+** on its row (or right-click it) for **New
  playlist…**, **New folder…**, **Add files…** (songs), **Add folder…**
  (everything inside, any depth) and **Add folder as playlist…** (also
  makes a playlist named after each folder). Right-click one of its
  playlists (or click its **+**) for **Add files here…** and **Add folder
  here…**, which put the music into that playlist (and into the library,
  if it isn't there yet), **Rename…** and **Delete playlist…**.
  You can also drag tracks from your Rekordbox or Engine DJ library onto
  one of its playlists (the track is copied into OpenCrate's library,
  without its cues and grid). Inside OpenCrate's library you can drag tracks onto its playlists,
  remove them from a playlist (**Remove from playlist**, ⌫) and drag them
  to reorder, as in your DJ libraries. MP3, M4A, WAV, AIFF and FLAC files
  are added; title, artist, album, genre, year, length and bitrate are
  read from the file's tags (a file with unreadable tags still appears,
  named after the file). The files themselves are never changed or moved,
  and a song that's already in OpenCrate's library isn't added twice.
  Removing the library with **×** deletes only its list (tracks and
  playlists), not your music. Add music with the **+** menu (or a
  playlist's **+**), or drag files and folders in from Finder or Explorer
  (folders become playlists). Drop them on an OpenCrate playlist or on
  the OpenCrate library in the sidebar (the row lights up), or anywhere
  else to add them to the playlist that's open. For now these tracks can be browsed, searched and played;
  analysing them and sending them to Rekordbox, Engine DJ or a USB stick
  comes next.
- **Devices:** a plugged-in USB stick with a Rekordbox export or an Engine
  DJ library shows under **Devices** in the sidebar, with its free space
  and an **⏏** button to eject it. Browse its Rekordbox and Engine DJ
  playlists and tracks like a library. Sticks are read-only here (change
  your library on the computer, then export); to bring a stick's playlists
  into your library, see [Importing from a USB stick](#importing-from-a-usb-stick).
  A stick leaves the sidebar when it's ejected or unplugged.
- **Selecting tracks:** click a track to select it, **⌘-click** (Ctrl-click
  on Windows) to add or remove one, **Shift-click** to select everything
  between it and the last one you clicked. Ratings keys, **Remove from
  playlist**, dragging onto a playlist and dragging to reorder work on all
  selected tracks.
- **Played tracks:** a track you've played in OpenCrate's player shows in
  green in the track list (amber in the Winamp theme), wherever it
  appears, until you quit OpenCrate.
- The **search** box filters by title, artist, album, genre, label and comment.
- Click a **column header** to sort. Drag a header to move its column,
  and drag a header's right edge to make the column wider or narrower
  (double-click the edge for the standard width). **Right-click the
  headers** to show or hide columns (a ✓ marks the ones shown; Title is
  always shown), or choose **Reset columns** to go back to the standard
  layout.
- **Rating:** click a star to rate a track (click the same star again to
  clear it), or select a track and press **1**–**5** (**0** clears). The
  rating is saved into the library you're viewing (backed up first;
  ratings you set quickly one after another are saved together), and
  that app must be closed. Your other libraries get it when you sync, or
  straight away if the library you're viewing is the **primary library**
  (Settings → Sync).
- **Playlists** (Rekordbox's own library and Engine DJ): hover over a
  library, folder or playlist in the sidebar and click **+** for **New
  playlist…** or **New folder…** (in a library or folder it goes inside;
  next to a playlist it goes right below it, in Rekordbox; Engine DJ adds
  it at the end). Right-click a playlist or folder to **Rename…** or
  **Delete…** it (its tracks stay in the collection). Drag tracks from the
  list onto a playlist to add them, or right-click a track and choose
  **Add to playlist ▸** (folders open as submenus; tracks a playlist
  already has aren't added twice); inside a playlist, right-click a track
  for **Remove from playlist**. Both work on all selected tracks. **Drag to reorganise:** drag a playlist
  or folder onto a playlist to put it right below, onto a folder to put
  it inside, or onto the library name to put it at the top; inside a
  playlist sorted by **#**, drag a track up or down to move it. **Delete**
  (or Backspace) removes the selected tracks from the playlist, or deletes
  the selected playlist in the sidebar, after asking; **⌘-Delete**
  (Ctrl-Delete on Windows) does it at once, as in Rekordbox (drop it in the empty space below the list to move it to the end). Changes are saved into that library
  (backed up first; the app must be closed), and into your other
  libraries too if it's the primary library (Settings → Sync). Edits
  show at once and are saved in the background, in order; if one can't be
  saved (e.g. the app is open), OpenCrate says so and puts the playlists back
  as they are in the library.
- **Format** shows the file type (MP3, AIFF, WAV, FLAC, …). **Bitrate** and
  **Label** are hidden at first; turn them on with a right-click on the
  headers.
- Drag the **sidebar's right edge** to make it wider or narrower; drag it
  far to the left, or click **‹** next to "Libraries", to hide it. Click
  the thin strip with **›** to bring it back. OpenCrate remembers the layout.
- A faint **waveform** behind each title shows the track's shape at a
  glance (from Rekordbox's or Engine DJ's own analysis; tracks that haven't
  been analysed show none).
- **Album art** has its own column at the left: the cover embedded in the
  audio file, read when the row comes into view (tracks without one show an
  empty square). Decks show the cover next to the track title; hover over
  it to see it bigger. Settings → Appearance → **Show album art** turns
  covers off everywhere.

### Playing tracks

Load a track into a deck at the bottom of the window by:

- **dragging** it from the track list onto a deck (its waveform or its
  controls),
- **right-clicking** it and choosing **Load to Deck A** or **Load to
  Deck B** (Deck B switches the player to two decks), or
- **double-clicking** it (deck A, or deck B while A is playing).

If the deck is playing, OpenCrate asks before replacing its track. Playback
keeps going while you switch tabs.

Click **Player** (top left of the player area) to minimize it to one line,
and again to open it. Minimized, each loaded deck shows ▶ / ❚❚, its title,
the time and a thin overview of the track (click to jump; you can drop
tracks on it too); with nothing loaded the line stays empty. Settings →
Player & mixer chooses how the player starts and whether it minimizes on
other screens.

Choose the player at the top right of the player area:

- **1 deck:** the big waveform with all of the deck's controls in one row
  below (it wraps onto a second row in a narrow window).
- **2 decks:** both decks' waveforms stacked on top of each other (A above
  B, like Rekordbox), with the two decks' controls side by side below.
  **Load selected** loads the track selected in the list into that deck.
  Switching back to 1 deck while deck B plays asks first, then stops
  deck B.

On a deck:

- **Waveform:** scrolls past the white playhead in the middle. Bar lines
  are bright, beats are short ticks. Hot cues show as coloured flags with
  their letter, memory cues as red triangles at the bottom, saved loops as
  shaded areas, the cue point as an orange triangle. The zoom control in
  its top right corner shows how many seconds are on screen; the
  magnifier with **+** zooms in, the one with **−** zooms out.
- **Scratching:** hold the waveform and drag. The track follows your hand
  like a record, forwards and backwards; let go and it plays on (if it was
  playing). A click without dragging jumps to that spot.
- **Overview:** the whole track below; click to jump.
- **CUE** works like on a CDJ: while playing, it jumps back to the cue
  point and stops. Stopped at the cue point, **hold** CUE to play from it;
  release to jump back. Press ▶ while holding CUE to keep playing. Stopped
  anywhere else, CUE sets the cue point there. A loaded track starts at its
  first memory cue; if it has none, where the sound starts (snapped to the
  nearest beat), like Rekordbox's auto cue.
- **▶ / ❚❚:** play and pause.
- **Hot cues A–H:** the thin bars at the top of each deck's controls. A
  bar lights in the cue's colour (with its name, if it has one) when the
  track has that hot cue; click it to jump there and play. Click an empty
  bar to set that hot cue where the deck is. Right-click a hot cue to delete
  it, move it to where the deck is, change its colour, or name it.
- **◁ MEMORY ▷:** **MEMORY** stores a memory cue where the deck is (when
  stopped, that spot also becomes the cue point). If there's already a
  memory cue there, it goes to it instead of adding a second one. ◁ and ▷
  jump to the previous or next memory cue and make it the cue point.
  Parked on a memory cue, the button reads **DELETE** and removes it.
- **Loops (IN · OUT · RELOOP · ½ · 4 · ×2):** **IN** marks where a loop
  starts, **OUT** loops from there to where the deck is now (while looping,
  OUT moves the loop's end). **EXIT** leaves a playing loop and plays on;
  **RELOOP** goes back to its start and loops again. The number is the auto
  loop: click it to loop that many beats from here (click again to leave
  the loop); **½** and **×2** halve or double the playing loop, or pick a
  smaller or bigger auto loop (1/4 to 32 beats). The loop shows as a green
  area on the waveform and the overview (grey once you've left it). Loops
  stay seamless with Master Tempo on. Jumping somewhere outside the loop
  leaves it.
- **Q (quantize):** new hot cues, memory cues and loop points snap to the
  nearest beat, and jumping to a hot cue while playing keeps the beat (it
  lands as far past the cue as the deck was past its beat). OpenCrate
  remembers the setting.
- **CUES:** the track's cues and saved loops in time order (the number is
  how many it has): hot cues A–H, memory cues (**MEM**) and loops with
  their length. Click one to go there (stopped, it becomes the cue point; a
  loop starts looping). Type in the name field to name it (Enter saves,
  Esc cancels), click the colour square to change the colour, × deletes
  it. **Save loop** keeps the deck's current loop with the track. Loops
  from Rekordbox show the hot cue pad they sit on (**A ⟳**), Engine's their
  loop pad (**L1**–**L8**). **Done** closes the list.
- **GRID:** beatgrid tools, shown instead of the mixing tools: **‹ ›** move
  the grid 1 ms earlier or later (**« »** 10 ms), **Beat 1 here** makes the
  playhead the first beat of a bar, and the tempo box sets the grid's BPM
  (type a value and press Enter, or use − / + for 0.01 BPM, **½** / **×2**).
  Changing the tempo makes the grid steady, keeping the beat nearest the
  playhead in place. Sync and the phase meter follow the edited grid.
  **Done** goes back to the mixing tools.
- **EDITED:** appears while a track's changed cues, loops or grid aren't
  in your DJ library yet (they're saved into it on their own; see
  [Saving cue and grid edits](#saving-cue-and-grid-edits)). Click it to go
  back to the library's own cues, loops or grid.
- **Volume:** the deck's volume, in percent.
- **EQ:** the bands of the mixer chosen in Settings →
  Player & mixer, highs on the left. As knobs: drag up or down (hold Shift
  for fine steps), or scroll; double-click puts a knob back in the centre.
  As kill buttons: a lit button cuts its band. Bands that fully kill on the
  real mixer go silent when turned all the way left; the others stop at the
  mixer's cut (for example −26 dB on Pioneer mixers). The ring lights blue
  while a band is cut and red while it's boosted.

Below that, the beatmatching tools:

- **SLOW / FAST (pitch bend):** hold to slow the deck down or speed it up
  by 4 %, to push it into time with the other deck.
- **Tempo fader:** drag the fader cap (or anywhere along the fader; hold
  Shift for fine steps), scroll, or use the arrow keys. It clicks into
  place at 0 %, where the green light above the middle comes on;
  double-click to go back to 0 %. The percentage shows underneath.
  **±8%** next to it switches the range (±8, ±16, ±50 %). The BPM in the
  deck's top row shows the tempo it plays at now.
- **MT (Master Tempo):** keylock. With it on, changing the tempo keeps the
  key; with it off, the key rises and falls with the tempo like a record.
- **Key:** the key the track sounds in now. **−** and **+** shift it by a
  semitone; click the shifted key to reset it. OpenCrate shows keys the way
  your library writes them (Am, 8A or 1m).

With 2 decks you also get:

- **SYNC:** match the master deck's tempo and lock onto its beats. The
  deck jumps onto the master's beat when it starts (or when you press SYNC
  while both play) and then stays locked. Its tempo fader follows the
  master. Nudging a synced deck moves it off the beat; sync keeps the
  offset you chose, useful when a beatgrid is slightly off. Tracks at half
  or double the tempo (70 against 140 BPM) sync too.
- **MASTER:** the deck that synced decks follow (lit orange). The first
  deck you load becomes the master; pressing SYNC with no master makes the
  other deck the master. Loading a new track into the master deck passes
  the master to the other deck (if it's synced or playing), so that deck
  keeps its tempo, as on CDJs.
- **Phase meter** (the small bar next to MASTER): where this deck's beat
  falls against the master's. The dot sits in the middle (and turns green)
  when the beats line up; left means behind, right means ahead. It works
  without SYNC too, for beatmatching by hand.
- **KEY SYNC:** shifts the deck's key to fit the master's, either the same
  key or its relative major/minor (the same Camelot number), by the
  smallest step. It turns Master Tempo on.

Sync and the phase meter need a beatgrid on both tracks. In 2 decks, the
waveforms scroll at real time: two decks at the same BPM show their beats
the same distance apart, so you can see whether they line up.

Cue points and beatgrids come from the library the track belongs to, and
line up with the audio for both Rekordbox and Engine DJ libraries.

---

## Sync: Rekordbox to Engine DJ

Sync copies your Rekordbox playlists, tracks, cue points, loops and
beatgrids into Engine DJ, so you can play the same library on Denon
gear.

Sync has two parts, switched at the top: **Libraries** (described here)
and **USB stick** (see below). Cue and grid edits from OpenCrate's player
don't need a sync: they're saved into your libraries on their own.

1. **From:** your Rekordbox library (or a Rekordbox XML export).
   **To:** your Engine DJ library. OpenCrate finds both automatically; use
   **Change…** to pick another location.
2. **What:** the **full library**, or only the **playlists** you tick.
3. **Mode:**
   - **Merge** (recommended) adds what's missing and never removes anything
     from Engine DJ.
   - **Rewrite** makes Engine DJ's playlists match Rekordbox exactly:
     playlists and entries that aren't in Rekordbox are **removed**.
4. **Cues & beatgrids:**
   - **Cues:** hot cues, memory cues, or both. Engine DJ has no memory cues,
     so they go into free hot cue slots.
   - **Overwrite cues & beatgrids on tracks Engine already has:** off by
     default, so cue points you set in Engine DJ are kept and only empty
     slots are filled.
   - **Keep duplicate cues:** keep cues at the same position as an existing
     one.
   - **Lock beatgrids** so Engine DJ doesn't re-analyse them.
5. Click **Preview changes**. OpenCrate lists exactly which tracks and
   playlists will be added, changed or removed. Nothing has been written
   yet.
6. Click **Sync now** to write it. Engine DJ must be closed.

Cue points line up exactly between the apps, including the small timing
difference Rekordbox and Engine DJ have with some MP3 files.

**Syncing again.** OpenCrate remembers what both libraries held after each
sync, so the next one knows what you changed where since then (track
info, ratings, cues, loops and beatgrids), and applies it without asking:

- Changed in **Rekordbox**: copied to Engine DJ, even in Merge mode (it's
  an edit, not a gap to fill). The track list says what changed, e.g.
  "info rating".
- Changed in **Engine DJ**: with **Two-way** ticked (the default when
  syncing from Rekordbox's library), copied back into Rekordbox: track
  info, ratings, hot cues and beatgrids. Only the fields you changed are
  written; Rekordbox's memory cues stay. Rekordbox is backed up first and
  must be closed. Loops changed in Engine DJ stay there for now.
- **Playlists** made or changed in **Engine DJ** (with Two-way): new
  playlists and folders are created in Rekordbox with Engine DJ's tracks
  in its order; tracks added or moved in Engine DJ are added or moved in
  Rekordbox (tracks you removed in Engine DJ stay in Rekordbox); a
  playlist renamed in Engine DJ is renamed in Rekordbox. Tracks that
  aren't in Rekordbox's collection are left out. A playlist changed in
  both apps keeps Rekordbox's version; one deleted in Engine DJ isn't
  deleted in Rekordbox.
- Changed in **both**: the newest change wins (each app records when it
  last edited a track). When an app doesn't say, or if you chose **Ask
  me** in Settings → Sync, the track is listed under **Changed in both
  libraries**: pick **Copy Rekordbox's** or **Leave Engine DJ's**, and the
  preview updates. Undecided ones aren't written and come up again next
  time.
- Cues or loops **removed** in one app stay in the other.
- **Probably the same track, moved:** tracks that look like a moved copy
  of one OpenCrate knows (same size, length, artist and title). They're only
  listed for now, not linked.

The first sync between two libraries works as before; remembering starts
from there.

**Undoing a sync.** **Recent syncs** (on the Sync screen before you
preview) lists the last syncs and which libraries each one wrote.
**Undo this sync** on the most recent one (also shown right after a sync)
puts every library it wrote, Engine DJ and with two-way Rekordbox too,
back exactly as it was before, and OpenCrate's memory with it. The apps must
be closed. Changes made in them since that sync are undone too; their
current state is backed up first, so you can go back from Backups.

**Album art (Engine DJ):** tracks get the cover embedded in their audio
file, stored the way Engine DJ stores it, so it shows in Engine DJ and on
Denon players. Tracks already in Engine DJ without a cover get it with the
next sync; covers Engine DJ already has stay.

### Exporting to a USB stick

**Sync → USB stick → Export to stick** copies playlists from Rekordbox's
library on this computer to a stick, with the music, cues, loops and
beatgrids, for **Rekordbox** (Pioneer players: both of Rekordbox's stick
formats, for older players such as the CDJ-2000NXS2 and XDJ-XZ and newer
ones such as the CDJ-3000X, XDJ-AZ and OPUS-QUAD) and/or **Engine DJ**
(Denon players).

1. Tick the playlists on the left (a ticked folder takes all its
   playlists), or **All playlists** above the list. The bar at the bottom shows how many and roughly how much
   music that is, in orange if it won't fit on the stick.
2. Choose the stick in **Drives** on the right (each shows its free space;
   **↻** looks for drives again).
3. Tick **Rekordbox**, **Engine DJ** or both. Engine DJ needs a library on
   the stick already: plug the stick in with Engine DJ open once, so it
   sets one up.
4. **Preview** shows how many playlists and tracks go on the stick, and
   tracks left out (for example ones Rekordbox hasn't analysed). Nothing
   is written yet: the button then changes to **Export to *stick***.
5. **Export to *stick*** (Engine DJ must be closed for an Engine export).
   The bar at the bottom shows how far it is in percent, the track just
   written (copied, or already on the stick) and the playlists it's in,
   the transfer speed, how much has been written and the time left.
6. Click **⏏** next to the stick and unplug it once OpenCrate says it's
   ejected.

The stick always gets your library as it is on this computer, marked
as your Rekordbox library's: Rekordbox recognises the tracks as its own,
and each track and playlist keeps its number from the last export, so the
players' history stays right. For Engine DJ, songs it already has on the
stick (from its own export, or its import of the Rekordbox export) are
reused, not added twice; the preview counts only new ones. Each music
file is copied once and used by both formats; a file already on the stick
is only copied again if it changed on your computer since (for example
after Tidy fixed its tags). If a track's artist or album changed, it gets
a new folder on the stick and the old copy stays there. For Rekordbox,
playlists already on the stick that your library also has are exported
again, so they stay (also when the stick keeps them in other folders);
ones your library doesn't have leave the stick's Rekordbox list (the
preview names them; their music stays on the stick). For Engine DJ,
playlists and tracks are added, and nothing on the stick is removed. Each
database is backed up before it's written, and your players' settings on
the stick are left alone. Exporting is never done automatically. For now
it works from Rekordbox's own library (not Engine DJ or an XML export). Exporting **All playlists** checks every playlist and track on the stick
again and takes a while; to update a few playlists, tick just those.

### Importing from a USB stick

**Sync → USB stick → Import from stick** brings a stick's playlists (for
example ones made on another computer or on the players) into Rekordbox's
or Engine DJ's library on this computer.

1. Choose the stick in **Drives**. If it has both a Rekordbox export and
   an Engine DJ library, pick which one to read.
2. Tick the playlists to import (or **All playlists**), and choose the library to **Import
   into**.
3. **Preview** lists each playlist: **new** (with how many tracks), **+N
   tracks** for one your library has already, or **up to date**, and
   tracks your library doesn't have.
4. **Import into *library*** (that app must be closed).

The stick's tracks are matched to the files already in your library (by
file size, else artist, title and length); nothing is copied from the
stick, and tracks your library doesn't have are left out. A playlist your
library has already (also in another folder, e.g. "Imported Playlists")
gets only the tracks it lacks; new ones are created in the folder of the
same name, or at the same place as on the stick. Nothing is removed. The
library is backed up first, and if it's your primary library, your other
libraries get the playlists too. Importing is never done automatically.

### Saving cue and grid edits

Hot cues, memory cues, saved loops and beatgrids you change in OpenCrate's
player are saved into your DJ library on their own, a moment after your
last change, like ratings: into the library the track is from (and your
other libraries too if it's the **primary library**, Settings → Sync),
backed up first. If that app is open, the edits wait and are saved when
you close it (or when OpenCrate next starts); the status bar says so. While
an edit isn't in your DJ library yet, the deck shows **EDITED**: click it
to go back to the library's own cues, loops or grid instead. To undo a
saved edit, restore the library from **Backups**.

Tracks a library doesn't have, and tracks Engine DJ hasn't analysed yet,
can't take the edits there: they stay **EDITED** in OpenCrate (load the track
in Engine DJ once, or sync it, and they follow).

**Engine DJ:** OpenCrate's hot cues replace Engine's for those tracks, and the
beatgrid replaces Engine's. Memory cues stay in OpenCrate (Engine DJ has
none). Loops saved in OpenCrate replace Engine's, on its 8 loop pads (a loop
keeps its pad, the others fill free pads in time order); if you didn't
change a track's loops, Engine's stay.

**Rekordbox:** OpenCrate's hot cues and memory cues replace Rekordbox's for
those tracks. Loops saved in OpenCrate replace Rekordbox's: a hot loop keeps
its pad unless a hot cue now sits there, other loops become memory loops.
If you didn't change a track's loops, Rekordbox's stay, except a hot loop
on a pad that now holds a OpenCrate hot cue. The beatgrid replaces
Rekordbox's, in the track's analysis files, the same way Rekordbox saves
a grid you move yourself; those files are backed up with the library and
restored with it. A track Rekordbox hasn't analysed yet can't take a grid
(it stays EDITED). Rekordbox has a fixed set of cue colours: OpenCrate's hot
cue colours are all among them, and any other colour gets the nearest
Rekordbox colour. If
your library uses Cloud Library Sync, OpenCrate says so: Rekordbox then sends
the saved cues to your other computers when it next syncs.

---

## Tidy: cleaning up your library

Tidy finds and fixes problems in track info and files: broken characters,
spam in comments, "ALL CAPS" titles, files that crash imports on players,
and so on. You always see every change before anything is written.

**Library** (top left) chooses which library's tracks to check. **Changes
go to** shows where fixes are written:

- **Audio files** – always. Each file is backed up before it's changed.
- **Rekordbox** – if ticked, the fixes go straight into Rekordbox's library
  too (backed up first; Rekordbox must be closed). If unticked, Rekordbox
  only sees the changes after you select the tracks there and choose
  **Reload Tag**.
- **Engine DJ** – if ticked, Engine DJ's library is kept in step (backed
  up first; Engine DJ must be closed).

If you change a track in Rekordbox or Engine DJ after Tidy showed its
preview, OpenCrate notices when you apply: those changes are left out (and
listed), so Tidy never overwrites an edit you made in the meantime. Scan
again to see the current values.

Tidy works on libraries on this computer. It doesn't change Rekordbox XML
exports (they can be out of date) or USB sticks (those are exported
copies: fix the library on your computer, then export again). USB sticks
have their own check, see [USB stick](#usb-stick).

### Smart fixes

A checklist of fixes that run together:

| Fix | What it does |
|---|---|
| Repair broken characters | `CafÃ©` → `Café`, and removes invisible characters such as hidden direction marks |
| Decode web characters | `&amp;` → `&`, `&#39;` → `'` |
| Remove promotional text | "Free Download", "OUT NOW", "[Promo]" and similar |
| Remove web addresses | URLs, domains and e-mail addresses. For comments you choose: **clear the whole comment** (such comments are nearly always ads) or **remove only the address** |
| Replace characters with spaces | e.g. `Artist_Name_Track` → `Artist Name Track`; pick which characters |
| Remove track numbers from titles | `01 - Title` → `Title`; real titles like "5 Minutes Late" are left alone |
| Split artist out of the title | for tracks with no artist: `Artist - Title` becomes artist + title; for tracks with one, a title starting with that same artist loses it (`Cristina Lazic - Jumpin'` → `Jumpin'`) |
| Remove the label from titles | `Jumpin' (Original Mix) - Bamboleo` → `Jumpin' (Original Mix)`, when the end matches the track's label or the label in its album (`Cabeza EP - Bamboleo Records`) |
| Put mix names in parentheses | `Track - Original Mix` → `Track (Original Mix)` |
| Fill in the remixer | from titles like `Track (Someone Remix)` |
| Fix ALL CAPS / all lowercase | Title Case for titles, artists and albums written entirely in capitals or lowercase |
| Tidy spacing | double spaces, spaces at the ends, stray separators |
| Repair broken dates | dates in a file's tags that apps can't read, such as a year written `25-08-2017`: Rekordbox shows the year as 25, and OpenCrate can't read the file's artwork or change its tags. The file and your libraries get the year it contains (2017); the preview shows what the file says. Only MP3, WAV and AIFF files have this kind of date |

1. Tick the fixes you want and click **Scan with … fixes**.
2. The list on the right shows every change (before → after). Click a fix
   on the left to show only its changes; use the search box to find tracks.
   Untick any change you don't want.
3. Ticking or unticking a fix updates the list by itself; changes you
   unticked stay unticked.
4. Click **Apply selected**. While it writes you can click **Stop** (files
   already changed stay changed) or **Stop and undo** (everything changed
   so far is restored).

If Rekordbox isn't being written to, a yellow banner lists tracks whose
files are fixed but Rekordbox doesn't show it yet, and in which playlists
to find them. Click **Write into Rekordbox now**, or save a playlist to
import into Rekordbox (File › Import › Import Playlist), select all its
tracks and choose **Reload Tag**.

### Genres and Artists

All genres (or artists) with how many tracks use each. Select one or more,
type a new name and click **Preview** to rename or merge them (e.g.
"Deep house", "Deep-House" → "Deep House"). Leave the name empty to remove
it from those tracks.

### Health

**Check all files** reads every audio file (nothing is changed) and reports
problems, grouped by how serious they are:

- **Problems:** missing or empty files.
- **Warnings:** files changed since they were imported, accented names
  stored differently on disk than in the library (fine on a Mac, but
  Linux-based players such as Denon's won't find them on a USB stick),
  hidden macOS `._` files, risky characters in file names, formats most
  players can't play, old ID3v2.2 tags, unusual or oversized artwork,
  tracks listed twice, tags OpenCrate couldn't read.
- **Good to know:** very long paths, high sample rates (above 48 kHz /
  24-bit), missing artwork, progressive JPEG artwork, duplicate tracks.

Click a group to see its tracks.

### USB stick

Checks a DJ USB stick with a Rekordbox export and/or an Engine DJ library.
Nothing on the stick is changed, except junk you choose to delete.

1. Pick the stick and click **Check stick**.
2. OpenCrate shows:
   - the stick's **file system** (FAT32 and exFAT are safest; OpenCrate warns
     about Mac-only or Windows-only formats),
   - what's on it (tracks in the Rekordbox export and Engine library),
   - which **Rekordbox databases** it has. Rekordbox writes two: one for
     newer players (CDJ-3000X, XDJ-AZ, OPUS-QUAD, OMNIS-DUO) and one for
     older players (CDJ-2000NXS2, XDJ-XZ, CDJ-3000 before firmware 3.30).
     If both are there but list different playlists or tracks, OpenCrate says
     which, because newer and older players would then show different
     things. Exporting again from Rekordbox 7.2.11 or newer fixes it,
   - **junk files**: macOS `._` files and `.DS_Store` files, and a leftover
     Rekordbox export lock,
   - **track problems**, with each track's position in the export
     (`#670 · …`). Players import tracks in this order, and some stop at a
     track they can't handle, so the position helps find it.
3. **Delete selected junk** removes only the junk files you tick. Your
   tracks, playlists and exports are never touched.

---

## Backups: undoing changes

### Libraries

Every backup OpenCrate made of your DJ libraries: which app, when, why, and
how many tracks changed since. Select one to see exactly which tracks were
added, removed or changed since then. **Restore** puts the library back
exactly as it was; the current state is backed up first, so a restore can
be undone too. The DJ app must be closed. OpenCrate keeps the 20 most recent
backups per library.

### Tag changes

Every time Tidy changed audio files: what changed in which file, and
whether Rekordbox and Engine DJ were updated. **Undo these changes**
restores the files exactly as they were (byte for byte) and puts the old
values back in Rekordbox and Engine DJ.

---

## Settings

Settings are grouped in a sidebar:

- **General → Updates:**
  - **Install updates automatically:** downloads new versions in the
    background and installs them when you quit OpenCrate.
  - **Tell me about updates** (default): shows a banner; you decide when.
  - **Don't check for updates.**
  - **Check now** looks right away. If you skipped a version, **Offer it
    again** brings it back.
- **General → OpenCrate's data:** the folder where OpenCrate keeps its own
  data: its library (OpenCrate's own playlists, the list of your DJ
  libraries), the backups it makes before changing your DJ libraries, and
  downloaded modules. Your music and your DJ apps' libraries aren't part
  of it. **Change folder…** copies everything into an empty folder you
  choose (for example on a bigger or external drive), checks the copy,
  and uses it after you restart OpenCrate; the old folder is left as it
  is, so you can delete it yourself once you're happy. **Use the standard
  folder** goes back (after a restart) to the standard folder, which holds
  your data as it was when you moved it away; anything done since then
  stays in your folder. If your folder can't be found when OpenCrate
  starts (an unplugged drive), OpenCrate says so and doesn't open
  anything else in its place: connect the drive and restart.
- **General → DJ libraries:** the libraries you chose not to be asked
  about at startup. **Ask again** offers one again the next time OpenCrate
  starts.
- **Appearance → Theme:** Dark, Light, Gray, High contrast or Classic
  Winamp.
- **Appearance → Track list size:** a slider from smaller (more tracks on
  screen) to larger, with a preview; the list follows as you drag.
  **Reset** goes back to the standard size.
- **Appearance → Album art:** show or hide covers in the track list and on
  the decks. OpenCrate keeps small copies of the covers (in your computer's
  cache folder), so they appear right away instead of being read from the
  audio files each time; a changed cover is picked up automatically. The
  section shows how many are cached and how much space they use. **Clear
  all** empties the cache; **Choose playlists…** clears only the covers of
  the playlists you tick (ticking a folder includes everything inside).
  Each playlist and folder shows how much space its covers take, and the
  button shows what clearing the ticked ones frees (tracks in several
  playlists count once).
  Cleared covers are read from the files again as they come into view.
- **Player & mixer:**
  - **Waveform frame rate:** the waveforms move as smoothly as your screen
    allows (up to 120 Hz on ProMotion MacBooks). **Always** caps it at 120
    or 60 fps; **On battery** sets a separate cap while unplugged (60 fps
    unless you change it). Lower caps use less power. **Show the frame
    rate** shows the screen's rate and the waveform frames drawn per second
    (whichever deck is playing) next to the 1 deck / 2 decks buttons.
  - **Deck waveforms:** **Blue** (one colour), **Tri-band** (bass, mids
    and highs layered in blue, orange and white) or **RGB** (red = bass,
    green = mids, blue = highs).
  - **When OpenCrate starts:** **Start maximized**, **Start minimized** or
    **Remember the last state** (open or minimized, as you left it). Also
    **Minimize on other screens** (on unless you turn it off): collapses the
    player while Sync, Tidy, Backups or Settings is open and opens it again
    in the library.
  - **EQ controls:** **Knobs** or **Kill buttons**.
  - **Mixer EQ:** the mixer whose EQ the decks copy, so a mix you prepare
    sounds close to how it will in the booth: Pioneer DJM-900NXS2, DJM-A9,
    DJM-V10 (4 bands), AlphaTheta Euphonia (its 3-band isolator),
    Allen & Heath Xone:92 and Xone:96 (4 bands). Each one lists where its
    figures come from. Pioneer doesn't publish the exact curves of the
    DJM-900NXS2 and DJM-A9, so those two are approximations. Switching puts
    the EQ knobs back in the centre.
- **Audio → Output device:** where the decks play: **System default**
  (your computer's sound setting) or a specific device such as headphones,
  an audio interface or a DJ controller. Switching pauses anything playing;
  loaded tracks stay where they were, with their tempo, EQ and sync. If the
  chosen device is unplugged, OpenCrate uses the system default until it's
  back. **Refresh list** looks for newly connected devices.
- **Sync → Primary library:** edits you make in OpenCrate (ratings,
  playlists, cues and grids) in the primary library also go straight into
  your other libraries (one whose app is open gets them when it closes or
  with the next sync). If you have both Rekordbox and Engine DJ, Rekordbox
  is the primary library until you choose another. **None**: edits go
  only into the library you're viewing, and the others catch up when you
  sync.
  - **Sync automatically when Rekordbox closes** (off by default; with
    Rekordbox as the primary library): when you quit Rekordbox and its
    library changed, OpenCrate syncs it into Engine DJ in the background, like
    the Sync button with Merge, one way (changes made in Engine DJ wait for
    a manual sync). It's backed up and listed under Recent syncs, so it
    can be undone. If Engine DJ is open, a track changed in both apps, more
    than 200 tracks would change, or the two were never synced by hand,
    OpenCrate tells you to open Sync instead.
- **Sync → When something changed in both libraries:** for track info,
  rating, cues, loops and beatgrid: **Newest change wins** (default: the
  app that edited the track last; asks when that's unknown), **Ask me**,
  **The library I sync from wins**, **The library I sync into wins**, or
  for cues and loops **Keep both** (the other's go into free slots).
- **Tidy & backups:**
  - **Where Tidy writes its changes:** write into Rekordbox's library, and
    keep Engine DJ's library in step (both on by default). The same switches
    are on the Tidy screen.
  - **Before changing audio files, back up…** **Tags and artwork only**
    (recommended: small backups, and undo still restores the exact original
    file) or **The entire file** (a full copy of every file before it's
    changed).
- **Modules:** optional parts OpenCrate downloads only when you want them, so
  the app itself stays small (audio analysis, file conversion and the
  like, as they become available). Each shows its size with **Download**,
  **Update** or **Remove**. Every module is signed by OpenCrate and checked
  before it's installed. A feature that needs a module offers the
  download the first time you use it. There are no modules yet.
- **About:** OpenCrate's version and licence. **Copy log** copies OpenCrate's log
  (what it did and any errors) for a bug report; **Show log file** opens
  its folder.

---

## Battery

On a laptop, the top right corner of the window shows the battery: its
charge, with a green bolt beside it while charging, or a plug while on the
power adapter but not charging. Next to it is the time: how long the
battery lasts on battery, how long until full while charging, or **Fully
charged**. **Charging on hold** means macOS is keeping the battery below
full to protect it. It updates within a couple of seconds of plugging in or
out. Computers without a battery don't show it.

---

## The status bar

The bar at the bottom shows what OpenCrate is doing (importing, scanning,
writing tags, syncing…) and, for each DJ app:

| Badge | Meaning |
|---|---|
| **Rekordbox open · read-only** | OpenCrate won't change Rekordbox's library until you quit Rekordbox |
| **Rekordbox closed · writable** | OpenCrate can write into Rekordbox (after a backup); keep it closed until OpenCrate is done |
| **Rekordbox · files only** | Writing into Rekordbox is off in Settings; use Reload Tag in Rekordbox |
| **Engine DJ open / closed** | The same for Engine DJ |

Hover over a badge for details.

---

## Not in OpenCrate yet

Planned, but not available in this version:

- More mixing tools: crossfader, beat jump
- Filter and effects; keyboard shortcuts; DJ controller support; a
  headphone (cue) output
- Syncing from Engine DJ to Rekordbox
- Exporting to a USB stick from Engine DJ's library or an XML export
- Importing tracks from a stick that your library doesn't have yet
- Cleaning old copies of music off a stick
- Looking up track info and album art online, and shrinking artwork for
  players
- Converting audio files (e.g. to AIFF or MP3)
- Scheduled backups

The Windows version hasn't been tested much yet; reports are especially
welcome.

---

## Reporting problems

Tell us what you did, what you expected and what happened, and include a
screenshot if you can. Settings → About → **Copy log** copies OpenCrate's log;
paste it into your report. It lists what OpenCrate did (imports, syncs, saves,
backups) and any errors, with file paths but no passwords. If a library looks wrong after a change, close the
DJ app and restore the backup from **Backups → Libraries** (or undo the
change in **Backups → Tag changes**) before doing anything else.

If OpenCrate shows **Please update OpenCrate** when it starts, your OpenCrate library
was last opened by a newer version. Click **Get the latest version** and
install it; nothing has been lost or changed. (Versions before 0.1.3 quit
straight away in this case instead of showing the message.)

---

OpenCrate is free software under the
[GNU General Public License v3.0](https://www.gnu.org/licenses/gpl-3.0.html).
