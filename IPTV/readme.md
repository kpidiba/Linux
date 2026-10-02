# IPTV on Linux — Simple README

## 1. What is IPTV?

**IPTV (Internet Protocol Television)** is a way of watching television channels and video content through an **Internet connection** instead of traditional terrestrial, satellite, or cable broadcasting.

The basic idea is:

```json
IPTV Provider
     │
     │ Internet
     ▼
 IPTV Stream
     │
     ▼
 IPTV Player
(IPTVnator / VLC / etc.)
     │
     ▼
 Your screen
```

The IPTV player normally **does not provide the TV channels itself**. It receives a playlist or connection information from an IPTV service and plays the streams. For example, IPTVnator supports M3U/M3U8 playlists, Xtream Codes and Stalker portals, but does not provide channels or playlists.

> **Important:** IPTV technology itself is not inherently illegal. What matters is whether the service has the necessary rights/licenses for the content in your country.

---

## 2. How IPTV works

A provider can give you one of several types of access.

### M3U / M3U8 playlist

You receive something similar to:

```json
https://example.com/playlist.m3u
```

The playlist contains information about channels and their stream URLs.

You give this URL to your IPTV application.

### Xtream Codes

Some providers give you:

```json
Server URL
Username
Password
```

For example:

```json
Server: https://example.com
Username: myuser
Password: mypassword
```

The IPTV player uses these credentials to retrieve the available channels, movies, series and sometimes EPG information.

### EPG

**EPG = Electronic Program Guide.**

It provides information such as:

```json
20:00  News
21:00  Football
23:00  Movie
```

IPTVnator supports EPG information in XMLTV format.

---

# 3. IPTV applications for Linux

## IPTVnator

IPTVnator is an open-source IPTV player based on Electron/Angular.

Official website:

[IPTVnator official website](https://4gray.github.io/iptvnator/?utm_source=chatgpt.com)

Official GitHub:

[IPTVnator GitHub](https://github.com/4gray/iptvnator?utm_source=chatgpt.com)

It supports:

- M3U / M3U8
- Xtream Codes
- Stalker portals
- EPG
- Favorites
- Search
- Catch-up / TV archive
- VLC / MPV
- Linux, Windows and macOS

The current official site provides Linux **AppImage, `.deb` and other packages**.

### Install on Ubuntu/Debian

You can use Snap:

```bash
sudo snap install iptvnator
```

Or download the `.deb`/AppImage from the official website.

---

# 4. Using IPTVnator

After installing IPTVnator:

### Method A — M3U URL

1. Open IPTVnator.
2. Choose **Add Playlist**.
3. Select **M3U**.
4. Enter your playlist URL.

Example:

```json
https://provider.example/playlist.m3u
```

5. Give the playlist a name.
6. Save.
7. Your channels should appear.

You can then select a channel and press **Play**.

---

### Method B — M3U file

If you have:

```json
channels.m3u
```

you can import the file directly into IPTVnator.

```json
Add Playlist
     ↓
M3U
     ↓
Local File
     ↓
channels.m3u
     ↓
Save
```

IPTVnator officially supports importing playlists from local files as well as remote URLs.

---

### Method C — Xtream Codes

If your legitimate IPTV provider gives you:

```json
Server URL
Username
Password
```

choose the **Xtream Codes** option and enter those values.

IPTVnator will then retrieve the available content from the service.

---

# 5. Other Linux options

### VLC

VLC media player can also play many IPTV streams.

For a direct stream:

```bash
vlc "https://example.com/live/channel.m3u8"
```

Or open VLC → **Media → Open Network Stream** and paste the stream URL.

VLC is useful when you simply want to test whether a particular stream works.

### MPV

mpv is another excellent Linux option:

```bash
mpv "https://example.com/live/channel.m3u8"
```

IPTVnator can also use external players such as VLC and MPV.

---

# 6. IPTV architecture in simple terms

```json
                    INTERNET
                       │
                       ▼
              ┌─────────────────┐
              │  IPTV Provider  │
              │                 │
              │ Live TV         │
              │ Movies          │
              │ Series          │
              │ EPG             │
              └────────┬────────┘
                       │
             M3U / Xtream / Stalker
                       │
                       ▼
              ┌─────────────────┐
              │  IPTVnator      │
              │                 │
              │ Playlist        │
              │ EPG             │
              │ Player          │
              │ Favorites       │
              └────────┬────────┘
                       │
                       ▼
                 ┌───────────┐
                 │  Screen   │
                 └───────────┘
```

The important distinction is:

**IPTV provider ≠ IPTV application**

For example:

```json
Your legal IPTV subscription
            +
       IPTVnator
            ↓
       TV channels
```

IPTVnator itself doesn't sell the subscription or supply the channels.

---

## 7. Recommended Linux setup

For a Linux desktop, a simple setup is:

```json
Ubuntu / Pop!_OS / Debian
          │
          ├── IPTVnator → main IPTV interface
          │
          ├── VLC       → alternative player
          │
          └── MPV       → lightweight alternative player
```

If you already have a **legitimate IPTV subscription**, IPTVnator is particularly convenient because it can manage the playlist, EPG, favorites, categories and playback from one application.

**Never download "IPTVnator Premium", "activated IPTVnator", or IPTV subscriptions from unofficial IPTVnator websites.** The project specifically warns that IPTVnator is free/open-source and does not sell IPTV subscriptions or channels.

Explore the IPTV setup further
