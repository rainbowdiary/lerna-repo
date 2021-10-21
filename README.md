# lerna管理项目
lerna是多git+npm的多package项目的管理工具
## 环境部署
开发环境使用lerna
`npm i -D lerna`

学习：sam9831

## 项目结构

- utils 工具包，让每个包和项目都可以使用
- core
- .gitignore

# 创建package
##  lerna create 
lerna create -h
@lerna/create
Create a new lerna-managed package
```js
//Usage
//Create a new lerna-managed package
lerna create <name> [loc]

Create a new lerna-managed package

Positionals:
  name  The package name (including scope), which must be locally unique _and_
        publicly available                                   [string] [required]
  loc   A custom package location, defaulting to the first configured package
        location                                                        [string]

Command Options:
  --access        When using a scope, set publishConfig.access value
                             [choices: "public", "restricted"] [default: public]
  --bin           Package has an executable. Customize with --bin
                  <executableName>                             [default: <name>]
  --description   Package description                                   [string]
  --dependencies  A list of package dependencies                         [array]
  --es-module     Initialize a transpiled ES Module
  --homepage      The package homepage, defaulting to a subpath of the root
                  pkg.homepage                                          [string]
  --keywords      A list of package keywords                             [array]
  --license       The desired package license (SPDX identifier)   [default: ISC]
  --private       Make the new package private, never published
  --registry      Configure the package's publishConfig.registry        [string]
  --tag           Configure the package's publishConfig.tag             [string]
  --yes           Skip all prompts, accepting default values
```

### 创建core和utils包
- lerna create core
修改package name配置为@rainbow-cli-dev/core；让其能发布到npm平台
- lerna create utils
修改package name配置为@rainbow-cli-dev/utils

**知识点**
- 如果npm包名以@开头则/前面的内容为npm的group name；
- 操作：需要到npm平台创建一个group name
头像->+Add Organization-Create a New Organization：rainbow-cli-dev->Unlimited public packages
- 如果不注册，包发npm上

## lerna add 安装依赖
文档：`lerna add -h`
Add a dependency to matched packages
```
Usage:
$ lerna add <package>[@version] [--dev] [--exact] [--peer]
```

### lerna clear 清空所有依赖包  
### 给每个包都安装依赖
测试`lerna add rainbow-test`
将会在所有的依赖包中都安装该依赖，查看core和utils的`package.json`文件；
### 给特定包安装依赖
lerna add rainbow-test packages/core/

操作：

- `lerna clean` 清空所有的依赖
提示：`lerna WARN No packages found where rainbow-test can be added. `
因为lerna clean 删除了所有包的node_modules，但是pakcage.json中的依赖还存在，需要手动删除

- lerna add rainbow-test packages/core
给core包安装指定的依赖包

## lerna bootstrap
重新安装依赖

## lerna link
文档：`lerna link -h`
`Symlink together all packages that are dependencies of each other`
```
Usage:
$ lerna link
```
如果包之间存在相互依赖，则会自动帮忙创建软链接；
例如：pakcages/core/package.json中依赖@rainbow-cli-dev/utils这个包
则lerna link会自动在pakcages/core/node_modules下面创建@rainbow-cli-dev/utils包的软链接


## 脚手架开发 lerna exec