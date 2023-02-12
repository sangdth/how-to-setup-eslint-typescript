# How to setup ESLint & Typescript
I always have to spend hours to setup ESLint with Typescript, this is my notes

## 1. Install `eslint-config-airbnb`:
```
npx install-peerdeps --dev --extra-args "--save-exact" eslint-config-airbnb 
```
Not using React:
```
npx install-peerdeps --dev --extra-args "--save-exact" eslint-config-airbnb-base
```
Read more: [npm](https://www.npmjs.com/package/eslint-config-airbnb)

## 2. Install `eslint-config-airbnb-typescript`:
```
npx install-peerdeps --dev --extra-args "--save-exact" eslint-config-airbnb-typescript
```
Read more: [npm](https://www.npmjs.com/package/eslint-config-airbnb-typescript)

### 2.1 Bonus Prettier
```
npm install --save-dev --save-exact eslint-config-prettier eslint-plugin-prettier prettier
```
Read more: [github](https://github.com/prettier/eslint-config-prettier)

## 3. Add `.eslintrc` file:
```
{
  "parser":"@typescript-eslint/parser",
  "extends":[
    "airbnb",
    "airbnb-typescript",
    "airbnb/hooks",
    "plugin:import/errors",
    "plugin:import/warnings",
    "plugin:import/typescript"
  ],
  "parserOptions":{
    "project":"./tsconfig.eslint.json",
    "tsconfigRootDir":"./",
    "ecmaFeatures":{
      "jsx":true
    },
    "ecmaVersion":2018,
    "sourceType":"module"
  },
  "plugins":[
    "@typescript-eslint",
    "react-hooks",
    "import"
  ],
  "settings":{
    "import/resolver":{
      "node":{
        "extensions":[
          ".js",
          ".ts",
          ".jsx",
          ".tsx",
          ".json",
          ".native.js"
        ]
      },
      "typescript":{
        "alwaysTryTypes":true,
        "project":"./tsconfig.json"
      }
    }
  },
  "rules":{
    "no-plusplus":"off",
    "no-underscore-dangle":"off",
    "import/no-unresolved":"off",
    "import/no-extraneous-dependencies":"off",
    "react/jsx-one-expression-per-line":"off",
    "react/jsx-props-no-spreading":"off",
    "react/require-default-props":"off",
    "react-hooks/rules-of-hooks":"error",
    "react-hooks/exhaustive-deps":"warn",
    "react/no-unused-prop-types":"warn",
    "@typescript-eslint/camelcase":"off",
    "@typescript-eslint/no-unused-vars":"warn",
    "@typescript-eslint/indent":[
      "error",
      2,
      {
        "ignoredNodes":[
          "TSTypeParameterInstantiation"
        ]
      }
    ]
  }
}

```
## 4. Add `tsconfig.eslint.json` file:
```
{
  "extends": "./tsconfig.json",
  "compilerOptions": {
    "noEmit": true // ensure that nobody can accidentally use this config for a build
  },
  "exclude": [
    "*.yaml",
    ".next",
    "dist",
    "node_modules",
    "public"
  ],
  "include": ["**/*.ts", "**/*.tsx", "**/*.js"]
}
```
