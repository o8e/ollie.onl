---
title: Keeping ESLint and Prettier sweet with Vue CLI
description: Strangely with the Vue CLI, if you select ESLint + Prettier as your linter and formatter of choice, it doesn't always appear to work outside of the box.
---

The solution is actually simple, but it took me a lot of fiddling about to work out what needed to go where, without potentially interrupting my VSCode setup and config. My thought process was that it has been working fine up until now – and still does on old projects – so it can't be something I'm doing.

```diff-js
module.exports = {
   rules: {
     'no-console': process.env.NODE_ENV === 'production' ? 'warn' : 'off',
     'no-debugger': process.env.NODE_ENV === 'production' ? 'warn' : 'off',
+    'prettier/prettier': [
+      'warn',
+      {
+        singleQuote: true,
+        semi: false,
+      },
+    ],
   },
```

Turns out you just need to add this little nugget to your **.eslintrc** and it will stop ESLint and Prettier getting stuck in a formatting loop. Obviously you will need to amend that actual rules inside the **prettier/prettier** array, but hey why would you _not_ use single quotes and no semicolons?

```js
'prettier/prettier': [
  'warn',
  {
    singleQuote: true,
    semi: false,
  },
],
```
