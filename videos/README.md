# Experiment video

`test-video.mp4` is a placeholder: a moving dot on a dark field with a burned-in
timecode. It exists so the pipeline can be checked end to end — after a run, the
recorded `gazeX`/`gazeY` should roughly follow the dot at the matching
`videoTime`, and the burned-in clock gives you something to eyeball against.

## Using your own video

1. Drop your file in this folder, e.g. `public/videos/my-stimulus.mp4`.
2. Point `videoPath` in `src/config.ts` at it:

   ```ts
   videoPath: 'videos/my-stimulus.mp4',
   ```

   The path is relative to `public/` with no leading slash — it is resolved
   against the deployment base path at runtime, so it keeps working under
   `https://USER.github.io/REPO/`.

Use H.264 in an MP4 container with `faststart` for the widest browser support:

```bash
ffmpeg -i input.mov -c:v libx264 -crf 22 -pix_fmt yuv420p \
  -c:a aac -movflags +faststart public/videos/my-stimulus.mp4
```

Large files count against your repository size. GitHub blocks pushes over 100 MB
per file and a Pages site is capped at 1 GB, so keep stimuli lean or host them
elsewhere and use an absolute URL in `videoPath`. If you do host the video on
another domain, that server must send permissive CORS headers.
