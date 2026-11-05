# Plan — Landing page: simpler downloads, a cleaner token example, Windows in the AI section, quieter trust cards, and "Works with"

**Status:** approved 2026-11-05, every decision as recommended. D1–D3 and D5–D8
built the same day (see Outcome); D4 (a Windows 0.7.8 build) is open, in the core repo.
**Requested by:** hants
**Applies to:** `site/index.html` (and `README.md` where noted). D4 is about
the core repo (`fordham_deid_service`), because the site's wording depends
on it.

## Approval

- [x] **Approve**: build every decision as ticked below
- [ ] **Approve with changes**: see the notes on each decision
- [ ] **Do not approve**

Notes:

Each decision has a recommendation. Tick **Approve** to take it, **Do not
approve** to leave that part of the page as it is, or **Other** and say what
you'd like instead.

## What I checked

**Copy and restore, the AI terminal and the rest on Windows.** In the core
repo they're designed and coded for Windows too:

- **Copy twice:** Ctrl+C twice on Windows, read from Windows'
  clipboard-change messages (`2026-10-24-copy-and-restore.md`).
- **The AI terminal:** runs on Windows' ConPTY; `claude`, `codex`, `gemini`
  and `opencode` run natively (`2026-10-26-ai-terminal.md`).
- **Desktop integration:** `DESKTOP.md` describes the notification-area icon
  and Explorer's right-click (**De-identify with De-ID**, and **Send To →
  De-ID**). The De-ID folder is pinned to Quick access.

**But no Windows build with any of it exists yet.** The AI terminal plan says
"built Mac first … Windows and Linux after the Mac" (D13 there). The newest
Windows installer, public or private, is `desktop-v0.4.3-windows`, and
`release/` holds no newer `.exe`. The copy-and-restore plan also flags one
thing to test on Windows: Office sometimes writes the clipboard twice for one
copy, which could trigger copy twice by mistake. So a Windows visitor today
downloads 0.4.3, which has none of the 0.5 features.

**What connects to De-ID today** (from `DESKTOP.md` and
`docs/ai-and-workflow.md`):

| How it connects | With | Mac 0.7.8 | Windows 0.4.3 |
|---|---|---|---|
| Copy and restore | ChatGPT, Claude, Gemini or any AI chat, in a browser or an app | yes | not yet |
| The AI terminal | Claude Code, Codex, Gemini CLI, Antigravity, OpenCode, Aider, or any command you add | yes | not yet |
| De-ID's read-only tool (MCP) | Claude Code, Claude Desktop, Copilot in VS Code | yes | yes |
| Files for AI | Any tool that reads Markdown or CSV, including a local model (then nothing leaves the computer) | yes | yes |

ChatGPT's desktop app can't use the read-only tool: it connects only to tools
hosted on the internet. With ChatGPT, it's Copy and restore or Files for AI.

## Decisions

### D1. The SHA-256 lines on the download cards

