# lerna管理项目
lerna是多git+npm的多package项目的管理工具
## 环境部署
开发环境使用lerna
`npm i -D lerna`

## 项目结构

- utils 工具包，让每个包和项目都可以使用
- core
- .gitignore

# 创建package
##  lerna create 
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
给每个包都安装依赖