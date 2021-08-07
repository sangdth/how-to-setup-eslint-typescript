# How to setup ESLint & Typescript
I always have to spend hours to setup ESLint with Typescript, this is my notes

## 1. Install the [required packages](https://www.npmjs.com/package/eslint-config-airbnb-typescript)
```
yarn add -D eslint-config-airbnb-typescript \
            eslint-plugin-jest \
            eslint-plugin-import@^2.22.0 \
            eslint-plugin-jsx-a11y@^6.3.1 \
            eslint-plugin-react@^7.20.3 \
            eslint-plugin-react-hooks@^4.0.8 \
            @typescript-eslint/eslint-plugin@^4.4.1 \
	    @typescript-eslint/parser \
	    @typescript-eslint/eslint-plugin
```

## 2. Configure it
```
{
	"parser": "@typescript-eslint/parser",
	"extends": [
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
