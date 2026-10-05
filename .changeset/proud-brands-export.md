---
"@langchain/core": patch
---

Export `BrandedClass` and `IsInstanceFn` from `@langchain/core/errors`

`ns.brand()` returns a `BrandedClass`, which wasn't exported, so TypeScript
could not name it when emitting declarations for a class in another package
that extends `ns.brand(...)`, and reported TS2883 instead (as in
`@langchain/typesafe`, `@langchain/openrouter` and `@langchain/google`). Both
types are now exported, so such classes emit portable declarations. No runtime
change.
