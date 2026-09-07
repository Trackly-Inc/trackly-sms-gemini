# Trackly SMS for Gemini CLI

Connect an assistant to Trackly SMS, inspect account setup and senders, and prepare text messages for human approval. This extension contains a remote MCP configuration and a portable skill; it does not contain the Trackly application, credentials, install scripts, or a local server.

## Current availability

As of September 6, 2026, the hosted MCP service is version **1.1.0**, OAuth account connection is enabled, and live SMS through hosted MCP is disabled. Sandbox workflows still require account/sender readiness and stored human approval. Sandbox execution can invoke real account webhooks.

This is a **release candidate**. Native Gemini CLI sign-in, tool execution, refresh, and revocation have not been tested. The service's separate OAuth checks do not establish Gemini compatibility. Extension package version `0.1.0` is independent of the hosted service version.

## Install and connect

Install this public release candidate:

```bash
gemini extensions install https://github.com/It-s-Today-Media/trackly-sms-gemini
```

Inspect `gemini extensions list`, start Gemini CLI, and use `/mcp auth trackly` to complete the client's browser sign-in and Trackly account consent. The extension uses Streamable HTTP and discovers OAuth from the service's initial authentication challenge.

New customers sign up in Trackly; existing customers select their intended account. If signup outlasts authorization, keep the account and restart authorization instead of creating a duplicate. Never paste passwords, API keys, email verification codes, authorization codes, or tokens into chat.

Existing `settings.json` entries named `trackly` take precedence over this extension's MCP entry. Review that configuration privately if the connected URL/account differs. Do not combine an API-key header with the OAuth connection.

Ask the assistant to activate the `trackly` skill, call `trackly_whoami`, verify the intended account and sandbox/confirmation policy, then call `trackly_get_setup_status`. Follow its setup links before proposing a message. A human reviews any held message in Trackly; client confirmation never replaces that approval. A setup summary is advisory and does not prove funding, eligibility, consent, or delivery.

## Documentation

- [Connect an assistant](https://docs.tracklysms.com/agents/connect)
- [Customer onboarding and registration](https://docs.tracklysms.com/agents/onboarding)
- [Send with approval](https://docs.tracklysms.com/agents/send-with-approval)
- [Gemini extension reference](https://geminicli.com/docs/extensions/reference/)
- [Gemini MCP authentication](https://geminicli.com/docs/tools/mcp-server/)

## Publication status

This release candidate is published in the public [Trackly SMS Gemini repository](https://github.com/It-s-Today-Media/trackly-sms-gemini). Gallery inclusion remains unverified. The gallery discovers public GitHub repositories carrying the `gemini-cli-extension` topic and a root `gemini-extension.json`, then validates them during its daily crawl. A listing does not prove native compatibility or install the extension for users. [Gallery requirements](https://geminicli.com/docs/extensions/releasing/)
