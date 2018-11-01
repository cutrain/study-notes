# \(Python\)import 和 from ... import ... 的区别和注意事项

## import

import 分为导入一个文件和导入一个包两种情况

* 导入一个文件时，相当于将该文件完全粘贴到import对应的代码块中
* 导入一个包时，相当于将该包文件夹中的\_\_init\_\_.py文件粘贴到对应代码块中。需要注意的是，如果导入子包，则会依次导入每一级的\_\_init\_\_.py。示例如下

{% tabs %}
{% tab title="包结构" %}
```text
foo1
├──__init__.py # print('foo1')
├──file1.py # print('file1')
└──foo2
    ├──file2.py # print('file2')
    └──__init__.py # print('foo2')
```
{% endtab %}

{% tab title="示例代码1" %}
```python
import foo1.foo2.file2
```

```bash
foo1
foo2
file2
```
{% endtab %}

{% tab title="示例代码2" %}
```python
import foo1
```

```text
foo1
```
{% endtab %}
{% endtabs %}

可以发现，`import foo1` 只会导入根目录下的\_\_init\_\_.py，如果需要导入file1.py，则需要执行 `import foo1.file1`

在执行`import foo1.foo2.file2`时，其实相当于导入了三个文件 \_\_init\_\_.py\(foo1\)、\_\_init\_\_.py\(foo2\)、file2.py

## from ... import ...

`from foo import func1` 使得在下文中能够直接使用func1来调用

\`\`

