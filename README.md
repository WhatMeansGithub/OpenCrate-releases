# Krate user manual

Krate is a DJ library manager for macOS and Windows. It reads your
**Rekordbox** and **Engine DJ** libraries, syncs playlists, cues and
beatgrids from Rekordbox to Engine DJ, and cleans up messy track info and
files so they work on every player.

> **Alpha version.** Krate is early software. It backs up your libraries
> before every change, but please keep your own backups as well, and tell
> us about anything that looks wrong.

---

## Contents

1. [Installing](#installing)
2. [How Krate keeps your library safe](#how-krate-keeps-your-library-safe)
3. [Getting started](#getting-started)
4. [Library: browsing your tracks](#library-browsing-your-tracks)
5. [Sync: Rekordbox to Engine DJ](#sync-rekordbox-to-engine-dj)
6. [Tidy: cleaning up your library](#tidy-cleaning-up-your-library)
7. [Backups: undoing changes](#backups-undoing-changes)
8. [Settings](#settings)
9. [The status bar](#the-status-bar)
10. [Not in Krate yet](#not-in-krate-yet)
11. [Reporting problems](#reporting-problems)

---

## Installing

Download the file for your computer from the
[releases page](https://github.com/WhatMeansGithub/krate-releases/releases):

| Your computer | File |
|---|---|
| Mac with Apple Silicon (M1 or newer) | `Krate_…_aarch64.dmg` |
| Mac with an Intel processor | `Krate_…_x64.dmg` |
| Windows | `Krate_…_x64-setup.exe` |

Not sure which Mac you have? Apple menu → **About This Mac**: "Chip: Apple
M…" means Apple Silicon, "Processor: Intel" means Intel.

These builds aren't signed yet, so the first launch needs one extra step:

- **macOS:** open the `.dmg` and drag **Krate** into **Applications**. If
  macOS says Krate can't be opened, go to **System Settings → Privacy &
  Security**, scroll down and click **Open Anyway**. (Or right-click Krate
  in Applications → **Open**.) If macOS instead says Krate "is damaged",
  open **Terminal** and run `xattr -cr /Applications/Krate.app`, then open
  Krate again.
- **Windows:** run the installer. If SmartScreen warns about an unknown
  app, click **More info → Run anyway**.

### Updating Krate

Krate updates itself. When a new version is out, a blue banner at the top
offers it: **Download update**, then **Restart and update**. Or choose
**Skip this version** or **Later**. Updates are signed, and Krate only
installs updates that come from Krate's own releases. Krate never restarts
by itself, and you can't restart while it's writing to a library. How Krate
handles updates is set in [Settings](#settings).

(Keep Krate in your Applications folder on a Mac; updates can't replace a
copy that's still on the disk image.)

---

## How Krate keeps your library safe

- **Reading never changes anything.** Krate reads your DJ libraries from a
  copy and never modifies them just by looking.
- **Backups before every write.** Before Krate changes a DJ library
  (syncing, Tidy, restoring), it makes a backup and checks that the backup
  is complete. Before it changes an audio file's tags, it backs up that
  file's tags and artwork (or the whole file, see [Settings](#settings)).
- **Only while the DJ app is closed.** Krate won't change Rekordbox's or
  Engine DJ's library while that app is open. The
  [status bar](#the-status-bar) shows when an app is open.
- **Checked after writing.** After writing to a library, Krate checks the
  database is intact and the values read back correctly. If not, it puts
  the backup back automatically.
- **Your music is never deleted or re-encoded.** Krate only edits tags
  (title, artist, …); the audio itself is never touched.
- **Everything can be undone** from the [Backups](#backups-undoing-changes)
  tab.

---

## Getting started

When you first open Krate, it looks for your libraries in their usual
places:

- **Rekordbox** (6 and 7): your Rekordbox library on this computer.
- **Engine DJ**: the `Engine Library` folder in your Music folder.

Click **Import Rekordbox library** or **Import Engine DJ library** (later on, these buttons are at the top of the window). Under
**Other…** you can import a **Rekordbox XML** export or an Engine Library
folder somewhere else (for example on a USB drive).

You can import several libraries; pick one in the sidebar. Imported
libraries update themselves: every time Krate starts (and after a sync,
Tidy or restore), it re-reads any library that changed.

---

## Library: browsing your tracks

- The **sidebar** lists your imported libraries and their playlists and
  folders. Click a playlist to show its tracks; click the library name for
  all tracks.
- The **search** box filters by title, artist, album, genre, label and comment.
- Click a **column header** to sort.
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

If the deck is playing, Krate asks before replacing its track. Playback
keeps going while you switch tabs.

Click **Player** (top left of the player area) to minimize it to one line,
and again to open it. Minimized, each loaded deck shows ▶ / ❚❚, its title,
the time and a thin overview of the track (click to jump; you can drop
tracks on it too); with nothing loaded the line stays empty. Settings →
Player & mixer chooses how the player starts and whether it minimizes on
other screens.

Choose the player at the top right of the player area:

- **1 deck:** the big waveform with the deck's controls below.
- **2 decks:** both decks' waveforms stacked on top of each other (A above
  B, like Rekordbox), with the two decks' controls side by side below.
  **Load selected** loads the track selected in the list into that deck.

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
  track has that hot cue; click it to jump there and play.
- **Volume:** the deck's volume, in percent.
- **EQ:** the bands of the mixer chosen in Settings →
  Player & mixer, highs on the left. As knobs: drag up or down (hold Shift
  for fine steps), or scroll; double-click puts a knob back in the centre.
  As kill buttons: a lit button cuts its band. Bands that fully kill on the
  real mixer go silent when turned all the way left; the others stop at the
  mixer's cut (for example −26 dB on Pioneer mixers). The ring lights blue
  while a band is cut and red while it's boosted.

Below that, the beatmatching tools:

- **◀ ▶ (nudge):** hold to slow the deck down or speed it up by 4 %, to
  push it into time with the other deck.
- **Tempo:** the tempo fader, in percent; double-click it to go back to
  0 %. **±8** next to it switches the range (±8, ±16, ±50 %). The BPM in
  the deck's top row shows the tempo it plays at now.
- **MT (Master Tempo):** keylock. With it on, changing the tempo keeps the
  key; with it off, the key rises and falls with the tempo like a record.
- **Key:** the key the track sounds in now. **−** and **+** shift it by a
  semitone; click the shifted key to reset it. Krate shows keys the way
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
  other deck the master.
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

1. **From:** your Rekordbox library (or a Rekordbox XML export).
   **To:** your Engine DJ library. Krate finds both automatically; use
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
5. Click **Preview changes**. Krate lists exactly which tracks and
   playlists will be added, changed or removed. Nothing has been written
   yet.
6. Click **Sync now** to write it. Engine DJ must be closed.

Cue points line up exactly between the apps, including the small timing
difference Rekordbox and Engine DJ have with some MP3 files.

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

Tidy works on libraries on this computer. It doesn't change Rekordbox XML
exports (they can be out of date) or USB sticks (those are exported
copies: fix the library on your computer, then export again). USB sticks
have their own check, see [USB stick](#usb-stick).

### Health

A checklist of fixes that run together:

| Fix | What it does |
|---|---|
| Repair broken characters | `CafÃ©` → `Café`, and removes invisible characters such as hidden direction marks |
| Decode web characters | `&amp;` → `&`, `&#39;` → `'` |
| Remove promotional text | "Free Download", "OUT NOW", "[Promo]" and similar |
| Remove web addresses | URLs, domains and e-mail addresses. For comments you choose: **clear the whole comment** (such comments are nearly always ads) or **remove only the address** |
| Replace characters with spaces | e.g. `Artist_Name_Track` → `Artist Name Track`; pick which characters |
| Remove track numbers from titles | `01 - Title` → `Title`; real titles like "5 Minutes Late" are left alone |
| Split artist out of the title | for tracks with no artist: `Artist - Title` becomes artist + title |
| Put mix names in parentheses | `Track - Original Mix` → `Track (Original Mix)` |
| Fill in the remixer | from titles like `Track (Someone Remix)` |
| Fix ALL CAPS / all lowercase | Title Case for titles, artists and albums written entirely in capitals or lowercase |
| Tidy spacing | double spaces, spaces at the ends, stray separators |

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

### Files

**Check all files** reads every audio file (nothing is changed) and reports
problems, grouped by how serious they are:

- **Problems:** missing or empty files.
- **Warnings:** files changed since they were imported, accented names
  stored differently on disk than in the library (fine on a Mac, but
  Linux-based players such as Denon's won't find them on a USB stick),
  hidden macOS `._` files, risky characters in file names, formats most
  players can't play, old ID3v2.2 tags, unusual or oversized artwork,
  tracks listed twice, tags Krate couldn't read.
- **Good to know:** very long paths, high sample rates (above 48 kHz /
  24-bit), missing artwork, progressive JPEG artwork, duplicate tracks.

Click a group to see its tracks.

### USB stick

Checks a DJ USB stick with a Rekordbox export and/or an Engine DJ library.
Nothing on the stick is changed, except junk you choose to delete.

1. Pick the stick and click **Check stick**.
2. Krate shows:
   - the stick's **file system** (FAT32 and exFAT are safest; Krate warns
     about Mac-only or Windows-only formats),
   - what's on it (tracks in the Rekordbox export and Engine library),
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

Every backup Krate made of your DJ libraries: which app, when, why, and
how many tracks changed since. Select one to see exactly which tracks were
added, removed or changed since then. **Restore** puts the library back
exactly as it was; the current state is backed up first, so a restore can
be undone too. The DJ app must be closed. Krate keeps the 20 most recent
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
    background and installs them when you quit Krate.
  - **Tell me about updates** (default): shows a banner; you decide when.
  - **Don't check for updates.**
  - **Check now** looks right away. If you skipped a version, **Offer it
    again** brings it back.
- **Appearance → Theme:** Dark, Light, Gray, High contrast or Classic
  Winamp.
- **Appearance → Deck waveforms:** **Blue** (one colour), **Tri-band**
  (bass, mids and highs layered in blue, orange and white) or **RGB**
  (red = bass, green = mids, blue = highs).
- **Appearance → Album art:** show or hide covers in the track list and on
  the decks.
- **Player & mixer:**
  - **When Krate starts:** **Start maximized**, **Start minimized** or
    **Remember the last state** (open or minimized, as you left it). Also
    **Minimize on other screens**: collapses the player while Sync, Tidy,
    Backups or Settings is open and opens it again in the library.
  - **EQ controls:** **Knobs** or **Kill buttons**.
  - **Mixer EQ:** the mixer whose EQ the decks copy, so a mix you prepare
    sounds close to how it will in the booth: Pioneer DJM-900NXS2, DJM-A9,
    DJM-V10 (4 bands), AlphaTheta Euphonia (its 3-band isolator),
    Allen & Heath Xone:92 and Xone:96 (4 bands). Each one lists where its
    figures come from. Pioneer doesn't publish the exact curves of the
    DJM-900NXS2 and DJM-A9, so those two are approximations. Switching puts
    the EQ knobs back in the centre.
- **Tidy & backups:**
  - **Where Tidy writes its changes:** write into Rekordbox's library, and
    keep Engine DJ's library in step (both on by default). The same switches
    are on the Tidy screen.
  - **Before changing audio files, back up…** **Tags and artwork only**
    (recommended: small backups, and undo still restores the exact original
    file) or **The entire file** (a full copy of every file before it's
    changed).
- **About:** Krate's version and licence.

---

## The status bar

The bar at the bottom shows what Krate is doing (importing, scanning,
writing tags, syncing…) and, for each DJ app:

| Badge | Meaning |
|---|---|
| **Rekordbox open · read-only** | Krate won't change Rekordbox's library until you quit Rekordbox |
| **Rekordbox closed · writable** | Krate can write into Rekordbox (after a backup); keep it closed until Krate is done |
| **Rekordbox · files only** | Writing into Rekordbox is off in Settings; use Reload Tag in Rekordbox |
| **Engine DJ open / closed** | The same for Engine DJ |

Hover over a badge for details.

---

## Not in Krate yet

Planned, but not available in this version:

- More mixing tools: setting and deleting hot cues, crossfader, loops, quantize, editing
  beatgrids (in progress)
- Filter and effects; keyboard shortcuts; DJ controller support; a
  headphone (cue) output
- Editing playlists inside Krate
- Syncing from Engine DJ to Rekordbox
- Syncing straight onto an Engine DJ USB stick (copying the music too)
- Exporting Rekordbox USB sticks
- Looking up track info and album art online, and shrinking artwork for
  players
- Converting audio files (e.g. to AIFF or MP3)
- Scheduled backups

The Windows version hasn't been tested much yet; reports are especially
welcome.

---

## Reporting problems

Tell us what you did, what you expected and what happened, and include a
screenshot if you can. If a library looks wrong after a change, close the
DJ app and restore the backup from **Backups → Libraries** (or undo the
change in **Backups → Tag changes**) before doing anything else.

---

Krate is free software under the
[GNU General Public License v3.0](https://www.gnu.org/licenses/gpl-3.0.html).
