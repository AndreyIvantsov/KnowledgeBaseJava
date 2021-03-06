---
description: class String
---

# Особенности строк

### Сравнение строк

<mark style="color:orange;">**Для сравнения строк ВСЕГДА используй метод equals()! Сравнивая строки, ты почти всегда имеешь в виду сравнение их текста, а не ссылок, областей памяти и прочего.**</mark>

Метод equals() делает именно то, что тебе нужно.

Оператор **`==` ** сравнивает ссылки.

Метод **`equals` ** сравнивает значения.

Следовательно, если вы хотите сравнить строки на равенство, следует использовать **`equals`**.

Однако в некоторых случаях строки гарантированно представлены одним и тем же объектом благодаря [пулу строк](https://ru.wikipedia.org/wiki/%D0%9F%D1%83%D0%BB\_%D1%81%D1%82%D1%80%D0%BE%D0%BA) ([string interning](https://en.wikipedia.org/wiki/String\_interning)). Эти случаи явно описаны в [спецификации языка Java](http://docs.oracle.com/javase/specs/jls/se7/html/jls-3.html#jls-3.10.5).

**Пул строк** — область для хранения всех строковых значений, которые ты создаешь в своей программе.

Оператор `==` используется для проверки, что две строки указывают на один и тот же объект.

```java
// Эти строки имеют одно и тоже же значение
new String("test").equals("test") // --> true 

// ...но это разные объекты
new String("test") == "test" // --> false 

// ...эти строки тоже разные объекты
new String("test") == new String("test") // --> false 

// ...но эти строки указывают на один и тот же объект,
// потому что компилятор добавляет все литералы в пул.
"test" == "test" // --> true 

// Конкатенация литералов тоже происходит на стадии компиляции,
// поэтому они указывают на один объект
"test" == "te" + "st" // --> true

// но вызов substring() происходит во время выполнения,
// в результате получаются разные объекты.
"test" == "!test".substring(1) // --> false

// Строки из пула могут быть получены с помощью вызова intern().
"test" == "!test".substring(1).intern() // --> true
```

Надо отметить, что `==` заметно быстрее, чем `equals` (сравнение ссылки вместо вызова метода и посимвольного сравнения, если строки разной длины), поэтому, если вы работаете со строками из пула (или системного, или своего), замена `equals` на `==` может привести к заметному ускорению. Но это **случается очень редко**.

Остерегайтесь вызова `equals` на `null`! Оператор `==` прекрасно сравнивает строки, если одна или более из них равна `null`, но вызов метода `equals` на строке, равной `null`, приведёт к исключению.

Для сравнения строк, которые могут быть равны `null`, вы можете воспользоваться следующим методом:

```java
public static boolean equals(String str1, String str2) {
    return str1 == null ? str2 == null : str1.equals(str2);
}
```

Он присутствует в некоторых сторонних библиотеках, например, в Apache Commons.

Если вы пользуетесь современными средами разработки, то они предупредят, если вы попытаетесь сравнить строки с помощью оператора `==`. Всегда обращайте внимание на подобные предупреждения.

### Метод String.intern()

У класса `String` есть еще один хитрый метод — `intern()`; Метод `intern()` напрямую работает со `String Pool`’ом. Если ты вызываешь метод `intern()` у какой-то строки, он:

* Смотрит, есть ли строка с таким текстом в пуле строк
* Если есть — возвращает ссылку на нее в пуле
* Если же нет — помещает строку с этим текстом в пул строк и возвращает ссылку на нее.

Применив метод `intern()` к ссылке на строку, которая создавалась через new, мы можем сравнивать ее со ссылкой на строку из `String Pool`’a через оператор `==`.

```
```

```java
public class Main {

   public static void main(String[] args) {

       String s1 = "JavaRush - лучший сайт для изучения Java!";
       String s2 = new String("JavaRush - лучший сайт для изучения Java!");
       System.out.println(s1 == s2.intern());
   }
}
```

Вывод в консоль:

```
true
```

Раньше, когда мы сравнивали их без `intern()`, результат был равен false. Теперь же метод `intern()` проверил, есть ли строка с текстом "JavaRush — лучший сайт для изучения Java!" в пуле строк. Разумеется, она там есть: мы создали ее, когда написали

```
```

```java
String s1 = "JavaRush — лучший сайт для изучения Java!";
```

Была проведена проверка, что ссылка `s1` и ссылка, возвращенная методом `s2.intern()` указывают на одну область в памяти, и, конечно, так оно и есть:)
