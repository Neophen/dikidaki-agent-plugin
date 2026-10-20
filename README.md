# DikiDaki

Help your class move from “who has replied?” to a clear next step. This plugin
lets an adult class administrator create **news, polls and questions** from
Codex or Claude Code, using DikiDaki’s own class permissions.

![DikiDaki](assets/icon.png)

## Connect your class

Install the plugin and choose **Authenticate** for the DikiDaki MCP server.
Sign in with your existing DikiDaki account, choose one class, select the creation
tools to allow and set an access duration of 1, 7 or 30 days. No API keys or
environment variables are needed. A current administrator role and an active
class are required. Normal DikiDaki plan limits apply.

Browser authorization currently supports local Codex and Claude Code clients.
Hosted ChatGPT and Claude web authorization is not yet supported.

Directory publication is pending review. This repository is a direct distribution
option; it does not imply approval by OpenAI or Anthropic.

For Claude Code, add this marketplace and install the plugin:

```sh
claude plugin marketplace add Neophen/dikidaki-agent-plugin
claude plugin install dikidaki@dikidaki
```

Then open `/mcp` and authenticate DikiDaki. For Codex, install the same plugin from this repository:

```sh
codex plugin marketplace add Neophen/dikidaki-agent-plugin
codex plugin add dikidaki@dikidaki
```

Choose Authenticate for DikiDaki. If your client does not yet support plugins,
add the server directly:

```sh
codex mcp add dikidaki --url https://dikidaki.lt/mcp
codex mcp login dikidaki
```

Use one installation method per client to avoid duplicate tools. Authorize another
connection separately if you want to work with a second class.

## Try it

- “Post class news: Please bring a water bottle for Friday’s trip.”
- “Create a children’s participation poll: Will your child join Friday’s trip?”
- “Ask the class: Where should we meet before the trip?”

For a choice poll, supply the options and whether people may select one answer or
several. For participation, choose whether parents answer for themselves or their
children. Missing decisions are clarified before publication. The skill follows
the language and wording you provide, including English, Lithuanian and Polish.

## Publication and permissions

Posts go live immediately as the administrator who authorized the connection,
and families receive normal notifications. Ask for a draft when you want to
review wording first. The server exposes only `get_connection`, `create_news`,
`create_poll` and `create_question`. It cannot read chats, list classmates, upload
images, manage money, vote, answer questions, edit or delete posts. Access applies
to exactly one class and cannot be changed through tool arguments.

Revoke a connection at any time under **Class → AI connections** at
https://dikidaki.lt/mcp-connections. Losing administrator access also revokes the
connection. Access tokens expire and refresh only within the authorization’s
chosen lifetime. The server stores token hashes, not reusable token secrets.

## Privacy and data handling

The declared remote service is https://dikidaki.lt/mcp. It receives the post text
and options you ask to publish, checks the authorizing account and class, and
stores successful publications in that class. `get_connection` returns only the
class name, role, granted tools and expiry. It does not retrieve class content.
There are no scripts, hooks, tracking SDKs or additional network destinations in
this package. Your chosen agent provider separately handles your conversation
under its own policies. Do not paste private exports into an agent unless you
intend to share them with that provider.

Publications remain ordinary class content under DikiDaki’s retention and deletion
rules; revoking the plugin does not remove previously published posts. This plugin
is intended for adult parents and guardians, not independent child accounts.

[Privacy policy](https://dikidaki.lt/privacy?lang=en) ·
[Terms of service](https://dikidaki.lt/terms?lang=en) ·
[Contact support](mailto:mykolas@mdis.lt)

Publisher: **MB "MDIS"**. The MIT license covers this plugin package only.
It does not license the hosted DikiDaki service, its private application source,
customer data or DikiDaki trademarks. Bundled branding identifies this integration.
