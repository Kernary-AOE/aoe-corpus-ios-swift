# @ios-swift — Swift API Design + style, atom-shaped

> 17 typed Prime atoms distilled from the **Swift API Design Guidelines**
> (swift.org) and the **Google Swift Style Guide** — the naming,
> type-design, optional-handling, and concurrency rules every iOS / Swift
> agent should follow before writing the first line of public API.

This is a **starter seed corpus** for the Skill Wiki marketplace. It gives
an AI coding agent a small, audited reference set covering Swift idioms
that distinguish good Swift from "Java with `let`" or "Objective-C with
braces".

The corpus answers a common question for AI agents writing Swift:
*how do I write a Swift API that reads naturally and survives a code
review?* The answer is no longer "read these two long guides" — it is
"load this Prime, follow the rules, avoid the anti-pattern."

---

## What's in the box

17 atoms across five concern areas, plus two principles.

| Concern | Atoms | Kinds |
|---|---|---|
| Naming (Swift API Design Guidelines) | 6 | rule × 6 |
| Protocols and types | 4 | rule × 4 |
| Optionals and force-unwrap | 3 | rule × 2, anti-pattern × 1 |
| Memory and concurrency | 2 | rule × 2 |
| Principles | 2 | principle × 2 |
| **Total** | **17** | — |

Each atom carries source attribution to a specific guideline section at
the top of the `.prime` file.

---

## License

This Prime is multi-licensed — code, Swift-derived atoms, and
Google-derived atoms each carry their upstream license:

| Layer | License |
|---|---|
| **Code** (pack.yaml, domain.yaml, build glue, packaging) | Apache-2.0 |
| **Atom content** derived from Swift API Design Guidelines | Apache-2.0 |
| **Atom content** derived from Google Swift Style Guide | CC-BY 3.0 |

Each `.prime` file's `// Source:` header identifies which upstream and
which license apply to that atom. If you adapt or extend the corpus,
you must:

1. Keep the per-file `// Source: …` attribution headers.
2. Distribute Apache-derived atoms under Apache-2.0 and Google-derived
   atoms under CC-BY 3.0 (or compatible).
3. Note your changes near the original attribution.

See `LICENSE` for the full text.

---

## How to compile

The corpus is checked-in pre-compiled (`compiled/_index.xml` + per-atom
directories). To rebuild from sources:

```bash
# from the repo root
bun ../prime-system/scripts/build-atom-dirs.ts \
  --src primes/sources \
  --out compiled

# Expected output:
# Found 17 .prime files in primes/sources
# ... per-atom emit lines ...
# 17 atoms compiled
#   → compiled/_index.xml (~Nk tokens, 17 atoms)
```

The build script lives in the
[`prime-system`](https://github.com/skill-wiki/prime-system) repo. Clone
both side-by-side, or vendor the script in if you prefer.

---

## How to install

### As an MCP server in Claude Code

```json
{
  "mcpServers": {
    "ios-swift": {
      "command": "bunx",
      "args": ["@skill-wiki/mcp-server-core"],
      "env": {
        "PRIME_DIR": "/abs/path/to/skill-corpus-ios-swift/compiled"
      }
    }
  }
}
```

The agent now sees a 17-atom Swift index on every turn. It pulls the
relevant atoms when the task touches naming a public API, designing a
type, handling optionals, or writing async code, and ignores them
otherwise.

### From the marketplace

After this Prime is registered in
[`skill-wiki/website`](https://github.com/skill-wiki/website)'s
`data/skills.yaml` it appears on the public marketplace and can be
installed via the website's install flow.

---

## Reading order

If you're learning the corpus from scratch:

1. **`principle-clarity-at-call-site`** — the thesis of the Swift API
   Design Guidelines. Every other naming atom follows from it.
2. **`principle-Swift-as-progressive-disclosure`** — the language-design
   principle. Explains why `struct` is the default, `class` is the
   exception, and why `async`/`@Sendable`/`@MainActor` are opt-in.
3. The **six naming rules** — read them in order. They form a single
   decision procedure: read the call site, omit needless words, label
   what the grammar requires.
4. **`rule-protocol-vs-class-when-to-use`** + **`rule-value-types-by-default`** —
   the type-design defaults.
5. The **optional triple** (`rule-guard-let-early-return`,
   `rule-optional-chaining-over-nil-check`,
   `anti-pattern-never-force-unwrap-publicly`) — the operational core
   for nil-safety.
6. **`rule-await-not-completion-handler`** + **`rule-prefer-Sendable`** +
   **`rule-weak-self-in-escaping-closures`** — modern concurrency.

---

## Contributing

This is a seed set. The Swift API Design Guidelines and the Google
Swift Style Guide together contain hundreds of atom-shaped facts; we
picked 17 because that's the smallest set that demonstrates the model
and is genuinely useful by itself.

Good additions:

- More **naming rules** — booleans read as assertions, factory methods,
  protocol naming conventions, deprecated-API renaming.
- More **type-design** — copy-on-write boxes, phantom types, `~Copyable`
  / `~Escapable` (Swift 6), opaque return types (`some P`).
- More **concurrency** — `MainActor` discipline, isolation domain
  inference, structured-concurrency cancellation patterns, `TaskGroup`
  vs `async let` tradeoffs.
- More **anti-patterns** — `NSError` bridging, singleton-via-class-method,
  forced casts, optional-of-optional, abusing `defer`.
- A **persona** — `swift-api-reviewer`, `ios-app-engineer`, etc. — and
  a **collection** that bundles the lot.

Open a PR. Keep:

- Atoms terse — atom-shaped, not paraphrased prose.
- One `.prime` file per atom.
- The `// Source: …` header pointing to the originating guideline section.
- Edges (`requires` / `enhances` / `contradicts` / `related`) where the
  relationship is real, not for decoration.
- A passing `bun ../prime-system/scripts/build-atom-dirs.ts ...` run.

---

## Provenance

- **Knowledge sources:**
  - Swift API Design Guidelines, Apache-2.0,
    https://www.swift.org/documentation/api-design-guidelines/
  - Google Swift Style Guide, CC-BY 3.0,
    https://google.github.io/swift/
- **Atom packaging:** Skill Wiki contributors, Apache-2.0
- **Distillation:** the prose in each atom is heavily compressed and
  re-shaped from the originals; this is fair use within each upstream
  license, but the substance is Apple's and Google's work.
