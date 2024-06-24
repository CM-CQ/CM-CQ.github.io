
# 函数式编程-Stream流
## 1、概述
### 1.1 为什么学？
- 看懂公司的代码
- 大数据量下处理集合效率高
- 代码可读性高
- 消灭嵌套地狱

```
//查询未成年作家的评分在70以上的书籍 由于洋流影响所以作家和书籍可能出现重复，需要进行去重
List<Book> bookList = new ArrayList<>();
Set<Book> uniqueBookValues = new Hashset<>:
Set<Author> uniqueAuthorValues = new Hashset<>();
for (Author author :authors) {
    if (uniqueAuthorValues.add(author)){
        if(author.getAge()< 18){
            List<Book> books = author.getBooks();
            for(Book book :books){
                if(book.getscore()>70){
                    if (uniqueBookValues.add(book)){
                        bookList.add(book);
                    }
                }
            }
        }
    }
}
System.out.println(bookList):
```
```
List<Book> collect = authors.stream()
    .distinct()
    .filter(author -> author.getAge()< 18)
    .map(author -> author.getBooks())
    .flatMap(collection::stream)
    .filter(book -> book.getscore()>170)
    .distinct()
    .co1lect(co1lectors.toList());
System.out.println(collect);
```
## 1.2 函数式编程思想
### 1.2.1 概念
面向对象思想需要关注用什么对象完成什么事情。而函数式编程思想就类似于我们数学中的函数。它主要关注的是对数据进行了什么操作。
### 1.2.2 优点
- 代码简洁，开发快速
- 接近自然语言，易于理解
- 易于"并发编程”

# 2、Lambda表达式
## 2.1 概述
Lambda是IDK8中一个语法糖。他可以对某些匿名内部类的写法进行简化。它是函数式编程思想的一个重要体现。让我们不用关注是什么对象。而是更关注我们对数据进行了什么操作。
## 2.2 核心原则
可推导可省略
## 2.3 基本格式
`(参数列表) -> {代码}`
例一
我们在创建线程并启动时可以使用匿名内部类的写法:
```
new Thread(new Runnable(){
    @override
    public void run() {
        System.out.println("你知道吗 我比你想象的 更想在你身边");
    }).start();
```
可使用Lambda的格式对其进行修改。修改后如下：
```
new Thread(() -> {
    System.out.println("你知道吗 我比你想象的 更想在你身边");
}).start();
```
**例二**
 现有方法定义如下，其中IntBinaryOperator是一个接口。先使用匿名内部类的写法调用该方法。