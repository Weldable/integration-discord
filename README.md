# @weldable/integration-discord

Discord messaging and server actions for Weldable.

Part of the [Weldable](https://weldable.ai/) integration library — see [@weldable/integration-core](https://github.com/weldable/integration-core) for the full catalog.

## Install

```bash
npm install @weldable/integration-discord @weldable/integration-core
```

`@weldable/integration-core` is a peer dependency and must be installed alongside this package.

## Usage

```ts
import integration from '@weldable/integration-discord'

// Send a message to a channel
const send = integration.actions.find(a => a.id === 'discord.send_message')!

const result = await send.execute(
  {
    channel_id: '1234567890123456789',
    content: 'Deployment to production succeeded.',
  },
  ctx, // ActionContext from your Weldable-compatible host
)

console.log(result.id) // Discord message snowflake ID

// Read recent messages
const read = integration.actions.find(a => a.id === 'discord.read_messages')!

const messages = await read.execute(
  { channel_id: '1234567890123456789', limit: 10 },
  ctx,
)
```

## Contributing and releasing

See [CONTRIBUTING.md](https://github.com/weldable/integration-core/blob/main/CONTRIBUTING.md) in `@weldable/integration-core` for the development workflow and release process.

## License

MIT
