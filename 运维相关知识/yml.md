```
name: Code Linting   //workflow的名称，每个workflow文件夹里面的每一个都是一个workflow文件。

on:                  //on是指什么时候运行。
  push:              //当是push的时候运行。
    branches: [ "main" ]    //当push了这些branch之后就会运行。     
  pull_request:
    branches: [ "main" ]

jobs:               //jobs是指条件满足了之后会执行那些任务。
  build:
    runs-on: ubuntu-latest    //表示命令应该在什么环境下执行。 这个命令是指应该在ubuntu的最新版本下执行。

    steps:          //steps是说执行这个任务有那些步骤。
    - uses: actions/checkout@v3  //每个横杆都是一个步骤。这个步骤是吧repo里面的所有代码都checkout出来，相当于git clone。
    - name: Use Node.js 19.7.0   //给起steps个名字叫Use Node.js 19.7.0。
      uses: actions/setup-node@v3 // 安装node.js
      with:
        node-version: 19.7.0
        cache: 'npm'              //cache是指缓存，缓存npm安装的内容。
    - run: npm ci
    - run: npm run lint
```

```
name: Code Linting

env:                  //在workflow里面定义变量
  NODE_VERSION: 19.7.0

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  code-linting:     //jobs的名称
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v3
    - name: Use Node.js ${{ env.NODE_VERSION }}
      uses: actions/setup-node@v3
      with:
        node-version: ${{ env.NODE_VERSION }}
        cache: 'npm'
    - run: npm ci
    - run: npm run lint
```