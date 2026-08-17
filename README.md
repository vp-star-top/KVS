# KVS
# KVS — Kishore Vibe Studio

> **Timeless melodies. Endless memories.**

KVS (Kishore Vibe Studio) is a premium vintage-inspired music web application celebrating classic Hindi music, Bollywood nostalgia, Indian radio culture, cassette tapes, vinyl records and selected international classics.

The project should feel like:

**Vintage Indian Radio + Bollywood Cinema + Cassette Culture + Vinyl + Modern Premium Web Design**

It must **not** look like Spotify or a generic music dashboard.

---

# 🚨 AI DEVELOPER INSTRUCTIONS

If you are an AI coding agent working on this repository, follow these rules strictly.

## DO

* Build the complete working application.
* Use the local music files supplied by the project owner.
* Keep all music data in an editable data structure.
* Use HTML5 audio for local MP3 playback.
* Make the music player actually functional.
* Make the site responsive.
* Use localStorage for favorites, queue and recently played.
* Handle missing audio files gracefully.
* Keep components reusable.
* Keep the code clean and maintainable.
* Preserve the KVS vintage visual identity.

## DO NOT

* Invent songs.
* Invent artists.
* Invent movie names.
* Invent years.
* Invent genres.
* Invent artwork.
* Invent external URLs.
* Download replacement music.
* Scrape YouTube.
* Convert YouTube videos to MP3.
* Download from Spotify.
* Bypass streaming restrictions.
* Treat YouTube or Spotify webpage URLs as direct audio sources.
* Create fake MP3 files.
* Replace missing audio with placeholder music.

If information is unavailable, use:

**Information unavailable**

or leave the field empty.

---

# 1. PROJECT PURPOSE

KVS is a digital home for timeless music.

The primary experience should feel like entering an old Indian music studio late at night.

The interface should combine:

* Old Indian radio
* Vintage Bollywood
* Classic cinema
* Cassette culture
* Vinyl records
* Warm studio lighting
* Aged paper
* Film grain
* Modern responsive UI

The design should be premium, atmospheric and cinematic.

---

# 2. CORE FEATURES

The application must contain:

* Home
* Songs
* Artists
* Eras
* Moods
* KVS Radio
* About
* Global Search
* Full Music Player
* Sticky Bottom Player
* Queue
* Favorites
* Recently Played
* Song Details
* MP3 Import/Preview interface
* Music File Status panel

---

# 3. MUSIC FILE ARCHITECTURE

Permanent music assets belong here:

```text
public/
└── assets/
    └── music/
```

Example:

```text
public/assets/music/
├── ab-agar-humse-khudai-bhi.mp3
├── badan-pe-sitare-lapete-hue.mp3
├── badi-mastani-hai-meri-mehbooba.mp3
├── baharo-phool-barsao.mp3
├── dil-ne-dil-ko-pukara.mp3
├── kaun-kisi-ko-baandh-saka.mp3
├── tere-naina-mere-naino.mp3
├── mere-samne-wali-khidki-mein-ik-chaand.mp3
├── laagi-chhute-na-ab-to-sanam.mp3
└── aaj-phir-jeene-ki-tamanna-hai.mp3
```

These are expected filenames only.

**Do not create fake files if they are missing.**

The application must work correctly even when these files have not yet been added.

---

# 4. SONG DATA

Keep all music metadata in one easily editable location.

Preferred:

```text
src/
└── data/
    └── songs.js
```

or the equivalent structure for the chosen framework.

Example:

```js
export const songs = [
  {
    id: 1,
    title: "",
    artist: "",
    movie: "",
    year: "",
    genre: "",
    duration: "",
    audioUrl: "/assets/music/example.mp3",
    youtubeUrl: "",
    spotifyUrl: "",
    officialUrl: "",
    artwork: ""
  }
];
```

Every song object should support:

```text
id
title
artist
movie
year
genre
duration
audioUrl
youtubeUrl
spotifyUrl
officialUrl
artwork
```

Only use metadata actually supplied by the project owner.

---

# 5. AUDIO PLAYBACK

Use a real HTML5 audio implementation.

