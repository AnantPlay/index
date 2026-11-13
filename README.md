# AnantPlay index

The list of sources [AnantPlay](https://github.com/AnantPlay/android) shows in *Settings, Sources*. The app carries no sites, channels or links of its own: it reads this file, shows each source with an **Add** button, and loads only what you add.

## Format

`index.json`:

```json
{
  "name": "My index",
  "sources": [
    {"id": "my-sites", "name": "My sites", "description": "Shown under the name",
     "type": "sites", "url": "https://example.com/sites.json"}
  ]
}
```

| Field | |
| --- | --- |
| `id` | Unique within the index |
| `name`, `description` | What the Sources screen shows |
| `type` | `sites`, `playlist` or `deeplinks` (below) |
| `url` | Where the source's file is |
| `languages` | Playlists only, optional: a second M3U of the same streams grouped by language (`group-title` = language) |
| `adult` | `true`: listed only after 18+ is switched on in Settings |
| `default` | `true`: added for people who update from version 2.20.1 or older |

### Types

- **`sites`**: a JSON file of streaming sites in rows: `{"rows": {"movies": [...], "tv": [...], "sports": [...], "anime": [...], "live": [...], "more": [...]}, "languages": {"Spanish": [...]}}`. Each site is `{"name", "url", "mirrors": [], "tags": [], "group", "pick", "index"}`; rows are shown in the order given. [AnantPlay/scraper](https://github.com/AnantPlay/scraper) makes one.
- **`playlist`**: an M3U / M3U8 playlist. Channels are grouped by `group-title`, and by country from the `tvg-id` suffix.
- **`deeplinks`**: a JSON table of title-page addresses per site, `{"host": {"movie": "/movie/{tmdb}", "tv": "/tv/{tmdb}", "episode": "/tv/{tmdb}/{season}/{episode}"}}`. See [AnantPlay/sources](https://github.com/AnantPlay/sources).

## Your own index

Host a file in this format anywhere and add it in the app: *Settings, Sources, Add an index by link*. An older `sources.txt` list (`label|url`, `label|url|18`, `@deeplinks|url`) works too.

## Contributing

Open an issue or a pull request with a source that works and says what it carries. Sources that stop working are removed. This repository holds links to lists, not video.
