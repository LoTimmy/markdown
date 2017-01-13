```console
shell> npm install -g eslint
shell> eslint --init
shell> eslint yourfile.js

shell> npm install eslint eslint-config-airbnb-base eslint-plugin-import

```

`.eslintrc`
```
{
  "rules": {
    "no-console": 0,
    "semi": ["error", "always"],
    "quotes": ["error", "double"]
  },
  "env": {
    "browser": true,
    "node": true
  },
  "extends": "airbnb-base",
  "plugins": [
    "import"
  ]
}
```

- https://www.npmjs.com/package/eslint
- https://www.npmjs.com/package/eslint-config-airbnb-base
- http://eslint.org/docs/user-guide/command-line-interface
- http://eslint.org/docs/rules/
- http://eslint.org/docs/rules/no-console
- http://eslint.org/docs/2.0.0/rules/no-undef
- http://eslint.org/docs/user-guide/configuring#specifying-environments
