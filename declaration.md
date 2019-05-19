

一般组织声明文件的方式取决于库是如何被使用的。


## 识别库的类型

### 全局库

无需主动引用，在全局范围内直接可以使用的，比如 jQuery，`$(() => { console.log('hello!'); } );`。一个全局库声明文件样板：

```js
// Type definitions for [~THE LIBRARY NAME~] [~OPTIONAL VERSION NUMBER~]
// Project: [~THE PROJECT NAME~]
// Definitions by: [~YOUR NAME~] <[~A URL FOR YOU~]>

// 如果这个库可以被直接调用，比如 myLib(3)，保留下面的调用特性，否则删除。
declare function myLib(a: string): string;
declare function myLib(a: number): number;

// 如果想让这个库的名字是一个有效的类型，可以按下面方式处理，这样，你就可以这么使用：`var x: myLib;`
// 请确认是否需要，如果不需要请删除此处，并在下方的 namespace 中添加类型
interface myLib {
    name: string;
    length: number;
    extras?: string[];
}

// 如果你的库需要暴露一些属性到一个全局变量，那么应该按照下面处理
// 你可能也需要把类型（接口和类型别名）也放到这里
declare namespace myLib {
    // 使用： 'myLib.timeout = 50;'
    let timeout: number;

    // 可以通过 'myLib.version' 访问，但不能修改哦
    const version: string;

    // 可以通过 'let c = new myLib.Cat(42)' 创建实例
    // 或者引用 'function f(c: myLib.Cat) { ... }
    class Cat {
        constructor(n: number);

        // 可以通过 'c.age' 读取实例上属性值
        readonly age: number;

        // 可以通过 'c.purr()' 调用实例方法
        purr(): void;
    }

    // 可以通过 'var s: myLib.CatSettings = { weight: 5, name: "Maru" };' 声明变量
    interface CatSettings {
        weight: number;
        name: string;
        tailLength?: number;
    }

    // 可以 'const v: myLib.VetID = 42;' 或者 'const v: myLib.VetID = "bob";'
    type VetID = string | number;

    // 可以 'myLib.checkCat(c)' 或 'myLib.checkCat(c, v);' 调用
    function checkCat(c: Cat, s?: VetID);
}
```

## 模块库



