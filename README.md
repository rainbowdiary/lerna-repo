# lerna管理项目
lerna是多git+npm的多package项目的管理工具
## 环境部署
开发环境使用lerna
`npm i -D lerna`

## 项目结构

- utils 工具包，让每个包和项目都可以使用
- core
- .gitignore



# 新建

# 创建package
- lerna create 
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
