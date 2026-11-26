# Hype HUD

What did the audience actually say about the game?

Hype HUD reads the comments under a sponsored YouTube video and reports whether viewers want to play, what is holding them back, whether they come from a competing game, and how they react to the sponsorship. Every number links back to the comments behind it.

**Live site:** https://iamyuhanliu.github.io/hype-hud/

## What it does

- Paste one video link, or import a spreadsheet full of creator links (.xlsx or .csv). Links are found anywhere in the sheet, duplicates and unsupported links are flagged before anything is analysed.
- Compare videos side by side: views, views per subscriber, share of comments about the game, want to play, hesitant, top barrier, competitor players, ad pushback, CPM.
- Click any number to see the comments behind it, with the phrase the model relied on highlighted.
- Export the comparison, the labelled comments, or the original sheet with result columns appended.
- English and Chinese interface.

## How it works

- `index.html` is the whole front end. Spreadsheets are parsed in the browser; only video links are sent to the back end.
- The back end runs as a private Cloudflare Worker and is not part of this repository. It fetches public data from the official YouTube Data API, has Claude label each comment and caches results. API keys never reach the browser.
- YouTube is supported today.

## Limits

- Up to 300 top level comments per video, in YouTube relevance order. This is not a random sample.
- Labels come from a language model. On a 100 comment test set it matched a reference answer on stance for 92 comments and on barrier for 99.
- Commenters are a small and unusual part of the audience. Use the numbers to compare videos and find reasons, not to forecast sales.

Built by Yuhan Liu.
