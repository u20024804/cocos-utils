cocos-utils
===========

Cocos utilities for Cocos2d-html5 NPM supporting.

A tool to help developers coding cocos2d-html5 easily.


## Installing
* Install `nodejs`...
* Install `ant`...
* Then type:

```bash
npm install cocos-utils -g
```

You know, it may take a long time to install modules from npm in China, because there is a "Wall".
In this case, you can try this:

```bash
npm --registry "http://registry.cnpmjs.org" install cocos-utils -g
```

Type `cocos help` to check whether the installing is successful.



## HelloWorld

##### Install all modules of cocos2d-html5

```bash
cd your/workspace/
cocos install
```

##### Create project of cocos2d-html5

(under your workspace)

```bash
cocos new helloworld
cd helloworld
cocos build
```

##### Visit dev version
* Be sure that your project has been published in a webserver, then visit `http://serverhost:port/your/project/path/index.html` in your browser.

##### Publishing

(under helloworld)

```bash
cocos publish
```

##### Visit release version
* Be sure that your project has been published in a webserver, then visit `http://serverhost:port/your/project/path/release.html` in your browser.

## Structure of project

```script
- node_modules (dir of engine modules)
    -cocos2d-html5 (core for engine)

- helloworld (project dir)
    - cfg
        - res.js (Config of path of resources, generated by cocos genRes)
        - jsRes.js (Config of path of js sources, generated by cocos genRes)
        - resCfg.js (Config of dependencies for all resources)

    - res (Path of resources)
        - Normal (Normal version)
        - HD (HD version)
        - Audio

    - src (Dir to put sources)
    - test  (Dir to put test sources)

    - node_modules (dir of third party modules)

    - cocos2d.js (Boot config of game)
    - main.js (Main for game)
    - baseCfg.js (Base config for game to load js and so on)
    - index.html (Url of dev version)

    - mini.js (Generated by cocos publish)
    - build.xml (Generated by cocos publish, used for closer compiler)
    - release.html (Url of release version)

    - cocos.json (Config for cocos command)

    - package.json
```



## Files generated by the utils.
There are files generated by the utils, which you should not edit by yourself.
* files in __temp
* res.js
* jsRes.js
* baseCfg.js
* build.xml (after publishing)
* mini.js (after publish)
* sourcemap (after publish)


## cocos.json
This file is about config of `cocos` command.
If there is something wrong while using `cocos` command, check this file first.

[Click here to see more details](https://github.com/SmallAiTT/cocos-utils/wiki/cocos.json).

[怒看中文说明](https://github.com/SmallAiTT/cocos-utils/wiki/cocos.json-%E4%B8%AD%E6%96%87%E8%AF%B4%E6%98%8E)


## resCfg
This is the main config for the dependencies of the project.
It is the core to load js and resources, just like what `resources.js` and `appFiles` of `cocos2d.js` do in the develop branch.
`cc.js` takes place of `jsLoader.js`, so `jsLoader` do not work in this npm branch.

[Click here to see more details](https://github.com/SmallAiTT/cocos-utils/wiki/resCfg).

[怒看中文说明](https://github.com/SmallAiTT/cocos-utils/wiki/resCfg-%E4%B8%AD%E6%96%87%E8%AF%B4%E6%98%8E)


## package.json
Same as `package.json` of `npm`.

Third party modules will be configured in `dependencies`.
If you add or delete a module (dependencies in package.json or cocos.json),
you should run `cocos build` or `cocos genBaseCfg` once more.


## Test Case
By default, we have provided some test functions for you.
Also you can define your own test functions.

[Click here to see more details](https://github.com/SmallAiTT/cocos-utils/wiki/Test-Case).

[怒看中文说明](https://github.com/SmallAiTT/cocos-utils/wiki/Test-Case-%E4%B8%AD%E6%96%87%E8%AF%B4%E6%98%8E)

## Notes
Do not forget run `cocos genRes` if you add or delete resources, rename the resources or change the paths of the resources.

Do not forget run `cocos genJsRes` if you add or delete js, rename js or change the path of js.

Do not forget run `cocos genBaseCfg` if you install or uninstall modules of cocos2d-html5 which are configured in dependencies of cocos.json,
or of third party which are configured in dependencies of package.json.

In fact, you can use `cocos build` which includes these three command above.


Be sure that each key in your `res.js` and `jsRes.js` is unique, which is generated by the file name. The rule of key is :

```script
a.png  :  a_png        //"." will be replaced by "_"
a-b.png  :  a_b_png    //"-" will be replaced by "_"
1a.png  :  _1a_png     //"_" will be add before if the first char is a number
a b.png  :  ab.png     //" " will be replaced by ""
```

`cc.js` will be replaced with `cc4publish.js` when publishing.
