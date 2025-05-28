---
title: "Markdown 指南"
description: "以下是在 Astro 中编写 Markdown 内容时可以使用的一些基本语法示例。"
pubDate: "05 17 2025"
image: /image/markdown/background.png
categories:
  - tech
tags:
  - Markdown
badge: FE
---

## 标题

以下 HTML `<h1>`—`<h6>` 元素表示六个级别的章节标题。 `<h1>` 是最高的部分级别， 而 `<h6>` 是最低的。

# H1

## H2

### H3

#### H4

##### H5

###### H6

## 段落

&emsp;&emsp;你有没有权利向我们透露你所来自的那个世界的秘密，哪怕只透露一个？’我诗剧中的老法官问他，接着就自己代他回答，‘不，你没有权利；你对自己以前说过的话不得再作什么补充，不得剥夺人们的自由，当年你还在人世时曾竭力捍卫这种自由。不论你带来什么新的信息,都将侵犯人们的信仰自由，因为此信息将被视为奇迹，而人们的信仰自由你在一千五百年前就看得比什么都宝贵。当初你自己经常这样说：“我要使你们成为自由的人。”现在你看到了这些“自由的人”，’老人忽然露出淡淡的一丝若有所思的笑容。

&emsp;&emsp;‘我们曾为此付出昂贵的代价’，他严厉地瞧着囚徒，继续说,‘但我们终于彻底解决了这件事，以你的名义。我们为这自由折腾了十五个世纪但现在解决了，解决得很牢靠。你不信解决得很牢靠？你瞧着我的样子挺温顺，你甚至不屑于向我表示愤慨。但是我告诉你,如今，正是现在而不是过去，这些人比任何时候都相信他们有充分的自由，其实是他们自己把他们的自由乖乖地放到我们的脚边。但这是我们努力的结果，而你所希望的是这样的自由吗？’

## 图像

#### 语法

```markdown
![Alt text](./full/or/relative/path/of/image)
```

#### Output

![blog placeholder](/image/markdown/non.jpg)

## 块引用

blockquote 元素表示从其他来源引用的内容，可以选择使用必须在 `footer` or `cite` 元素内的引用，也可以选择使用内联更改，例如注释和缩写。

### 没有署名的块引用

#### 语法

```markdown
> Tiam, ad mint andaepu dandae nostion secatur sequo quae.
> **Note** that you can use _Markdown syntax_ within a blockquote.
```

#### Output

> Tiam, ad mint andaepu dandae nostion secatur sequo quae.
> **Note** that you can use _Markdown syntax_ within a blockquote.

### 署名的块引用

#### 语法

```markdown
> Don't communicate by sharing memory, share memory by communicating.<br>
> — <cite>Rob Pike[^1]</cite>
```

#### Output

> Don't communicate by sharing memory, share memory by communicating.<br>
> — <cite>Rob Pike[^1]</cite>

[^1]: The above quote is excerpted from Rob Pike's [talk](https://www.youtube.com/watch?v=PAAkCSZUG1c) during Gopherfest, November 18, 2015.

## 表格

#### 语法

```markdown
| Italics   | Bold     | Code   |
| --------- | -------- | ------ |
| _italics_ | **bold** | `code` |
```

#### Output

| Italics   | Bold     | Code   |
| --------- | -------- | ------ |
| _italics_ | **bold** | `code` |

## 代码块

#### 语法

我们可以在新行中使用 3 个反引号 ``` 并在新行上编写 snippet 并以 3 个反引号结束，为了突出特定于语言的 syntac，在前 3 个反引号后写下语言名称的一个单词，例如。HTML、JavaScript、CSS、Markdown、TypeScript、TXT、Bash

````markdown
```cpp
#include <bits/stdc++.h>
using namespace std;
const int N = 1e5 + 5;
int n, k, a[N];
long long ans;
vector<int> v[N];
int main()
{
    scanf("%d%d", &n, &k);
    for (int i = 1; i <= n; i++)
    {
        scanf("%d", &a[i]);
        v[i % k].push_back(a[i]);
    }
    for (int i = 0; i < k; i++)
        sort(v[i].rbegin(), v[i].rend());
    for (int i = 0; i < k; i++)
    {
        for (int j = 0; j + 1 < v[i].size(); j += 2)
        {
            ans += v[i][j] + v[i][j + 1];
        }
    }
    printf("%lld\n", ans);
    return 0;
}
```
````

Output

```cpp
#include <bits/stdc++.h>
using namespace std;
const int N = 1e5 + 5;
int n, k, a[N];
long long ans;
vector<int> v[N];
int main()
{
    scanf("%d%d", &n, &k);
    for (int i = 1; i <= n; i++)
    {
        scanf("%d", &a[i]);
        v[i % k].push_back(a[i]);
    }
    for (int i = 0; i < k; i++)
        sort(v[i].rbegin(), v[i].rend());
    for (int i = 0; i < k; i++)
    {
        for (int j = 0; j + 1 < v[i].size(); j += 2)
        {
            ans += v[i][j] + v[i][j + 1];
        }
    }
    printf("%lld\n", ans);
    return 0;
}
```

## 列表类型

### 有序列表

#### 语法

```markdown
1. First item
2. Second item
3. Third item
```

#### Output

1. First item
2. Second item
3. Third item

### 无序列表

#### 语法

```markdown
- List item
- Another item
- And another item
```

#### Output

- List item
- Another item
- And another item

### 嵌套列表

#### 语法

```markdown
- Fruit
  - Apple
  - Orange
  - Banana
- Dairy
  - Milk
  - Cheese
```

#### Output

- Fruit
  - Apple
  - Orange
  - Banana
- Dairy
  - Milk
  - Cheese

## 其他元素

#### 语法

```markdown
<abbr title="Graphics Interchange Format">GIF</abbr> is a bitmap image format.

H<sub>2</sub>O

X<sup>n</sup> + Y<sup>n</sup> = Z<sup>n</sup>

Press <kbd><kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>Delete</kbd></kbd> to end the session.

Most <mark>salamanders</mark> are nocturnal, and hunt for insects, worms, and other small creatures.
```

#### Output

<abbr title="Graphics Interchange Format">GIF</abbr> is a bitmap image format.

H<sub>2</sub>O

X<sup>n</sup> + Y<sup>n</sup> = Z<sup>n</sup>

Press <kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>Delete</kbd> to end the session.

Most <mark>salamanders</mark> are nocturnal, and hunt for insects, worms, and other small creatures.
