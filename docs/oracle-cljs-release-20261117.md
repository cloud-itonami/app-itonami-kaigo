# cljs release bundle built by an oracle (2026-11-17)

ORACLE evidence, not a native build. The committed `web/dist/js/main.js` is the output of a JVM shadow-cljs
release run. No CI, gate, packaging or runtime path depends on it; the Tauri host only copies the
committed bundle. The dev build (`cljs-runtime/`) that was committed before is removed.

- Command: `python3 oracle/cljs-release-oracle.py <work> app-itonami-kaigo app (mirrors .cljk to .cljc and .mjs to .js, overrides io.github.kotoba-lang/* with the local worktree)`
- Tools: node v26.0.0, npm 11.12.1, openjdk 21.0.1, shadow-cljs 2.28.20, kotoba-lang/kotoba@426ddd2a635b6714ad60a8d7852f4f802e3e54b6 (sparse lib/)
- Input: this repository at 37e9eb88c181116fd845884c57327b2005b12b96.
- Output: `Build completed`, exit 0; `main.js` 440218 bytes, sha256 febe75500174823fd719ea2869bcaf78e031ef912289cd771678ac008eff292d.
- Check: the Tauri host built from it renders the page in Chromium under a CSP with no `'unsafe-eval'`
  (no EvalError). Blocked as intended by the hash-only style-src and frame-src 'none': Google Fonts stylesheet, dynamic inline style, the iframe to giemon.etzhayyim.com.
- Not shown: behaviour with live data; that a native (Amu) build produces the same code.