Preferred architecture:

```js
const audio = new Audio();
```

or a shared:

```html
<audio></audio>
```

element managed by the application.

When a song is selected:

```js
audio.src = song.audioUrl;
audio.load();
```

Playback must be real.

Do not simulate playback with timers or fake progress bars.

---

# 6. PLAYER FEATURES

The music player must support:

* Play
* Pause
* Previous
* Next
* Seek
* Progress
* Current time
* Total duration
* Volume
* Mute
* Queue
* Automatic next song
* Error handling

The UI must update from the actual HTML5 audio state.

For example:

```js
audio.addEventListener("timeupdate", ...)
audio.addEventListener("loadedmetadata", ...)
audio.addEventListener("ended", ...)
audio.addEventListener("error", ...)
```

The progress bar must represent the real playback position.

---

# 7. AUDIO ERROR HANDLING

If:

```text
/assets/music/song.mp3
```

does not exist or cannot be played:

Display:

> **Audio unavailable**

Then display:

> Add this MP3 to `public/assets/music/` to enable playback.

The application must not crash.

Other songs must remain playable.

---

# 8. EXTERNAL LISTENING

External links are optional.

Supported fields:

```js
youtubeUrl
spotifyUrl
officialUrl
```

Only display these buttons if an actual URL was supplied.

Buttons:

```text
LISTEN ON YOUTUBE
LISTEN ON SPOTIFY
OPEN OFFICIAL SOURCE
```

IMPORTANT:

These URLs are external destinations only.

Never assign them to:

```js
audio.src
```

YouTube and Spotify webpage URLs must never be treated as direct MP3/audio URLs.

---

# 9. MP3 IMPORT / PREVIEW

Create a simple music import interface.

It should support:

```html
<input
  type="file"
  accept="audio/mpeg,audio/mp3"
  multiple
/>
```

Also support drag and drop.

When files are selected:

1. Display filenames.
2. Create temporary browser URLs with `URL.createObjectURL()`.
3. Allow immediate preview.
4. Match filenames against catalogue songs where possible.
5. Show matched files.
6. Show unmatched files.
7. Show missing permanent assets.

Example:

```js
const temporaryUrl = URL.createObjectURL(file);
```

Then:

```js
audio.src = temporaryUrl;
audio.play();
```

Temporary browser imports do not need to survive a page refresh.

---

# 10. IMPORTANT — TEMPORARY VS PERMANENT FILES

Clearly explain in the import UI:

### Temporary Browser Import

Files selected through the browser are available for preview during the current browser session.

They are not automatically added to the deployed project.

### Permanent Music

For permanent website playback, place the MP3 files inside:

```text
public/assets/music/
```

Then make sure the corresponding `audioUrl` points to the correct file.

---

# 11. MUSIC FILE STATUS

Create a developer/admin status panel.

Title:

**MUSIC LIBRARY**

For each song show:

```text
Song Name
Audio: ✓ Available
```

or:

```text
Song Name
Audio: ✕ Missing
```

The status should be determined by the actual file availability where possible.

Do not simply mark every file as available.

---

# 12. HOME PAGE

Create a dramatic hero.

Display:

```text
KVS

KISHORE VIBE STUDIO

Timeless melodies. Endless memories.
```

Supporting text:

> Step into a world of unforgettable voices, timeless Bollywood melodies and songs that generations grew up with.

Buttons:

```text
EXPLORE MUSIC
KVS RADIO
```

Visual direction:

* Vintage radio
* Vinyl
* Cassette
* Warm lighting
* Paper texture
* Film grain
* Cinematic shadows

---

# 13. NAVIGATION

Create a sticky navigation.

```text
KVS
Kishore Vibe Studio

HOME
SONGS
ARTISTS
ERAS
MOODS
KVS RADIO
ABOUT
SEARCH
```

Mobile:

* Hamburger navigation
* Touch-friendly controls
* No horizontal overflow

---

# 14. SONGS PAGE

Display the complete supplied catalogue.

Features:

* Search
* Sort
* Artist filter
* Year filter
* Genre filter
* Movie filter

Each song card should contain:

