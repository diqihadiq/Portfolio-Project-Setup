# Collection Guide: LinkedIn Posts and YouTube Transcripts

This guide explains how to collect content from LinkedIn and YouTube for this research project.

---

## LinkedIn Posts (Manual Collection)

LinkedIn blocks automated scraping, so posts need to be collected manually.

### Steps

1. Open the expert's LinkedIn profile (links in `/research/sources.md`)
2. Click on their name to go to their profile
3. Scroll down to the "Activity" section and click "Show all activity"
4. Click "Posts" to filter only their posts (not comments or reactions)
5. Scroll through and look for posts about AI, SEO, content production, workflows, or tools
6. For each relevant post: copy the full text, the date, and the URL
7. Paste into the expert's `/research/linkedin-posts/{name}/posts.md` file using this format:

```
### Post 1
**Date:** 2025-03-15
**URL:** https://linkedin.com/posts/...
**Content:**
[full post text here]

---
```

### What to look for

Prioritize posts that contain:
- Specific workflows or step-by-step processes
- Data, numbers, or experiment results
- Tool recommendations with context (not just "use this tool")
- Opinions that go against common advice (high signal)
- Screenshots or carousels with frameworks (describe what they show)

Avoid posts that are just:
- Motivational content without substance
- Reposts of other people's content
- Generic "AI is changing SEO" takes without specifics

### Target: 5-10 posts per expert (quality over quantity)

---

## YouTube Transcripts (via yt-dlp)

yt-dlp is a free command-line tool that can extract transcripts from YouTube videos without needing to watch them.

### Installation

**Mac:**
```bash
brew install yt-dlp
```

**Windows:**
Download the .exe from https://github.com/yt-dlp/yt-dlp/releases and add it to your PATH.

Or install via pip (works on both):
```bash
pip install yt-dlp
```

### Extract a transcript

Basic command to get a transcript (subtitles) from a video:

```bash
yt-dlp --write-auto-sub --skip-download --sub-format vtt --sub-lang en -o "transcript" "https://www.youtube.com/watch?v=VIDEO_ID"
```

This will save a `.vtt` file. To convert it to clean readable text, run:

```bash
yt-dlp --write-auto-sub --skip-download --sub-format vtt --sub-lang en --convert-subs srt -o "transcript" "https://www.youtube.com/watch?v=VIDEO_ID"
```

Then open the `.srt` file - it will be readable plain text with timestamps.

### Example: Kevin Indig SEO interview

```bash
yt-dlp --write-auto-sub --skip-download --sub-lang en -o "kevin-indig-majestic" "https://www.youtube.com/watch?v=PASTE_VIDEO_ID_HERE"
```

Save the output to `/research/youtube-transcripts/kevin-indig/transcripts.md`

### Priority videos to collect

| Expert | Video | URL |
|--------|-------|-----|
| Kevin Indig | SEO in 2025 (Majestic interview) | Search "Kevin Indig SEO in 2025 Majestic" on YouTube |
| Gael Breton | Automate $10K/Month in Tasks with AI | https://www.youtube.com/watch?v=blG6gss-mUY |
| Koray GUBUR | Complete AI Agents + Semantic SEO interview | https://www.youtube.com/watch?v=mSHq_HxOyTA |
| Kyle Roof | On-page SEO experiment videos (2024-2025) | Search "Kyle Roof PageOptimizer Pro 2025" on YouTube |
| Aleyda Solis | BrightonSEO or MozCon talks | Search "Aleyda Solis BrightonSEO 2025" on YouTube |

### If yt-dlp does not find auto-generated subtitles

Some videos only have manual captions or none at all. In that case:

Option A - Use Supadata (free tier available):
1. Go to https://supadata.ai
2. Paste the YouTube URL
3. It will return a transcript you can copy

Option B - Use YouTube's built-in transcript:
1. Open the video on YouTube
2. Click the three dots (...) below the video
3. Click "Show transcript"
4. Copy and paste the full text

---

## Saving Your Collected Content

After collecting, save everything in the correct folder:

```
LinkedIn post from Kevin Indig  ->  /research/linkedin-posts/kevin-indig/posts.md
YouTube transcript from Gael    ->  /research/youtube-transcripts/gael-breton/transcripts.md
Newsletter or blog article      ->  /research/other/{expert-name}-{source}.md
```

Commit regularly - do not wait until everything is collected to push to GitHub.

```bash
git add .
git commit -m "Add Kevin Indig LinkedIn posts and Gael Breton YouTube transcript"
git push
```
