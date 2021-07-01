## 从未知道的 npm 特性

> 部分我不感兴趣的已被省略，[查看原文](https://github.com/npm/rfcs/tree/latest/implemented)

### 1. 别名

可以在安装包时给包取别名，这样就可以在一个包里同时引用两个版本的其他包。

```json
> npm i bar foo@npm:bar
> cat package.json
{
  "dependencies": {
    "foo": "npm:bar@^0.1.0",
    "bar": "^0.1.0",
  }
}
```

可用格式：

```
foor@npm:bar@^0.1.0
foor@github:user/bar
foor@../bar
```

### 10. `repository` 下可以多一个 `directory` 字段

方便 monorepo 更精确地找到源码位置。

```json
"repository": {
  "type": "git",
  "url": "https://github.com/facebook/react",
  "directory": "packages/react-dom"
}
```

### 16. `npm set-script start "http-server ."`

### 17,18. `funding`

```json
"funding": {
  "type": "patreon",
  "url": "https://www.patreon.com/my-account"
}
```

### 23. `acceptDependencies`

用来向下兼容旧的 node 平台，例如有一个包需要支持 node4：

```json
{
  "name": "my-node4-package",
  "engines": {
    "node": ">=4"
  },
  "dependencies": {
    "make-dir": "^1.3.0"
  },
  "acceptDependencies": {
    "make-dir": "2.x - 3.x"
  }
}
```

同时如果用户手动安装了 make-dir 2.x 或 3.x，那么 make-dir 1.x 就被扔掉了。

### 26. workspaces

```json
{
  "name": "workspace-example",
  "version": "1.0.0",
  "workspaces": [
    "packages/*"
  ]
}
```

### 27. `npm outdated`

### 33. `npm diff`

显示本地文件和线上最新版的包之间的差别。
