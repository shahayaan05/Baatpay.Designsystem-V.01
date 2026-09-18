# Baatpay Design System

The single source of truth for Baatpay's visual language: design tokens, foundations, brand assets, and component specs. This repo exists so any developer or designer can build Baatpay-consistent UI without opening Figma.

> **Baatpay** is a fintech-social super-app for Pakistan (chat, calling, payments). The brand reads clean, premium, and minimal, with a blue-forward identity.

---

## What's in here

| Folder | What it holds |
|---|---|
| `tokens/` | Machine-readable design tokens (W3C format). The source of truth for every color, size, and style. |
| `flutter/` | Ready-to-use Dart token constants and a `ThemeData` for the Flutter app. Generated from `tokens/`. |
| `docs/` | Human-readable documentation: foundations, brand, components, and guidelines. |
| `assets/` | Logo, icons, illustrations, and fonts (drop exported files here). |

---

## Quick start

### For developers (Flutter)

1. Copy the files in `flutter/lib/` into your app (or add this repo as a package).
2. Apply the theme:

   ```dart
   import 'baatpay_theme.dart';

   MaterialApp(
     theme: BaatpayTheme.light,
     darkTheme: BaatpayTheme.dark,
     home: const HomeScreen(),
   );
   ```

3. Reference tokens directly instead of hardcoding values:

   ```dart
   Container(
     color: BaatpayColors.brandPrimary,
     padding: const EdgeInsets.all(BaatpaySpacing.md),
   );
   ```

### For designers

Start in [`docs/`](docs/). Foundations first (color, type, spacing), then brand, then components. Every value shown in the docs maps 1:1 to a token in `tokens/`.

---

## The golden rule

**Never hardcode a value.** If you're typing a hex code, a pixel number, or a font name directly into a screen, stop and reach for a token. If the token you need doesn't exist yet, add it to `tokens/` first, then use it. This is what keeps the app consistent and makes rebrands a one-file change.

---

## How the pieces connect

```
tokens/tokens.json   ← source of truth (edit here)
        │
        ├──►  flutter/lib/baatpay_tokens.dart   (Dart constants)
        ├──►  flutter/lib/baatpay_theme.dart     (ThemeData)
        └──►  docs/*                              (documentation reflects these)
```

When a token changes, update `tokens/tokens.json` first, then regenerate the platform files. See [`tokens/README.md`](tokens/README.md).

---

## Contributing

Small system, simple rules:

1. Propose the change in `tokens/` or the relevant `docs/` file.
2. Keep naming consistent: `[ramp]-[step]` for raw values (e.g. `blue-500`), semantic aliases for intent (e.g. `brand-primary`, `success`).
3. Update `CHANGELOG.md`.
4. Open a PR.

See [`docs/04-guidelines/contributing.md`](docs/04-guidelines/contributing.md) for the full flow.

---

## Status

This repo is the scaffold and framework. Exact token values are being populated from the master `design.md` extraction. Sections marked _"pending design.md"_ or labeled **starter default** should be treated as placeholders until finalized.
