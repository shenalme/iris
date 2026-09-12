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

**Workers & Pages -> Create -> Pages -> Upload assets**, name the project, drag
in this folder or the zip as-is, deploy.

## Netlify

Drag this folder onto the Sites list, or **Add new site -> Deploy manually**.

## What changed in this build

Gaze is now estimated from MediaPipe FaceMesh iris landmarks with head-pose
compensation, replacing WebGazer. The JavaScript bundle dropped from ~2.3 MB to
~0.33 MB because TensorFlow.js is no longer needed. The `mediapipe` folder is
the face and iris model, served from your own site - no third-party requests.

## Changing the video

Replace `videos/test-video.mp4` with your own MP4 using the same filename, then
redeploy. Changing the filename or any setting in `src/config.ts` needs the
source project and a rebuild.
