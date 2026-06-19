# POSIX PW gen
Password (not passphrase) generator shell script. Designed to be easy, simple, portable, and standards-compliant (not just POSIX).

> [!important]
> The CLI API is unstable!

I made this because I've noticed [the power of `tr`](https://pubs.opengroup.org/onlinepubs/9799919799/utilities/tr.html), and I didn't like that many pw-gens lack transparency in how they work (looking at you, Avast) and flexibility (looking at you Firefox). This generator aims to be flexible enough while being constrained to sensible standards.

I've also extended the POSIX char-classes to include handy aliases (e.g. num = digit), and even charsets designed to reduce [confusability](https://www.unicode.org/reports/tr39/tr39-32.html#confusables) (such as [B32](https://en.wikipedia.org/wiki/Base32))

Each charset is designed to satisfy a real use-case (except `punct`, only demented people use that):
- `lower|upper|alpha`: legacy systems
- `digit`: PINs
- `alnum`: not-so-legacy systems with braindead policies/requirements
- `lonum`: keyboard [wear-leveling](https://en.wikipedia.org/wiki/Wear_leveling), and for lazy humans who hate modifier keys
- `hex|xdigit`: [WPA](https://en.wikipedia.org/wiki/Wi-Fi_Protected_Access). Avoids [KDF](https://en.wikipedia.org/wiki/Key_derivation_function) overhead when length is 64.
- `b32`: reduce glyph confusability when rendering and reading
- `graph|print`: maximum entropy density, ideal for password managers

If you want to generate a *master* key, use a *passphrase* generator, not this. You won't remember a random key.
