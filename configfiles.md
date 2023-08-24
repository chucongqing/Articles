# 常见配置文件介绍

在软件开发/维护中有一些功能，在不同的环境中有着不同的配置。这时候我们就需要使用配置文件来动态的调整这些配置项。
配置文件有很多种类，常见的有INI，XML，JSON，YAML，TOML，环境变量等。
下文就对这么多配置文件有什么优缺点，选择的时候需要进行什么考虑来进行简单的介绍。

## 需求
* 使用配置文件的人是谁。 用户还是运维人员，如果是习惯有界面系统的终端用户那么可能需要提供的就不是配置文件，而是图形化的配置界面。
* 你的配置文件的数据结构是否复杂。简单配置的比如只有字符串，软件中使用字符串解析为数字或者分割成数组。 更复杂的数据在需要支持复杂配置的时候使用，比如map，sets，这种配置文件往往需要专门的解析器(Parser)来解析。
* 另外还需要了解下项目中使用的编程语言有没有支持读写这种配置文件的，稳定好用的库。如果你有选择的话，尽量不要自己去实现一个配置文件解析的代码。
* 配置文件需要被程序读取，同时也需要人来配置和阅读。所以配置文件的需要对于使用者来说，比较容易的阅读，理解，和编辑。如果配置的格式出错了，程序最好清晰的指出哪里（哪行）配置出现了问题导致失败，以方便调试。
* 配置文件中可以增加注释。 软件开发人员应该在创建一个Sample config文件，同时在配置项的方便添加注释说明。配置者应该恰当的解释下他们设置的值的用意。这样方便后续维护。支持注释还有个好处是可以通过注释功能，切换不同的配置选项。（JSON 就不支持）

## 配置文件类型

### ENVIROMENT

环境变量是操作系统和shells里面的一项功能。使用环境变量的话需要在运行程序之前将需要的变量提前设置好。

### INI

[INI](https://en.wikipedia.org/wiki/INI_file),最早在MS-DOS中使用。这是一个k/v 对的格式。 其中key可以以section分组。
这种配置文件有很多解析器（parser)。 对于比较简单的配置，而且你使用的语言中有对应解析器可以使用这种。

### XML

对于更复杂的数据格式，后来又诞生了[XML](https://en.wikipedia.org/wiki/XML), 1996年推出后的10年渐渐流行，但是现在的新技术很少使用。 可能是容易写的冗长和臃肿，而且不太直观。对比下xml和json
```xml
<config>
  <post title="Config files: ..."
    date="2019-08-26"
    draft="false">
    <tags>
      <t>tag1</t>
      <t>tag2</t>
    </tags>
  </post>
  ...
</config>
```
```json
[
  { title: "Config files: ...",
    date: "2019-08-26",
    draft: false,
    tags: [
      "tag1",
      "tag2"
    ]
  },
  ...
]
```

### JSON

[JSON](https://en.wikipedia.org/wiki/JSON) 也是可以配置复杂的数据。 JSON是为了在AJAX调用中取代XML而设计的。所以在最初的设计中它是为了数据交换而不是作为一种配置文件。 这可能是JSON不支持注释的原因。
VSCode中扩展了JSON到[JSONC](https://code.visualstudio.com/docs/languages/json#_json-with-comments) “JSON with comments"。但是这不是广泛使用的标准。如果你的配置文件需要注释，不要使用JSON。

### YAML

[YAML](https://en.wikipedia.org/wiki/YAML), 最开始设计为一种 markup 语言（类型HTML），但是后来重新定位为数据。
YAML对于缩进敏感，如果代码的缩进有问题，会导致预期之外的结果和错误。这对于对技术不太了解的配置人员不太友好。
YAML也会将配置的值转换为数据类型(string,number,boolean,date等),这些都是根据值的内容来转换。但是有时候会产生问题。
比如如下的配置
```yaml
tv_shows:
  - 新闻
  - 24
  - !!str 90210
```
这是一个关于电视节目的配置表，`新闻`是一个节目的名称，被解析为`string`，这没有问题。但是第二个选项`24`却被解析为整数，这可能导致程序崩溃。第三个选项明确指定了这个选项为字符串才会避免这个问题。
YAML的配置还有一些坑：
* 配置的1.20 结果用的1.2。yaml 在不显式声明字段值为字符串的时候会把符合数字格式的字段值视为数字去处理，这个时候你的 1.20 会变成 1.2，换成字符串就好了  
* OFF 会被当作false，no 会被映射为false [ref](https://blog.csdn.net/quuqu/article/details/119330533)  
* yaml 只能用space缩进  

### TOML

[TOML](https://github.com/toml-lang/toml) [wiki](https://en.wikipedia.org/wiki/TOML) 相比YAML比较简单，它没有使用缩进来代表数据层级。缩进会被Parser忽略。
TOML有着明确的语法来配置数据类型：strings,integers,floats,booleans,dates,times 等等。
```toml
tv_shows = [
    "新闻",
    "24",
    "90210",
]
```

## 结论

对于配置文件的选择，还是得看你的使用场景/编程语言/用户习惯,等等。明白了不同的配置文件的不同可以帮助你的选择。

## ref

[Config Files: INI, XML, JSON, YAML, TOML](https://www.barenakedcoder.com/blog/2020/03/config-files-ini-xml-json-yaml-toml/)