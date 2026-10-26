# Claude Tag setup

Checklist for enabling Claude Tag (Claude in Slack) for this organization.
Setup itself happens in Slack and in claude.ai admin settings, not in this repo.
Claude Tag is in public beta, so behavior may change.

Admin page: <https://claude.ai/admin-settings/claude-tag>

## 0. Prerequisites

- [ ] Team or Enterprise plan on claude.ai (no ZDR or CMEK policy)
- [ ] Routines enabled: Admin settings > Capabilities > Remote sessions > Routines
- [ ] You hold the **Owner** role in the Claude organization
- [ ] A Slack workspace admin is available while you pair (codes expire after 15 minutes)
- [ ] Usage credits loaded (Team plans): <https://claude.ai/admin-settings/usage>
- [ ] A public Slack channel for the pilot
- [ ] If services restrict by IP, file the network-requirements request early

## 1. Pair the Slack workspace

1. Install the Claude app: <https://claude.com/claude-for-slack> > **Add to Slack**.
2. In any channel: `/invite @Claude`, then send `@Claude connect` (no other text).
   Only a Slack workspace admin can run this. Claude replies with a one-time code.
   On Enterprise Grid, paste the `enterprise_` code, not the `workspace_` one.
3. Paste the code on the setup page and click **Pair workspace**.

## 2. Buy credits (only if the page shows this step)

Enter an amount and click **Buy now**, or **Skip** and buy later.

## 3. Launch

1. Set the monthly spend limit (`$2,500` is preselected), unless the credits step was shown.
2. Select at least one public channel for Claude to join.
3. Leave **Let members know they can now tag Claude** on, or turn it off to skip the DMs.
4. Click **Launch Claude Tag**.

## 4. Give Claude access to tools

- **GitHub:** a GitHub org owner installs the Claude GitHub App, then grant
  `lostempire/friendly-engine` under **Repositories** on the admin page.
- **Other tools:** create a mailbox for Claude (for example `claude@yourcompany.example.com`),
  add it to each tool as a member with a read-only role, create an API key there, and add it as
  a connection in an Access bundle. Do one tool end to end before the next.

## 5. Verify

In the pilot channel:

```text
/invite @Claude
@Claude summarize what this channel decided this week and list any open questions
@Claude what can you access from this channel?
@Claude list the open pull requests in lostempire/friendly-engine and who each one is waiting on
```

Passed when Claude replies in a thread, the reply ends with a model footer and a **Configure** link,
the second reply lists connected tools, and the third lists the pull requests.

Troubleshooting: "Claude isn't on in this channel yet" means launch is not finished.
No reply at all means the channel isn't covered.

## Message for the Slack workspace admin

```text
Please install the Claude app (https://claude.com/claude-for-slack) in [workspace]. When that's done, let me know a time that works for the next part: in any channel, run /invite @Claude, then post "@Claude connect" with no other text and send me the code it returns. Pick a channel that belongs to just [workspace]. The code expires 15 minutes after Claude posts it, so I'll redeem it right away. What it can access: https://claude.com/docs/claude-tag/admins/for-slack-admins
```

## Draft custom instructions

Paste into **Custom instructions** on **Default Slack** and adjust.

```text
- Reply in the language the person wrote in.
- Be concise. Lead with the answer, then the detail.
- Work in the existing thread; do not start new top-level messages unless asked.
- For code work, open draft pull requests and never push to the default branch.
- Say what you could not verify instead of guessing.
- Do not take destructive or outward-facing actions without asking first.
```