* Song title
* Artist
* Movie/album
* Year
* Genre
* Play
* Favorite
* External listening buttons when available

---

# 15. GLOBAL SEARCH

Search instantly across:

* Title
* Artist
* Movie
* Album
* Year
* Genre

Search results should update without unnecessary page reloads.

---

# 16. ARTISTS

Generate artist pages from the actual song data.

Do not create artists that do not exist in the supplied catalogue.

Artist pages should show:

* Artist name
* Number of songs
* Artwork when supplied
* Introduction when supplied
* Songs
* Movies/albums
* Years
* Genres

---

# 17. KISHORE KUMAR COLLECTION

When Kishore Kumar songs exist in the catalogue, create:

## THE KISHORE KUMAR COLLECTION

Subtitle:

> Celebrating an unforgettable voice of Indian cinema.

Possible filters:

* Romantic
* Sad
* Classic
* Duets
* 70s
* 80s
* Movie Songs

Only show categories containing actual matching songs.

---

# 18. MUSIC ERAS

Automatically group songs according to their actual year.

Possible groups:

```text
1960s
1970s
1980s
1990s
2000s
2010s+
```

Only show eras represented by the actual data.

Use a vintage timeline design.

---

# 19. MOOD COLLECTIONS

Generate mood collections from available metadata.

Possible collections:

* Romantic Memories
* Heartbreak Classics
* Late Night Melodies
* Evening Chai
* Road Trip Classics
* Bollywood Gold
* 90s Nostalgia
* Legendary Voices

Do not invent metadata to force songs into collections.

---

# 20. KVS RADIO

Create a dedicated radio experience.

Title:

**KVS RADIO**

Subtitle:

> Broadcasting timeless memories.

Include:

* Current song
* Artist
* Movie
* Year
* Artwork
* Previous
* Play/Pause
* Next
* Volume
* Equalizer
* Radio tuning animation

Use actual local audio files.

If audio is missing:

> Choose a listening source

---

# 21. QUEUE

Create:

## UP NEXT

Users can:

* Add songs
* Remove songs
* Clear queue
* Play next
* Navigate previous/next

Persist the queue using:

```js
localStorage
```

---

# 22. FAVORITES

Each song has:

```text
♡ Favorite
♥ Favorite
```

Create:

## MY FAVORITES

Persist favorites using:

```js
localStorage
```

No login required.

---

# 23. RECENTLY PLAYED

Create:

## RECENTLY PLAYED

Store the latest 10 selected/played songs.

Use:

```js
localStorage
```

Avoid storing unlimited history.

---

# 24. SONG DETAILS

Create a detailed song view.

Show:

* Artwork
* Title
* Artist
* Movie
* Year
* Genre
* Duration
* Description if supplied

Actions:

```text
PLAY
YOUTUBE
SPOTIFY
OFFICIAL SOURCE
```

Only show external buttons when valid URLs exist.

Also show:

* More from this artist
* More from this year
* More from this movie

---

# 25. STICKY MUSIC BAR

Create a bottom music control bar.

Desktop:

```text
Artwork | Song | Artist | Progress | Controls | Volume
```

Mobile:

```text
Artwork | Song | Play/Pause
```

Clicking the bar opens the expanded player.

The active state must reflect the real audio element.

---

# 26. VISUAL DESIGN

Use:

* Warm cream
* Aged paper
* Dark brown
* Charcoal
* Muted red
* Vintage orange
* Subtle gold

Visual effects:

* Paper grain
* Film grain
* Soft gradients
* Cinematic shadows
* Vintage borders
* Vinyl rotation
* Cassette reels
* Radio tuning
* Equalizer bars
* Floating dust
* Soft hover effects

Keep animations lightweight.

Respect:

```css
@media (prefers-reduced-motion: reduce)
```

---

# 27. RESPONSIVE DESIGN

The application must work on:

* Desktop
* Laptop
* Tablet
* Mobile

Requirements:

* No horizontal scrolling
* Touch-friendly controls
* Readable song cards
* Responsive player
* Responsive navigation
* Proper spacing on small screens

---

