# twitch-vaft-patched

Patched copy of `vaft/vaft-ublock-origin.js` from
[ryanbr/TwitchAdSolutions](https://github.com/ryanbr/TwitchAdSolutions) at commit
`6f7f110eb1a8134ae200fcaceeaad999be03d5d8` (v68.4.0).

## Change

The `visibilitychange` handler in `onContentLoaded()` resumed a user-paused stream when another
extension overrides `document.hidden` to always return `false`:

- `wasVideoPlaying` starts as `false` and is reset after each resume check
- hidden detection uses `document.visibilityState === 'hidden'` instead of `document.hidden`
- no auto-resume while `playerBufferState.userPauseIntent` is set
