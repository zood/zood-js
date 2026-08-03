# zood-js

Browser-side TypeScript/JavaScript shared by the Zood web properties.

- `js/zood.ts` - client for the [oscar](https://github.com/zood/oscar) API: login (challenge/response),
  account deletion, drop box watching, and the libsodium wrappers that go with them.
- `js/zdtime.ts` - relative time formatting helpers.
- `libs/sodium.0.7.15.js` - vendored [libsodium.js](https://github.com/jedisct1/libsodium.js), loaded as-is.
- `typings/` - hand-maintained `.d.ts` files for `sodium` and `Intl`.

## Building

There is no JS toolchain here on purpose. Compile with the TypeScript compiler and nothing else:

```
tsgo -p .     # or: tsc -p .
```

Everything is plain `namespace` code compiled in place (`js/zood.ts` → `js/zood.js`), targeting ES2017 with
no module system, so consumers just add `<script>` tags in dependency order.

**The generated `.js` files are committed.** Consumers embed this repo as a git submodule and serve the files
directly — none of them have a build step — so a change to a `.ts` file isn't done until the matching `.js`
is regenerated and committed alongside it.

## Consumers

- `buster` (www.zood.xyz) - submodule at `assets/js/zood-js`.
- `Lucille` (locationshare.zood.xyz) - will use these files later.

## License

Copyright 2026 Arash Payan

Licensed under the AGPLv3: https://www.gnu.org/licenses/agpl-3.0.html

Zood is a trademark of Tangled Wires, LLC
