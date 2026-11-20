# Privacy Policy — QAlity Discord Bot

> **Status: pre-release draft.** The application is under active development. Everything below is
> accurate for the version running today, and that version is a pre-release build: the intents the
> application declares, the data it handles, and the third-party services it can be connected to may
> all change before general availability. Any such change is republished on this page with a new
> effective date and a note on what changed, so check the effective date before relying on it.
> Fields still shown as `[BRACKETED]` are not filled in, which means this draft is **not yet the
> operative privacy policy** — the operator and contact address in §10 are still placeholders, and
> no effective date is set.

**Effective date:** [DATE]
**Operator / data controller:** [LEGAL ENTITY NAME], [ADDRESS] — contact: [PRIVACY EMAIL]
**Application:** `wiki-bot` (Discord application ID `1573304492886204447`), operated by [LEGAL ENTITY
NAME] on behalf of its business customers ("the **Bot**").

## 1. What the Bot does

The Bot is a Discord bot installed in a single server chosen by our customer. It watches **one
category** of text channels in that server, and copies what is decided there into the customer's own
document wiki, so that a conversation becomes a durable page. A person in the server can also run
slash commands (`/decision`, `/note`, and a thread-to-page action) to file a specific message or
thread.

The Bot does not have a website, does not log people in, does not run advertising, and does not
profile anyone. Its only function is to move text from the server's own channels into the customer's
own systems.

## 2. Data we collect

We receive only the data Discord makes available to a bot through the Discord API. Specifically:

| Source | Data | Why |
| --- | --- | --- |
| `GUILDS` intent | Server and channel names, channel IDs, the category the customer selected | to know which channels are in scope, and to keep that list current when channels are added or removed |
| `GUILD_MESSAGES` intent | Message ID, channel ID, timestamp, author ID, message content of messages in the selected category | to identify what was said, and to link back to the original message on the page it files |
| `MESSAGE_CONTENT` intent | The text of messages in the selected category | to summarise and file the decisions in them. This is the whole product; without it the Bot sees no text at all |
| Slash-command interactions | The Discord user ID and display name of the person who ran the command, plus the option they typed | so a filed page says who recorded the decision, and so the reply reaches the person who asked |
| Channel and thread events | Channel/thread name, parent channel, member join/leave of a thread | to notice a new thread that is to be filed as a page |

**We do not** request direct messages, voice audio, voice channel membership, presence/status, the
server member list beyond what the events above carry, any OAuth user token, or any privileged
`GUILD_MEMBERS`, `GUILD_PRESENCES` or `GUILD_MESSAGE_REACTIONS` intent. The Bot's guild permissions
are limited to **View Channels**, **Send Messages** and **Read Message History**; it holds no
administrator, moderation, management, or webhooks permission.

## 3. How the data is used

- To write pages into the customer's wiki: a thread becomes a page, a `/decision` becomes a dated
  decision line, and each entry links back to the Discord message it came from.
- To reply to the command that asked for it, in the channel where it was asked.
- Optionally, with the customer's own summarisation service: an extract of the conversation text is
  sent to an inference endpoint **the customer configures and contracts directly** (see §4) to draft
  a dated summary. [CONFIRM: state whether this feature is enabled for the deployment under review.]
- To operate the service: error handling, rate-limit awareness, and operational logs. Operational
  logs record IDs, timestamps and outcome counts, not message bodies, and credentials are masked by
  the logging layer before anything is written.

We do **not** use Discord content to train machine-learning models, and we do not sell or share it
for advertising.

## 4. Where the data goes

1. **The customer's wiki.** Message content, timestamps, links to the original messages, and the
   display name of the person who filed an item are written into pages in folders of the customer's
   choosing. Pages written by the Bot carry the description marker `qality-discord-bot page`.
   **The customer is the controller of that wiki and decides who can read it.**
2. **The customer's summarisation endpoint**, if configured. Conversation text is sent over HTTPS to
   that provider under the customer's own agreement with them. We neither host nor control it.
3. **The host the Bot runs on** — operated by [us / the customer], in [JURISDICTION/DATA REGION].
4. **Discord**, as the platform the API is provided through, under Discord's own terms.

No data is transferred to any other third party, and nothing is sold.

## 5. Retention

- **On the Bot's host:** no archive of messages is kept. The Bot stores one small operational file,
  `pairing.json`, mapping channel ID → the wiki folder that channel files into. It contains no
  message text and no personal data beyond a channel identifier.
- **In the customer's wiki:** filed pages persist until the customer's own users edit or delete
  them. Retention there is governed by the customer's policy, not ours.
- **Operational logs:** retained for [N] days [AND/OR] rotated by [MECHANISM], with credentials
  masked.

## 6. Your rights, and how to exercise them

If you are a member of a server where this Bot is installed, requests about your data — access,
correction, deletion, objection — should go **first to the owner of that server**, who controls both
the Discord server and the wiki where the content is filed. You may also contact us at [PRIVACY
EMAIL]; we will act on a request that reaches us and, where the request concerns a customer's wiki,
pass it to that customer to action.

Deleting the original Discord message, or deleting the wiki page, removes the content from those
places. Removing the Bot from the server ends all further collection immediately.

[INCLUDE ONLY IF APPLICABLE: GDPR/UK-GDPR legal bases — legitimate interests (operating the
knowledge-capture service the server has chosen to install), consent where required by the server
owner; and the right to lodge a complaint with a supervisory authority.]
[INCLUDE ONLY IF APPLICABLE: standard contractual clauses / UK IDTA for any transfer outside
[JURISDICTION].]

## 7. Security

HTTPS-only, outbound-only connections; the Bot accepts no inbound connections and opens no listening
port. Every credential is held in a file readable by the service account alone (mode `0600`) outside
the application directory, is loaded at start, and is masked in every log line and diagnostic print.
Secrets are never accepted as command-line arguments. Configuration diagnostics print a credential
file's name and its file mode, never its contents.

## 8. Children

The Bot is not directed at children and is available only where Discord's own minimum-age terms are
met. We do not knowingly process children's data; report concerns to [PRIVACY EMAIL].

## 9. Changes

Material changes are posted at [POLICY URL] with a new effective date. [OPTIONAL: notice period.]

## 10. Contact

[LEGAL ENTITY NAME] — [PRIVACY EMAIL] — [POSTAL ADDRESS]
[OPTIONAL: Data Protection Officer / EU or UK representative, name and address.]
