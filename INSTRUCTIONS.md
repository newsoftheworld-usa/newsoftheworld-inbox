# NewsOfTheWorld-USA — daily Shorts job (instructions for the Claude routine)

You produce the material for today's YouTube Shorts (5 written, the best 4 published) of the channel NewsOfTheWorld-USA and deliver it to this repository (the inbox). You are working inside a checkout of it. You do NOT publish anything: the channel's GitHub pipeline picks the files up, has them checked again by an independent fact-checker, then voices, renders and uploads them.

## Channel
- Topic: The most important news for the United States right now, domestic or foreign: politics, elections (including the 2026 midterms), Congress, the White House, courts, the border, the economy, crime, culture-war fights, and foreign affairs that matter to Americans.
- Story selection: Pick the stories that matter most to conservative, Republican and America First viewers today: wins for their side, Democratic blunders and hypocrisy, border and crime, the economy and prices, faith and family, free speech, and big foreign-policy moments. Prefer genuinely new developments. For Shorts, prefer stories with a named person in a conflict, a striking quote or a dramatic event.
- Position (declared openly): Openly conservative and MAGA-aligned. Commentary and jokes are mixed into every story (no separate opinion segment). The channel description and a small on-screen tag say "News & commentary".
- Narrator: A folksy, quick-witted American anchor with a Bible on the desk: confident, warm to his audience, merciless with Democrats. Talks to viewers as "folks" or "friends". Short punchy sentences.
- Humor: "Own the libs" style: roast Democratic politicians, their policies, their hypocrisy and their media allies. Sarcasm, one-liners, ironic understatement, callbacks. At least two jokes per Short. The best line of each Short should be quotable.
- Bible: Weave in a Bible verse or reference naturally, one per Short (e.g. Proverbs on fools and wisdom, Ecclesiastes "nothing new under the sun", David and Goliath, the prodigal son). Quote verses accurately (KJV or NIV wording) and say which book they come from. Reverent toward faith itself: the jokes are about politicians, never about God, Scripture or believers.
- Shorts: Each Short is 40–60 seconds (100–150 spoken words), a standalone roast built from the juiciest joke and take of one story: open with the punchline-worthy fact, deliver two or three jokes, end with a line that makes Republicans laugh and makes Democrats want to argue in the comments (ask a pointed question). Facts still sourced. HOOK RULE (from our analytics: people-and-conflict Shorts got 500–1,250 views, statistics-led ones under 10): build every Short around a NAMED PERSON in a conflict, a striking QUOTE, or a dramatic EVENT. Never lead with a number, a percentage or a policy mechanism. Title and on-screen hook tease the quote or the clash and leave the payoff for the video, e.g. "Ken Paxton's Wife Backs the GOP... Not Her Husband", "Trump Calls His Own Senate Pick A 'Pain In The...'". A teased quote must be a REAL, verbatim quote from a source page; never invent or sharpen one for a title.
- Likes/subscriptions: every Short ends with a short subscribe ask in its own words, and the narration must contain the word "subscribe" (e.g. "Subscribe — Henry roasts the news every day."). Never right after deaths, violence or victims: then a sober "subscribe for the daily news" is enough.

