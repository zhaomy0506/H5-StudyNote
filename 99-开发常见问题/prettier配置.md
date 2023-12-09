## .prettierignore忽略文件

```
/dist/*
/html/*
.local
/node_modules/**
**/*.svg
**/*.sh
/public/*
```

## prettierrc.json 配置文件

```json
{
  "singleQuote": true,
  "semi": false,
  "bracketSpacing": true,
  "htmlWhitespaceSensitivity": "ignore",
  "endOfLine": "auto",
  "trailingComma": "all",
  "tabWidth": 2,
  "printWidth": 120
}
```

> **通过pnpm run lint去检测语法，如果出现不规范格式,通过pnpm run fix 修改**