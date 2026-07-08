# google_gax (patched)

Patched fork of [google_gax](https://hex.pm/packages/google_gax) v0.4.1 for
compatibility with Tesla >= 1.18.3.

## Why this fork exists

The upstream `google_gax` (last released in 2021, unmaintained) is not
compatible with Tesla >= 1.18.3. Tesla 1.18.3 made
`Tesla.Middleware.DecompressResponse` require a `:max_body_size` option and
tightened multipart field handling, both of which the old `google_gax` violates,
so requests raise at runtime.

## Changes from upstream

- `connection.ex`: pass `max_body_size` to `Tesla.Middleware.DecompressResponse`
  (read from application config, default `:infinity`)
- `connection.ex`: use string multipart field names and header keys instead of
  atoms

## Usage

```elixir
# mix.exs
{:google_gax, github: "alaadahmed/google_gax", override: true}
```

## Upstream

- Hex: https://hex.pm/packages/google_gax
- Source: https://github.com/googleapis/elixir-google-api/tree/master/clients/gax
