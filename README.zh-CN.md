# 垃圾代码书写准则

[![State-of-the-art Shitcode](https://img.shields.io/static/v1?label=State-of-the-art&message=Shitcode&color=7B5804)](https://github.com/trekhleb/state-of-the-art-shitcode)

这是一个你的项目应该遵循的垃圾代码书写准则的列表，把称为适当的垃圾代码。

_Read this in other languages:_
[_English_](https://github.com/trekhleb/state-of-the-art-shitcode)

## 获取徽章

如果你的仓库遵循垃圾代码书写准则，你应该用下面的"state-of-the-art shitcode" 徽章：

[![State-of-the-art Shitcode](https://img.shields.io/static/v1?label=State-of-the-art&message=Shitcode&color=7B5804)](https://github.com/trekhleb/state-of-the-art-shitcode)

标记徽章的源代码:

```
[![State-of-the-art Shitcode](https://img.shields.io/static/v1?label=State-of-the-art&message=Shitcode&color=7B5804)](https://github.com/trekhleb/state-of-the-art-shitcode)
```

## 准则

### 💩 以一种容易造成代码混淆的方式命名变量

命名越短，就需要越多的时间去思考代码逻辑等问题。

_Good 👍🏻_

```java
int a = 42;
```

_Bad 👎🏻_

```java
int age = 42;
```

### 💩 变量/方法命名风格不统一

为风格不统一干杯。

_Good 👍🏻_

```java
int wWidth = 640;
int w_height = 480;
```

_Bad 👎🏻_

```java
int windowWidth = 640;
int windowHeight = 480;
```

### 💩 不写注释

反正没人能读懂你的代码。

_Good 👍🏻_

```java
int cdr = 700;
```

_Bad 👎🏻_

注释应该包含一些“为什么”，而不是一些“是什么”。如果代码连是“什么”都表达不清楚，那代码也太烂了。

```java
// 700ms 的数量是从 UX A/B 测试结果中得到的一个经验值。
// @查看: <详细解释 700 的一个链接>
int callbackDebounceRate = 700;
```

### 💩 使用母语写注释

如果你的母语是英语，那么请忽略这条准则。

_Good 👍🏻_

```java
// Закриваємо модальне віконечко при виникненні помилки.
toggleModal(false);
```

_Bad 👎🏻_

```java
// 隐藏错误弹窗
toggleModal(false);
```

PS：如果英语书写能力不是很强的话，建议还是用母语吧。毕竟说清楚总比说不清楚要强。

### 💩 声明变量的风格不统一

再次为风格不统一干杯。

_Good 👍🏻_

```java
String [] i1 = {"沉", "默", "王", "二"};
String i2 [] = {"沉", "默", "王", "三"};
```

_Bad 👎🏻_

```java
String [] wanger = {"沉", "默", "王", "二"};
String wangsan [] = {"沉", "默", "王", "三"};
```

### 💩 尽可能把代码写成一行

_Good 👍🏻_

```java
IntStream.range(1, 5).boxed().map(i -> { System.out.print("Happy Birthday "); if (i == 3) return "dear NAME"; else return "to You"; }).forEach(System.out::println);
```

_Bad 👎🏻_

```java
for (int i = 1; i < 5; i++) {
    System.out.println("Happy Birthday " + (i == 3 ? "dear NAME" : "to you"));
}
```

### 💩 对错误信息不管不顾

无论什么时候发现错误，都没有必要让其他人知道。

_Good 👍🏻_

```java
try {
  // 意料之外的情况。
} catch (error) {
  // tss... 🤫
}
```

_Bad 👎🏻_

```java
try {
  // 意料之外的情况。
} catch (error) {
  // and/or
  logError(error);
}
```

### 💩 使用大量的全局变量

全球化的原则。

_Good 👍🏻_

```java
int x = 5;

void multi() {
  x = x * 2;
}

multi(); // 现在 x 是 10
```

_Bad 👎🏻_

```java
int x = 5;

int multi(int num) {
  return num * 2;
}

x = multi(x); // 现在 x 是 10
```

### 💩 声明根本不会使用的变量

万一以后用了呢？以备不时之需。

_Good 👍🏻_

```java
int sum(int a, int b, int c) {
  int timeout = 1300;
  int result = a + b;
  return a + b;
}
```

_Bad 👎🏻_

```java
int sum(int a, int b) {
  return a + b;
}
```

### 💩 如果条件允许的话，从不指定类型。

_Good 👍🏻_

```java
// 享受便捷的快乐
List list = new ArrayList();
list.add("沉默王二");
list.add(18);
```

_Bad 👎🏻_

```java
List<String> nameList = new ArrayList<String>();

// 编译出错
nameList.add(18);
```

### 💩 没鸟用的代码

看起来更严谨，其实很多余。

_Good 👍🏻_

```java
Integer multi(Object num) {
    if (!(num instanceof Integer)) {
        return null;
    } else if (num != null) {
        return (Integer) num * 2;
    }
    return null;
}
```

_Bad 👎🏻_

```java
Integer multi(Object num) {
    if (num instanceof Integer) {
        return (Integer) num * 2;
    }
    return null;
}
```

### 💩 大量的 if-else 嵌套

_Good 👍🏻_

```java
void someMethod(int a, int b, int c) {
    if (a > 0) {
        if (b > 0) {
            if (c > 0) {
               int result = a / b / c;
            }
        }
    }
}
```

_Bad 👎🏻_

```java
void someMethod1(int a, int b, int c) {
    if (a < 0 || b < 0 || c < 0) {
        return;
    }
    int result = a / b / c;
}
```

### 💩 参差不齐地缩进

参差不齐乃幸福本源。

_Good 👍🏻_

```java
String [] wanger = {"沉", 
        "默", "王", "二"};
String [] wangsan = {"沉", "默", "王", "三"};
Arrays.asList(wanger).stream().
        forEach(System.out::println);
Arrays.asList(wangsan).
        stream().
                forEach(System.out::println);
```

_Bad 👎🏻_

```javascript
String [] wanger = {"沉", "默", "王", "二"};
String [] wangsan = {"沉", "默", "王", "三"};
Arrays.asList(wanger)
        .stream()
        .forEach(System.out::println);
Arrays.asList(wangsan)
        .stream()
        .forEach(System.out::println);
```

### 💩 代码行数多的方法的比少的好

不要把代码逻辑分成可读的部分。

- 一个类中的代码行数超过 10000 行。
- 一个方法中的代码行数超过 1000 行。
- 一个方法里既做减法处理又做加法处理，还做乘除的处理。

### 💩 不要测试你的代码

代码测试是测试工程师的事，关我屁事。

### 💩 避免代码风格统一

随心所欲地编写代码，特别是在一个团队中有多个开发人员的情况下，我崇尚“自由”。

### 💩 不要写文档

从一开始就不要。

### 💩 不要删除废弃掉的代码

代码尽管已经废弃了，注释掉就行了，没必要删掉。
