# How to setup ESLint & Typescript
I always have to spend hours to setup ESLint with Typescript, this is my notes

## 1. Install `eslint-config-airbnb`:
```
npx install-peerdeps --dev eslint-config-airbnb
```
Read more: [npm](https://www.npmjs.com/package/eslint-config-airbnb)

## 2. Install `eslint-config-airbnb-typescript`:
```
npm install eslint-config-airbnb-typescript \
            @typescript-eslint/eslint-plugin@^5.0.0 \
            @typescript-eslint/parser@^5.0.0 \
            --save-dev
```
Read more: [npm](https://www.npmjs.com/package/eslint-config-airbnb-typescript)

## 2. Configure it
```
{
	"parser": "@typescript-eslint/parser",
	"extends": [
		"airbnb",
		"airbnb-typescript",
		"airbnb/hooks",
		"plugin:import/errors",
		"plugin:import/warnings",
		"plugin:import/typescript"
	],
	"parserOptions": {
		"project": "./tsconfig.eslint.json",
		"tsconfigRootDir": "./",
		"ecmaFeatures": {
			"jsx": true
		},
		"ecmaVersion": 2018,
		"sourceType": "module"
	},
	"plugins": [
		"@typescript-eslint",
		"react-hooks",
		"import",
		"jest"
	],
	"settings": {
		"import/resolver": {
			"node": {
				"extensions": [
					".js",
					".ts",
					".jsx",
					".tsx",
					".json",
					".native.js"
				]
			},
			"eslint-import-resolver-custom-alias": {
				"alias": {
					"@assets": "./assets",
					"@components": "./components",
					"@lib": "./lib",
					"@screens": "./screens",
					"@stacks": "./stacks",
				}
			},
			"typescript": {
				"alwaysTryTypes": true,
				"project": "./tsconfig.json"
			}
		}
	},
	"rules": {
		"no-plusplus": "off",
		"no-underscore-dangle": "off",
		"import/no-unresolved": "off",
		"import/no-extraneous-dependencies": "off",
		"react/jsx-one-expression-per-line": "off",
		"react/jsx-props-no-spreading": "off",
		"react/require-default-props": "off",
		"react-hooks/rules-of-hooks": "error",
		"react-hooks/exhaustive-deps": "warn",
		"react/no-unused-prop-types": "warn",
		"@typescript-eslint/camelcase": "off",
		"@typescript-eslint/no-unused-vars": "warn",
		"@typescript-eslint/indent": [
			"error",
			2,
			{
				"ignoredNodes": [
					"TSTypeParameterInstantiation"
				]
			}
		]
	}
}

```
