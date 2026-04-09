# Wix A/B Audio Comparison Player

This is a self-contained player for comparing two versions of the same song in sync.

## What it does

- Loads two audio files.
- Starts both together using the browser's Web Audio clock.
- Only one version is heard at a time.
- Lets the user switch between the versions during playback.
- Includes play, pause, and seek controls.

## Files

- `index.html` — the player.
- `.nojekyll` — tells GitHub Pages not to apply Jekyll processing.

## GitHub Pages setup

1. Create a new GitHub repository.
2. Upload `index.html` and `.nojekyll`.
3. In the repository, go to **Settings** → **Pages**.
4. Under **Build and deployment**, choose **Deploy from a branch**.
5. Choose your main branch and the root folder.
6. Save.
7. Wait for GitHub Pages to publish the site.

## Recommended repo structure

You can also create an `audio` folder for your example files:

- `audio/song-mixed.wav`
- `audio/song-unmixed.wav`

## Player URL format

Use query parameters to tell the player which files to load.

Example:

```text
https://YOUR-USERNAME.github.io/YOUR-REPO/?title=Track%20Comparison&mixed=https://YOUR-USERNAME.github.io/YOUR-REPO/audio/song-mixed.wav&unmixed=https://YOUR-USERNAME.github.io/YOUR-REPO/audio/song-unmixed.wav&mixedLabel=Mixed&unmixedLabel=Unmixed&accent=%23ffffff
```

## Wix embed

In Wix, use an **Embed a site** or HTML iframe-style embed and point it to the full player URL.

## Notes

- The two audio files should be exported from the same timeline and line up exactly.
- If one file has extra silence at the front, the comparison will not feel correct.
- Large WAV files sound great but load more slowly than compressed files.
