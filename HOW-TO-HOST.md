# Hosting this folder

Everything here is already built. Put these files on any static host that serves
over **HTTPS** - the webcam will not work over plain HTTP. Relative asset paths
are used throughout, so the same folder works at a domain root or in a
sub-folder such as https://you.github.io/my-study/.

## GitHub Pages

GitHub does not unzip archives. Extract this zip on your computer first, then
upload what is inside it - not the zip, and not the folder wrapping it.

1. Create a **public** repository (Pages on private repos needs a paid plan).
2. **Add file -> Upload files**, drag in `index.html` and the `assets`,
   `mediapipe` and `videos` folders. Commit.
3. **Settings -> Pages -> Source: Deploy from a branch**, branch `main`,
   folder `/ (root)`. Save.
4. After a minute the site is at https://USERNAME.github.io/REPOSITORY/

When it is right, `index.html` sits at the top level of the repository next to
`assets`, `mediapipe` and `videos`.

## Cloudflare Pages

**Workers & Pages -> Create -> Pages -> Upload assets**, drag in this folder or
the zip as-is, deploy.

## Netlify

Drag this folder onto the Sites list, or **Add new site -> Deploy manually**.

## Downloads at the end of a run

- **CSV** - one row per estimate: gaze position and video time.
- **Detailed CSV** - 77 columns: velocity, acceleration, fixation/saccade/blink
  labels, iris offsets, eye openness, head pose, and 18 face landmarks.
- **JSON** - metadata, calibration quality, drift correction and a fixation
  summary.

## Changing the video

Replace `videos/test-video.mp4` with your own MP4 using the same filename, then
redeploy. Changing the filename or any setting in `src/config.ts` needs the
source project and a rebuild.
