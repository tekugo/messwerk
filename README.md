# messwerk

A terminal monitor for **Claude Code OTLP telemetry**, built on the
[zeichenwerk](https://github.com/tekugo/zeichenwerk) TUI framework.
Receives metrics over OTLP/gRPC and displays token usage, cost, and
activity in real time.

## Install

```sh
go install github.com/tekugo/messwerk/cmd/mw@latest
```

The binary is named `mw`.

## Run

Add the following to your Claude Code `settings.json` (user, project,
or local scope):

```json
{
  "env": {
    "CLAUDE_CODE_ENABLE_TELEMETRY": "1",
    "OTEL_METRICS_EXPORTER": "otlp",
    "OTEL_EXPORTER_OTLP_PROTOCOL": "grpc",
    "OTEL_EXPORTER_OTLP_ENDPOINT": "http://localhost:4317"
  }
}
```

Then start `mw` before launching Claude Code:

```sh
mw
```

### Flags

| Flag | Default | Purpose |
|------|---------|---------|
| `-port` | `4317` | OTLP gRPC listen port |
| `-t` | `tokyo` | Theme: midnight, tokyo, nord, gruvbox-dark, gruvbox-light, lipstick |
| `-sim` | `false` | Populate the store with simulated sessions for UI testing |

If 4317 is taken, run `mw -port 4318` and set
`OTEL_EXPORTER_OTLP_ENDPOINT` to match.

## Status

Early — extracted from `cmd/messwerk` in the zeichenwerk monorepo
as a standalone tool. API and shape may change without notice.

## License

MIT — same as the upstream zeichenwerk library.
