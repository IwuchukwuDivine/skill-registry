# Hermes Tweet Usage Notes

## Good Prompts

- Search X/Twitter for recent posts about a product launch and summarize the
  common questions.
- Read this tweet and its replies, then identify actionable feedback.
- Monitor these accounts for new posts about an incident.
- Export followers for this account and group them by likely audience.
- Draft a reply, show it to me, and wait for approval before posting.

## Safety Checks

- Treat read-only analysis as the default mode.
- Ask for explicit approval before write actions.
- Do not reveal API keys, environment values, or private runtime details.
- Do not claim a post was created unless the plugin returns a successful result.
- If the plugin is not installed or `XQUIK_API_KEY` is missing, tell the user the
  setup step that is missing.

## Public References

- Hermes Tweet repository: <https://github.com/Xquik-dev/hermes-tweet>
- Hermes plugin install command:
  `hermes plugins install Xquik-dev/hermes-tweet --enable`