The Mac DMGs are signed and notarized, so macOS checks them itself; a
checksum adds nothing for almost everyone. The Windows installer isn't
signed, so there a checksum is the only integrity check, but few people know
how to use one. (Separately: 0.7.8's `SHA256SUMS.txt` lists only the Apple
silicon DMG. The release notes' table has both.)

- **A.** Take them off the cards, and add one line at the foot of the
  download section: "Checksums for each file are in the release notes."
  **Recommended:** the cards get simpler, and anyone who checks downloads
  knows where to look.
- **B.** Remove them with no mention at all.
- **C.** Keep them, folded behind "Verify the download (optional)" on each
  card.

- [x] **Approve** A
- [ ] **Do not approve**
- [ ] **Other:**

### D2. The token example box

Today the dark box holds the token line and two sentences of explanation. I
agree with you: the box should show only what the output looks like, and the
explanation should read as ordinary text.

- **A.** The box keeps only
  `Candidate: <PERSON_7f3a2c> · <EMAIL_ADDRESS_57898c> · <PHONE_NUMBER_b3179c>`.
  The two sentences move just below it, as ordinary text in the section's
  muted grey. **Recommended.**
- **B.** As A, plus a small caption above the box: "A clean copy reads like
  this:".
- **C.** Leave it as it is.

- [x] **Approve** A
- [ ] **Do not approve**
- [ ] **Other:**

### D3. "Everyday AI · Mac": writing it for Windows too

These are the places the page talks about the Mac where the feature is meant
for both:

- the label "Everyday AI · Mac";
- "taken out on your Mac first";
- "⌘C twice", in the example, the first card and the "Anyone pasting into an
  AI chat" card;
- "From Finder and the menu bar";
- the note "Mac only; the Windows version is still 0.4.3";
- the FAQ answers "On your Mac only" (token links) and "Can several people
  use it on one Mac?".

The agent audit stays Mac only: it uses macOS's `eslogger`.

- **A.** Write it for both now: "⌘C twice on a Mac, Ctrl+C twice on
  Windows", "the menu bar or the notification area", "Finder or Explorer",
  "your computer". Until a Windows build ships (D4), add one line: "Coming to
  Windows in the next release. Today's Windows download is 0.4.3."
  **Recommended:** the page describes the product as it's built, and a
  Windows visitor isn't promised something their download doesn't have.
- **B.** Write it for both with no caveat. Only right once D4 ships; until
  then a Windows user installs 0.4.3 and finds none of it.
- **C.** Keep it Mac only until Windows ships, then rewrite.

- [x] **Approve** A
- [ ] **Do not approve**
- [ ] **Other:**

### D4. A current Windows build (core repo)

This decides how long D3's caveat stays. The Windows build process is in
place (one x64 installer for Intel, AMD and ARM PCs).

- **A.** Build a Windows 0.7.8 installer next, do the hands-on on Windows
  (copy twice with Office, the AI terminal with Claude Code and Codex, the
  right-click entry), publish it on the public repo, and then drop D3's
  caveat. **Recommended:** the page can then say "Mac and Windows" without a
  footnote, and the Windows card stops being "Earlier version".
- **B.** Keep Windows at 0.4.3 for now.

- [x] **Approve** A
- [ ] **Do not approve**
- [ ] **Other:**

### D5. The trust cards: no code labels, green titles

Remove the six code-style labels (`cloud calls: 0`, `under the boxes:
nothing`, `second read: clean`, `spot check: 0 missed`, `repeat-check:
identical`, `audit: 0 flags`). Each card's title ("Everything stays on your
machine", and the rest) turns green, in the same font. The question is which
green.

- **A.** The brand green the section labels and links already use (`--accent`:
  `#4D7C0F` on light, `#A3E635` on dark). **Recommended:** one green across
  the page.
- **B.** The green the code labels used (`--good`: `#15803d` on light,
  `#34d399` on dark). A truer green, but a second one on the page.

- [x] **Approve** A
- [ ] **Do not approve**
- [ ] **Other:**

### D6. Remove "Watch the folders, not just the door." (the agent audit animation)

You'd like to save it for a later section on auditability: agent audits with
the human soft and hard audits.

- **A.** Remove the section and its CSS. Keep the two short trust cards that
  mention audits ("A person checks, and it's scored" and "See who actually
  opened what"), and drop the latter's "Watch one run ↓" link. The animation
  stays in git history for the auditability section;
  `git log -S 'class="stage"' -- site/index.html` finds the last commit that
  has it. **Recommended:** both audits are real reasons to trust it today,
  and one line each is enough until the full story.
- **B.** Remove the section and both audit cards, saving all of auditability
  for later. The trust grid drops to four cards.
- **C.** Keep the section.

- [x] **Approve** A
- [ ] **Do not approve**
- [ ] **Other:**

### D7. A new "Works with" section

My view: yes. It answers the first question most visitors have ("does it
work with what I already use?"). It also gathers the four ways De-ID meets an
AI in one place; today they're spread across three sections.

The content would be the table in "What I checked", written for visitors:
one row per way it connects, the tools in each, and which platforms have it.
It ends with the ChatGPT desktop note.

Where it goes:

- **A.** Its own short section right after "Everyday AI", before "Built to be
  checked". **Recommended:** "Everyday AI" shows how, and this lists with
  what, before the page turns to trust.
- **B.** At the end of "For AI agents", where the animation was.
- **C.** A single line of names under the hero.

- [x] **Approve** A
- [ ] **Do not approve**
- [ ] **Other:**

### D8. Names or logos in "Works with"

- **A.** Names only, as small labels (`Claude Code`, `ChatGPT`, `Gemini
  CLI` …), in the page's own style. **Recommended:** other companies' logos
  are their trademarks, can read as a partnership or endorsement, and some
  (OpenAI's, Google's) come with usage rules. Names are plain description,
  and they need nothing new on the page.
- **B.** Logos where a free icon exists (Simple Icons has several), names
  for the rest.

- [x] **Approve** A
- [ ] **Do not approve**
- [ ] **Other:**

## After approval

I build what's ticked in `site/index.html` (and `README.md` for D1), then:

- run the deploy workflow's check that the page loads nothing from other
  sites;
- check the page in light and dark mode and at phone width;
- send you screenshots.

Nothing is committed or pushed until you say so. D4 is separate work in the
core repo.

## Outcome

Built 2026-11-05 in `site/index.html`, not yet committed.

- **D1:** the three checksum lines are off the download cards. The foot of the
  download section now says "Checksums for each file are in the release
  notes." `README.md` had no checksums, so it's unchanged.
- **D2:** the dark box holds only the `Candidate: …` token line. The two
  sentences follow it as grey text.
- **D3:** "Everyday AI" (no "· Mac") now covers both platforms:
  - "copy twice" in the example, and "hold ⌘ (Ctrl on Windows)";
  - the De-ID folder in "your home folder";
  - "From Finder or Explorer", with the menu bar or the notification area;
  - "your computer" in the lead and the token FAQ, and "Can several people
    use it on one computer?";
  - the "Anyone pasting into an AI chat" card gives both keys.

  The note at the end of the section starts "**Coming to Windows in the next
  release.** Today's Windows download is 0.4.3." The agent-audit card still
  says Mac only.
- **D4:** open. Once a Windows 0.7.8 installer is published, the site needs
  four changes:
  - drop D3's caveat line;
  - turn the two "Windows: next release" labels in "Works with" green;
  - point the Windows card at the new installer and drop its "Earlier
    version" label;
  - update the hero line.
- **D5:** the six code labels are gone, and the trust card titles use
  `--accent`.
- **D6:** the audit section, its CSS and the `--bad` colours are removed, and
  so is the "Watch one run ↓" link. Both audit cards stay. The animation is
  in commit `f7bab45` and later: `git log -S 'class="stage"' -- site/index.html`.
- **D7, D8:** the new section "Works with: The AI tools you already use." sits
  between "Everyday AI" and "Built to be checked". Four cards (Copy and
  restore, the AI terminal, the read-only tool, Files for AI) list tools by
  name, and Mac and Windows labels show what each platform has today. It ends
  with the ChatGPT desktop note and a line that names belong to their owners.

**Checked:**

- the deploy workflow's check: no scripts, nothing fetched from other sites;
- the HTML structure;
- light and dark mode, at desktop and phone width.

One thing turned up and was fixed: the site's `.card .n` style (the step
numbers in "How it works") turned the grey "Windows: next release" label big
and green. A more specific `.plats .pill` rule fixes it.
