# TypeScript



提示：

`Experimental support for decorators is a feature that is subject to change in a future release. Set the 'experimentalDecorators' option to remove this warning."`

解决：

vs code 设置

```json
"javascript.implicitProjectConfig.experimentalDecorators": true,
```

tsconfig.json

```json
"compilerOptions": {
  "experimentalDecorators": true,
  "allowJs": true
}
```