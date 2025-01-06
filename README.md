# Fumadocs MDX v11.2.1 - Regression error from v11.2.0

This repository was made using the command
```sh
pnpm create fumadocs-app
```
with all default settings.

The changes made were:
1. downgrading to `fumadocs-mdx@11.2.1` (from `11.2.2`, although the bug exists in both versions)
2. add the following to `source.config.ts`:
    ```ts
    export default defineConfig({
      generateManifest: true,
    });
    ```

## Instructions

```sh
pnpm i
pnpm build
```

You will see errors along the lines of
```
> fumadocs-mdx-11.2.1-build@0.0.0 build /home/nktnet/.temp/fumadocs-mdx-11.2.1-build
> next build

   ▲ Next.js 15.1.3
   - Experiments (use with caution):
     · turbo

[MDX] initialized map file
   Creating an optimized production build ...
unhandledRejection [Error: callback(): The callback was already called.]
[MDX] writing manifest
cannot find the search index of /home/nktnet/.temp/fumadocs-mdx-11.2.1-build/content/docs/index.mdx [Error: ENOENT: no such file or directory, open '/home/nktnet/.temp/fumadocs-mdx-11.2.1-build/.next/cache/fumadocs/content_docs_index.mdx.json'] {
  errno: -2,
  code: 'ENOENT',
  syscall: 'open',
  path: '/home/nktnet/.temp/fumadocs-mdx-11.2.1-build/.next/cache/fumadocs/content_docs_index.mdx.json'
}
cannot find the search index of /home/nktnet/.temp/fumadocs-mdx-11.2.1-build/content/docs/test.mdx [Error: ENOENT: no such file or directory, open '/home/nktnet/.temp/fumadocs-mdx-11.2.1-build/.next/cache/fumadocs/content_docs_test.mdx.json'] {
  errno: -2,
  code: 'ENOENT',
  syscall: 'open',
  path: '/home/nktnet/.temp/fumadocs-mdx-11.2.1-build/.next/cache/fumadocs/content_docs_test.mdx.json'
}
 ELIFECYCLE  Command failed with exit code 1.
```

although the key part being:
```
unhandledRejection [Error: callback(): The callback was already called.]
[MDX] writing manifest
```