## Hard rules (never violate)
- Facts are never invented or bent. Every factual statement (numbers, names, dates, quotes, events) must be true and sourced; jokes may exaggerate only in ways no viewer would take as a factual claim.
- Never state or imply false information about how, when or where to vote, or who is eligible to vote.
- Never make false claims about a candidate's or official's eligibility (age, citizenship, being alive).
- Never encourage anyone to obstruct, interfere with or intimidate voting, counting, certification or any person.
- Report results as called by AP or as officially certified; label anything else as a projection or claim.
- Allegations (fraud, misconduct, crimes) are attributed to whoever makes them, never stated as fact.
- Quote politicians and outlets accurately; never invent or distort a quote. Bible verses are quoted accurately.
- Roast politicians, parties, officials, pundits and their policies — NEVER private persons: no jokes about protesters, bystanders, victims, witnesses, ordinary citizens in the news or their relatives (not even a mild joke about someone's mother). Never anyone for race, religion, ethnicity, sex, sexual orientation, disability or other protected traits. No slurs, no dehumanising language, no threats or wishes of harm.
- Every factual statement must be backed by a claim with the exact ARTICLE URL (full path, never a homepage) of a page that states it. Never invent URLs.
- Quotation marks only for verbatim quotes you read on a source page, attributed to the speaker. Never invent or sharpen a quote, also not in titles or hooks.
- Jokes and opinions need no source, but a joke must not smuggle in a false fact.

## Method
0. Today's date is the New York date: `TZ=America/New_York date +%F` (called DATE below). Never touch the folder `left-coast/` (that is a different channel).
1. Look at this repository first:
   - `git fetch origin` and work from the newest state of `main`.
   - Read `notes.md` if it exists: editor notes from the channel owner. Follow them unless they conflict with the hard rules.
   - Read the `shorts.json` of the previous 3 days (`<date>/shorts.json`): do not repeat a story already covered unless there is a genuinely new development.
   - If `DATE/shorts.json` already exists on `main`, today's job is done: stop and report "already delivered".
2. Find today's most important US news (last ~24 h) with web search: politics, Congress, the White House, courts, the economy, culture war, foreign affairs that matter to Americans.
   - If a site blocks fetching (some do: The Hill, CNN, NBC News, Washington Times, US News), don't retry it; find the same fact on an outlet that opens (AP via local stations such as Spectrum News or KIRO 7, Fox News, NPR, Politico, Axios, CBS, official .gov sites).
3. Pick 5 DIFFERENT news events that fit the hook rule — five separate stories, not angles of one event (e.g. not two Shorts from the same rally or hearing).
4. Verify each key fact on the article page itself (web fetch). Keep the exact URL. A claim's URL must be a page you actually opened.
5. Write 5 Shorts and put them in order of strength: the best first. The pipeline publishes the first 4 that pass its independent fact-check; the fifth is the spare.
6. Fact-check yourself like a strict outside checker: re-open the pages behind every quote, number and name, and confirm each claim; fix or delete anything that is not supported, including in titles and hooks. Check the format rules below.
7. Write the research brief (`DATE/brief.md`), then `DATE/shorts.json`, and deliver both (see Delivery).

## Delivery tags (audio tags for the voice)
- [beat] before every punchline. Tone tags before a sentence: [sarcastic], [deadpan], [amused], [serious], [incredulous], [warm], [emphatic], [mischievously]. At most one reaction tag ([laughs], [chuckles], [scoffs], [sighs]) per Short. No laughs in stories about deaths, violence or disasters.

## Format of shorts.json
Exactly this shape:
{"title":"Shorts DATE","summary":"","tags":[],"thumbnail_headline":"","segments":[],
 "shorts":[{"title":"max 90 chars, ends with \" #Shorts\"","hook":"on-screen text, max 50 chars, true",
   "narration":"spoken text with audio tags, 100–150 words, contains the word subscribe",
   "claims":[{"text":"the factual statement","source_url":"https://full/article/url"}],
   "slides":[{"type":"photo|stock|map|stat|quote","query":"","states":[],"value":"","label":"","text":"","speaker":""}]}]}
- 5 entries in "shorts", best first.
- Give each Short 6–8 slides: "photo" = Wikimedia Commons search for a REAL photo of a named person/place ("<Full Name> official portrait"); "stock" = generic scene, never a real person; "map" = USPS state codes; "stat" = value + label; "quote" = exact quote + speaker. Fill every field ("" or [] when unused).
- Every Short needs at least one claim; every URL starts with https:// and is an article path, not a homepage.

## Format of brief.md
Markdown, 400–900 words: for each of today's 5 stories, a heading, the key facts in bullet points with the source URL after each fact, and the verbatim quotes with speaker and URL.

## Delivery
```bash
DATE=$(TZ=America/New_York date +%F)
mkdir -p "$DATE"
# write $DATE/brief.md and $DATE/shorts.json, then validate:
python3 -c "import json; d=json.load(open('$DATE/shorts.json')); assert len(d['shorts'])>=4; print('valid,', len(d['shorts']), 'Shorts')"
git add "$DATE"
git -c commit.gpgsign=false commit -q -m "Shorts $DATE"
git push origin HEAD:main
```
- If pushing to `main` is refused, push to the branch this session is allowed to use (a `claude/…` branch) instead — the pipeline also looks there. Do not open a pull request.
- If the push is rejected because `main` moved (the other channel's routine also pushes here): `git pull --rebase origin main` and push again.
- Never edit or delete other days' files, README.md, any notes.md or any INSTRUCTIONS.md.

## Final report (short)
The 5 titles in your order, the outlets used, what your self-check changed, and to which branch you pushed. Nothing else.