# 28. PERFORMANCE

Prefer:

* Reusable components
* Lazy-loaded images
* Efficient filtering
* Minimal dependencies
* Small assets
* LocalStorage only where needed

Do not add libraries unless they provide real value.

---

# 29. ABOUT PAGE

Create:

## ABOUT KVS

### Kishore Vibe Studio

Text:

> KVS is a digital celebration of timeless music — bringing together legendary Hindi voices, unforgettable Bollywood melodies and classic international sounds in one nostalgic experience.

Display:

> Timeless melodies. Endless memories.

---

# 30. COPYRIGHT POLICY

Display an elegant notice:

> Music belongs to its respective artists, composers, labels and rights holders. KVS does not host or distribute copyrighted audio unless properly licensed. External listening links belong to their respective platforms.

The application must never implement:

* YouTube-to-MP3 conversion
* YouTube scraping
* Spotify downloading
* Audio ripping
* Streaming bypasses
* Unauthorized copyrighted audio hosting

Only owner-supplied and properly authorized local audio should be played.

---

# 31. FOOTER

Display:

```text
KVS
Kishore Vibe Studio

Timeless melodies. Endless memories.

Home
Songs
Artists
Eras
Moods
KVS Radio
About

© 2026 KVS — Kishore Vibe Studio
Music belongs to its respective rights holders.
```

---

# 32. RECOMMENDED PROJECT STRUCTURE

Use an architecture similar to:

```text
kvs/
├── public/
│   └── assets/
│       └── music/
│
├── src/
│   ├── components/
│   │   ├── AudioPlayer
│   │   ├── StickyPlayer
│   │   ├── SongCard
│   │   ├── SongGrid
│   │   ├── SearchBar
│   │   ├── Queue
│   │   ├── FavoriteButton
│   │   ├── Radio
│   │   └── MusicImport
│   │
│   ├── data/
│   │   └── songs.js
│   │
│   ├── pages/
│   │   ├── Home
│   │   ├── Songs
│   │   ├── Artists
│   │   ├── Eras
│   │   ├── Moods
│   │   ├── Radio
│   │   ├── SongDetails
│   │   └── About
│   │
│   ├── hooks/
│   │   └── useAudioPlayer
│   │
│   ├── utils/
│   │   ├── storage
│   │   ├── search
│   │   └── music
│   │
│   └── App
│
├── package.json
└── README.md
```

Adapt this structure to the actual framework rather than blindly creating unnecessary files.

---

# 33. QUALITY CHECKLIST

Before declaring the project complete, verify:

* [ ] Application starts successfully
* [ ] Homepage works
* [ ] Songs page works
* [ ] Search works
* [ ] Filters work
* [ ] Artists work
* [ ] Eras work
* [ ] Moods work
* [ ] KVS Radio works
* [ ] Song details work
* [ ] Audio player works
* [ ] Play works with a real MP3
* [ ] Pause works
* [ ] Previous works
* [ ] Next works
* [ ] Progress works
* [ ] Seek works
* [ ] Volume works
* [ ] Mute works
* [ ] Queue works
* [ ] Favorites persist
* [ ] Recently played persists
* [ ] Missing MP3 files are handled
* [ ] MP3 import preview works
* [ ] Music status panel works
* [ ] Mobile layout works
* [ ] Desktop layout works
* [ ] Reduced motion is respected
* [ ] No fake songs exist
* [ ] No fake URLs exist
* [ ] No fake MP3 files exist
* [ ] No YouTube/Spotify webpage is used as an audio source
* [ ] No copyrighted audio is downloaded automatically

---

# 34. FINAL AI AGENT INSTRUCTION

**Build the application, do not merely describe it.**

If some MP3 files are unavailable in the repository, continue development normally.

The missing files must only cause:

```text
Audio unavailable
```

They must not prevent the application from running.

When the owner later adds:

```text
public/assets/music/*.mp3
```

the corresponding songs must automatically become playable without requiring a redesign or major code changes.

The project should be easy for a non-programmer to maintain.

The most important rule is:

> **Never invent music data or audio. Use only the files and metadata supplied by the project owner.**
