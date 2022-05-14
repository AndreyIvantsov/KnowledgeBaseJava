---
description: >-
  Java предоставляет класс Date, который доступен в пакете java.util, этот класс
  заключает в себе текущую дату и время.
---

# Дата и время

### Конструкторы <a href="#konstruktory" id="konstruktory"></a>

Класс Date поддерживает два конструктора, которые показаны ниже.

| № | Конструктор и описание                                                                                                                            |
| - | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | <p><strong>Date()</strong><br>Этот конструктор инициализирует объект с текущей датой и временем.</p>                                              |
| 2 | <p><strong>Date(long millisec)</strong><br>Этот конструктор принимает аргумент равный числу миллисекунд, истекших с полуночи 1 января 1970 г.</p> |

### Методы класса Date <a href="#metody-klassa-date" id="metody-klassa-date"></a>

Ниже представлены методы класса Date.

| №  | Методы с описанием                                                                                                                                                                                                                                                                                    |
| -- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1  | <p><strong>boolean after(Date date)</strong><br>Возвращает значение true, если вызывающий объект date содержит дату, которая раньше заданной даты, в противном случае он возвращает значение false.</p>                                                                                               |
| 2  | <p><strong>boolean before(Date date)</strong><br>Возвращает значение true, если вызывающий объект date содержит дату, более раннюю, чем заданная дата, в противном случае он возвращает значение false.</p>                                                                                           |
| 3  | <p><strong>Object clone()</strong><br>Дублирование вызывающего объекта date.</p>                                                                                                                                                                                                                      |
| 4  | <p><strong>int compareTo(Date date)</strong><br>Сравнивает значение вызывающего объекта с этой датой. Возвращает 0, если значения равны. Возвращает отрицательное значение, если объект вызова является более ранним, чем дата. Возвращает положительное значение, если объект вызова позже даты.</p> |
| 5  | <p><strong>int compareTo(Object obj)</strong><br>Работает точно так же compareTo(Date), если объект вызова имеет класс Date. В противном случае вызывает ClassCastException.</p>                                                                                                                      |
| 6  | <p><strong>boolean equals(Object date)</strong><br>Возвращает значение true, если вызывающий объект date содержит то же время и дату, которая указана в date, в противном случае он возвращает значение false.</p>                                                                                    |
| 7  | <p><strong>long getTime()</strong><br>Возвращает количество миллисекунд, истекших с 1 января 1970 года.</p>                                                                                                                                                                                           |
| 8  | <p><strong>int hashCode()</strong><br>Возвращает хэш-код для вызывающего объекта.</p>                                                                                                                                                                                                                 |
| 9  | <p><strong>void setTime(long time)</strong><br>Задает дату и время, соответствующие моменту времени, что представляет собой общее затраченное время в миллисекундах от полуночи 1 января 1970 года.</p>                                                                                               |
| 10 | <p><strong>String toString()</strong><br>Преобразует вызывающий объект date в строку и возвращает результат.</p>                                                                                                                                                                                      |

### Текущая дата и время в Java <a href="#tekuschaya-data-i-vremya-v-java" id="tekuschaya-data-i-vremya-v-java"></a>

Получить текущую дату и время в Java достаточно не трудно. Вы можете использовать простой объект date вместе с методом [toString()](http://proglang.su/java/strings-tostring), чтобы вывести текущую дату и время следующим образом:

```java
import java.util.Date;

public class Test {

   public static void main(String args[]) {
      // Инициализация объекта date
      Date date = new Date();

      // Вывод текущей даты и времени с использованием toString()
      System.out.println(date.toString());
   }
}
```

Получим следующий результат:

```
Sun Nov 13 00:14:19 FET 2016
```

### Сравнение дат <a href="#sravnenie-dat" id="sravnenie-dat"></a>

Существуют три способа в Java сравнить даты:

* Можно использовать функцию getTime(), чтобы получить количество миллисекунд, прошедших с момента полуночи 1 января 1970, для обоих объектов, а затем сравнить эти два значения.
* Вы можете использовать методы before(), after() и equals(). Поскольку 12 число месяца раньше 18 числа, например, new Date(99, 2, 12).before(new Date (99, 2, 18)) возвращает значение true.
* Можно использовать метод compareTo(), который определяется сопоставимым интерфейсом и реализуется по дате.

### Форматирование даты с помощью SimpleDateFormat <a href="#formatirovanie-daty-s-pomoschyu-simpledateformat" id="formatirovanie-daty-s-pomoschyu-simpledateformat"></a>

**SimpleDateFormat** — это конкретный класс для парсинга и форматирования даты в Java. SimpleDateFormat позволяет начать с выбора любых пользовательских шаблонов для форматирования даты и времени. Например:

```java
import java.util.*;
import java.text.*;

public class Test {

   public static void main(String args[]) {
      Date dateNow = new Date();
      SimpleDateFormat formatForDateNow = new SimpleDateFormat("E yyyy.MM.dd 'и время' hh:mm:ss a zzz");

      System.out.println("Текущая дата " + formatForDateNow.format(dateNow));
   }
}
```

Получим следующий результат:

```
Текущая дата Вс 2016.11.13 и время 12:12:36 AM FET
```

### Формат-коды SimpleDateFormat <a href="#format-kody-simpledateformat" id="format-kody-simpledateformat"></a>

Для того, чтобы задать в Java формат даты и времени, используйте строковый шаблон (регулярные выражения) с датой и временем. В этой модели все буквы ASCII зарезервированы как шаблон письма, которые определяются следующим образом:

| Символ | Описание                       | Пример                                |
| ------ | ------------------------------ | ------------------------------------- |
| G      | Обозначение эры                | н.э.                                  |
| y      | Год из четырех цифр            | 2016                                  |
| M      | Номер месяца года              | 11                                    |
| d      | Число месяца                   | 13                                    |
| h      | Формат часа в A.M./P.M.(1\~12) | 7                                     |
| H      | Формат часа(0\~23)             | 19                                    |
| m      | Минуты                         | 30                                    |
| s      | Секунды                        | 45                                    |
| S      | Миллисекунды                   | 511                                   |
| E      | День недели                    | Вс                                    |
| D      | Номер дня в году               | 318                                   |
| F      | Номер дня недели в месяце      | 2 (второе воскресение в этом месяце)  |
| w      | Номер неделя в году            | 46                                    |
| W      | Номер недели в месяце          | 2                                     |
| a      | Маркер A.M./P.M.               | AM                                    |
| k      | Формат часа(1\~24)             | 24                                    |
| K      | Формат часа в A.M./P.M.(0\~11) | 0                                     |
| z      | Часовой пояс                   | FET (Дальневосточноевропейское время) |
| '      | Выделение для текста           | Текст                                 |
| ''     | Одинарная кавычка              | '                                     |

### Форматирование даты с помощью printf <a href="#formatirovanie-daty-s-pomoschyu-printf" id="formatirovanie-daty-s-pomoschyu-printf"></a>

Формат даты и времени можно сделать без труда с помощью метода printf. Вы используете формат двух букв, начиная с t и заканчивая одним из символов в таблице, приведенных ниже. Например:

```java
import java.util.Date;

public class Test {

   public static void main(String args[]) {
      // Инициализация объекта date
      Date date = new Date();

      // Вывод текущей даты и времени с использованием toString()
      String str = String.format("Текущая дата и время: %tc", date);

      System.out.printf(str);
   }
}
```

Получим следующий результат:

```
Текущая дата и время: Вс ноя 13 00:55:59 FET 2016
```

Было бы немного глупо, если Вы должны были бы поставить дату несколько раз для форматирования каждой части. По этой причине формат строки может указывать индекс аргумента для форматирования.

Индекс должен непосредственно следовать за % и завершаться $. Например:

```java
import java.util.Date;

public class Test {
 
   public static void main(String args[]) {
      // Инициализация объекта date
      Date date = new Date();
        
      // Вывод текущей даты с использованием toString()
      System.out.printf("%1$s %2$td %2$tB %2$tY", "Дата:", date);
   }
}
```

Получим следующий результат:

```
Дата: 13 ноября 2016
```

Кроме того, Вы можете использовать <. Это означает, что тот же самый аргумент должен использоваться снова, как и предыдущие спецификации формата. Например:

```java
import java.util.Date;

public class Test {
 
   public static void main(String args[]) {
       // Инициализация объекта date
       Date date = new Date();
        
       // Вывод отформатированной даты (удалите знак = ниже из кода, а то у меня конфликтует этот код с html)
       System.out.printf("%s %te %<=tB %<=tY", "Сегодняшняя дата:", date);
   }
}
```

Получим следующий результат:

```
Сегодняшняя дата: 13 ноября 2016
```

### Символы преобразования даты и времени <a href="#simvoly-preobrazovaniya-daty-i-vremeni" id="simvoly-preobrazovaniya-daty-i-vremeni"></a>

В Java вывод даты в нужном формате можно реализовать с помощью следующих символов преобразования:

| Символ  | Описание                                          | Пример                      |
| ------- | ------------------------------------------------- | --------------------------- |
| c       | Текущее время и дата                              | Вс ноя 13 01:19:27 FET 2016 |
| F       | Формат даты ISO 8601 (год-месяц-день)             | 2016-11-13                  |
| D       | Американский формат даты (месяц/день/год)         | 11/13/16                    |
| T       | 24-часовой формат времени                         | 01:26:09                    |
| r       | 12-часовой формат времени                         | 01:26:51 AM                 |
| R       | 24-часовой формат времени без секунд              | 01:27                       |
| Y       | Текущий год из четырех цифр (с ведущими нулями)   | 2016                        |
| y       | Последние две цифры года (с ведущими нулями)      | 16                          |
| C       | Первые две цифры года (с ведущими нулями)         | 20                          |
| B       | Полное название месяца                            | ноября                      |
| b       | Сокращенное название месяца                       | ноя                         |
| m       | Номер текущего месяца (с ведущими нулями)         | 11                          |
| d       | Номер текущего дня месяца (с ведущими нулями)     | 09                          |
| e       | Номер текущего дня месяца (без ведущих нулей)     | 9                           |
| A       | Полное название текущего дня недели               | воскресенье                 |
| a       | Сокращенное название дня недели                   | Вс                          |
| j       | Количество дней с начала года (с ведущими нулями) | 318                         |
| H       | Формат часа (с ведущими нулями), от 00 до 23      | 01                          |
| k       | Формат часа (без ведущих нулей), от 0 до 23       | 1                           |
| I       | Формат часа (с ведущими нулями), от 01 до 12      | 01                          |
| l       | Формат часа (без ведущих нулей), от 1 до 12       | 1                           |
| M       | Минуты (с ведущими нулями)                        | 38                          |
| S       | Секунды (с ведущими нулями)                       | 50                          |
| L       | Миллисекунды (с ведущими нулями)                  | 382                         |
| N       | Наносекунды (с ведущими нулями)                   | 775000000                   |
| p (%Tp) | Верхний регистр маркера A.M./P.M.                 | AM                          |
| p (%tp) | Нижний регистр маркера A.M./P.M.                  | am                          |
| z       | Часовое смещение RFC 822 по GMT                   | +0300                       |
| Z       | Часовой пояс                                      | FET                         |
| s       | Секунды, начиная с 1970-01-01 00:00:00 GMT        | 1478991147                  |
| Q       | Миллисекунды, начиная с 1970-01-01 00:00:00 GMT   | 1478991172134               |

Есть и другие полезные классы, связанные с датой и временем. Для получения более подробной информации обратитесь к стандартной документации Java.

### Преобразование строки в дату <a href="#preobrazovanie-stroki-v-datu" id="preobrazovanie-stroki-v-datu"></a>

Класс SimpleDateFormat имеет некоторые дополнительные методы, в частности parse(), который в Java поможет нам перевести строку в дату соответствии с форматом, хранящимся в данном объекте SimpleDateFormat. Например:

```java
import java.util.*;
import java.text.*;
  
public class Test {

   public static void main(String args[]) {
      SimpleDateFormat ft = new SimpleDateFormat ("yyyy-MM-dd"); 
      String str = args.length == 0 ? "2011-11-11" : args[0]; 

      System.out.print("Строка " + str + " распаршена как "); 
      Date parsingDate;
      try {
         parsingDate = ft.parse(str); 
         System.out.println(parsingDate); 
      }catch (ParseException e) { 
         System.out.println("Нераспаршена с помощью " + ft); 
      }
   }
}
```

Получим следующий результат:

```
Строка 2011-11-11 распаршена как Fri Nov 11 00:00:00 FET 2011
```

### Задержка по времени <a href="#zaderzhka-po-vremeni" id="zaderzhka-po-vremeni"></a>

Вы можете увеличить или уменьшить время работы программы на любой период времени, от одной миллисекунды до срока службы вашего компьютера. Например, следующая программа будет находится в режиме ожидания в течение 10 секунд:

```java
import java.util.*;
  
public class Test {
   public static void main(String args[]) {
      try { 
         System.out.println(new Date() + "\n"); 
         Thread.sleep(10000); // Замораживает весь поток на 10 секунд
         System.out.println(new Date() + "\n"); 
      } catch (Exception e) { 
          System.out.println("Получили исключение!"); 
      }
   }
}
```

Получим следующий результат:

```
Sun Nov 13 02:42:16 FET 2016

Sun Nov 13 02:42:26 FET 2016
```

Вместо Thread.sleep() рекомендуется использовать TimeUnit(): TimeUnit.NANOSECONDS.sleep(), TimeUnit.MICROSECONDS.sleep(), TimeUnit.MILLISECONDS.sleep(), TimeUnit.SECONDS.sleep(), TimeUnit.MINUTES.sleep(), TimeUnit.HOURS.sleep() или TimeUnit.DAYS.sleep().

### Время выполнения программы <a href="#vremya-vypolneniya-programmy" id="vremya-vypolneniya-programmy"></a>

Довольно просто можно узнать время выполнения кода вашей программы с помощью System.currentTimeMillis(). Для этого необходимо в начале программы записать в переменную значение System.currentTimeMillis(), а в конце вычесть из текущего значения System.currentTimeMillis() переменную, записанную вначале. Рассмотрим пример, в котором измерим скорость работы кода программы, которая выводит 10 случайных чисел на экран.

```java
import java.util.*;
  
public class Test {
   public static void main(String args[]) {
      // Начала отсчета
      long start = System.currentTimeMillis();
        
      // Код программы. Получение 10 случайных чисел от 0 до 9 и вывод на экран
      for(int i = 1;i <= 10;i++) {
          System.out.println("Случайное число №" + i + ": " + (int)(Math.random() * 10));
      }

      // Получение и запись в переменную timeWorkCode времени работы программы
      long timeWorkCode = System.currentTimeMillis() - start;  
      // Вывод времени выполнения работы кода на экран
      System.out.println("Скорость выполнения программы: " + timeWorkCode + " миллисекунд");
   }
}
```

Получим следующий результат:

```
Случайное число №1: 0
Случайное число №2: 5
Случайное число №3: 9
Случайное число №4: 9
Случайное число №5: 0
Случайное число №6: 2
Случайное число №7: 0
Случайное число №8: 3
Случайное число №9: 5
Случайное число №10: 9
Скорость выполнения программы: 2 миллисекунд
```

### Разница дат в Java <a href="#raznica-dat-v-java" id="raznica-dat-v-java"></a>

Иногда Вам может понадобиться рассчитать разницу между датами, измерить точку во времени в миллисекундах. Поэтому давайте перепишем еще раз пример, находящийся выше:

```java
import java.util.*;

public class Test {

   public static void main(String args[]) {
      try {
         long start = System.currentTimeMillis();
         System.out.println(new Date() + "\n");
         
         Thread.sleep(10000);
         System.out.println(new Date() + "\n");
         
         long end = System.currentTimeMillis();
         long diff = end - start;
         System.out.println("Разница между датами: " + diff + " миллисекунд");
      }catch (Exception e) {
         System.out.println("Получили исключение!");
      }
   }
}
```

Получим следующий результат:

```
Sun Nov 13 03:22:10 FET 2016

Sun Nov 13 03:22:20 FET 2016

Разница между датами: 10081 миллисекунд
```

### Количество дней между датами <a href="#kolichestvo-dney-mezhdu-datami" id="kolichestvo-dney-mezhdu-datami"></a>

А иногда Вам может понадобиться в Java узнать количество дней, часов, минут и т.п. между датами. Рассмотрим один из способов нахождения дней между двумя датами ниже в примере:

```java
import java.util.*;

public class Test {

   public static void main(String args[]) {
      String date1 = "01.03.2016";
      String date2 = "01.02.2016";
        
      SimpleDateFormat format = new SimpleDateFormat("dd.MM.yyyy");
        
      Date dateOne = null;
      Date dateTwo = null;
        
      try {
          dateOne = format.parse(date1);
          dateTwo = format.parse(date2);
      } catch (Exception e) {
          e.printStackTrace();
      }
        
      // Количество дней между датами в миллисекундах
      long difference = dateOne.getTime() - dateTwo.getTime();
      // Перевод количества дней между датами из миллисекунд в дни
      int days =  (int)(difference / (24 * 60 * 60 * 1000)); // миллисекунды / (24ч * 60мин * 60сек * 1000мс)
      // Вывод разницы между датами в днях на экран
      System.out.println(days + " дн.");
   }
}
```

Получим следующий результат:

```
29 дн.
```

### Класс GregorianCalendar <a href="#klass-gregoriancalendar" id="klass-gregoriancalendar"></a>

**GregorianCalendar** является конкретной реализацией класса Calendar, который отображает обычный григорианский календарь, с которым Вы знакомы. Мы не обсуждали класс Calendar в этом учебнике, для этого Вы можете посмотреть стандартную документацию Java.

Метод getInstance() Calendar возвращает GregorianCalendar, который инициализирован по умолчанию текущей датой и временем, локализацией и часовым поясом. GregorianCalendar определяет два поля: н. э и до н. э. Они представляют собой две эпохи, которые определяются по григорианскому календарю.

Существует несколько конструкторов для объектов GregorianCalendar:

| № | Конструктор и его описание                                                                                                                                                                                                      |
| - | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | <p><strong>GregorianCalendar()</strong><br>Создает значение GregorianCalendar, используя по умолчанию текущей датой и временем, локализацией и часовым поясом.</p>                                                              |
| 2 | <p><strong>GregorianCalendar(int year, int month, int date)</strong><br>Создает GregorianCalendar в соответствии с заданной датой в часовом поясе и локализацией по умолчанию.</p>                                              |
| 3 | <p><strong>GregorianCalendar(int year, int month, int date, int hour, int minute)</strong><br>Создает GregorianCalendar в соответствии с заданной датой и временем в часовом поясе и локализацией по умолчанию.</p>             |
| 4 | <p><strong>GregorianCalendar(int year, int month, int date, int hour, int minute, int second)</strong><br>Создает GregorianCalendar в соответствии с заданной датой и временем в часовом поясе и локализацией по умолчанию.</p> |
| 5 | <p><strong>GregorianCalendar(Locale aLocale)</strong><br>Создает GregorianCalendar в соответствии с текущим временем в часовом поясе по умолчанию в рамках заданной локализации.</p>                                            |
| 6 | <p><strong>GregorianCalendar(TimeZone zone)</strong><br>Конструирует GregorianCalendar, основанный на текущем времени в данной зоне времени с локализацией по умолчанию.</p>                                                    |
| 7 | <p><strong>GregorianCalendar(TimeZone zone, Locale aLocale)</strong><br>Конструирует GregorianCalendar, основанный на текущем времени в заданном часовом поясе и локализации.</p>                                               |

Список нескольких полезных методов, предоставляемых классом GregorianCalendar:

| №  | Методы с описанием                                                                                                                                                             |
| -- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1  | <p><strong>void add(int field, int amount)</strong><br>Добавляет указанное количество времени в данное временное поле в соответствии с правилами календаря.</p>                |
| 2  | <p><strong>protected void computeFields()</strong><br>Преобразует время по Гринвичу в миллисекунды до значения полей времени.</p>                                              |
| 3  | <p><strong>protected void computeTime()</strong><br>Преобразует значения временного поля Календаря в UTC формате в миллисекундах.</p>                                          |
| 4  | <p><strong>boolean equals(Object obj)</strong><br>Сравнивает этот GregorianCalendar эталонным объектом.</p>                                                                    |
| 5  | <p><strong>int get(int field)</strong><br>Получает значение для поля заданного времени.</p>                                                                                    |
| 6  | <p><strong>int getActualMaximum(int field)</strong><br>Возвращает максимальное значение, которое это поле может иметь, учитывая текущую дату.</p>                              |
| 7  | <p><strong>int getActualMinimum(int field)</strong><br>Возвращает минимальное значение, которое это поле может иметь, учитывая текущую дату.</p>                               |
| 8  | <p><strong>int getGreatestMinimum(int field)</strong><br>Возвращает наибольшее минимальное значение для данного поля, если изменяется.</p>                                     |
| 9  | <p><strong>Date getGregorianChange()</strong><br>Получает изменения даты по григорианскому календарю.</p>                                                                      |
| 10 | <p><strong>int getLeastMaximum(int field)</strong><br>Возвращает минимально максимальное значение для данного поля, если изменяется.</p>                                       |
| 11 | <p><strong>int getMaximum(int field)</strong><br>Возвращает максимальное значение для данного поля.</p>                                                                        |
| 12 | <p><strong>Date getTime()</strong><br>Определяет текущее время в соответствии с календарем.</p>                                                                                |
| 13 | <p><strong>long getTimeInMillis()</strong><br>Получает текущее время по Календарю как длительное.</p>                                                                          |
| 14 | <p><strong>TimeZone getTimeZone()</strong><br>Возвращает часовой пояс.</p>                                                                                                     |
| 15 | <p><strong>int getMinimum(int field)</strong><br>Возвращает минимальное значение для данного поля.</p>                                                                         |
| 16 | <p><strong>int hashCode()</strong><br>Переопределите хэш-код.</p>                                                                                                              |
| 17 | <p><strong>boolean isLeapYear(int year)</strong><br>Определяет, является ли год високосным.</p>                                                                                |
| 18 | <p><strong>void roll(int field, boolean up)</strong><br>Добавление или вычитание (вверх/вниз) одной единицы времени в данном временном поле без изменений в больших полях.</p> |
| 19 | <p><strong>void set(int field, int value)</strong><br>Устанавливает временное поле с заданным значением.</p>                                                                   |
| 20 | <p><strong>void set(int year, int month, int date)</strong><br>Задает значения для поля год, месяц и дата.</p>                                                                 |
| 21 | <p><strong>void set(int year, int month, int date, int hour, int minute)</strong><br>Задает значения для поля год, месяц, дату, час и минуту.</p>                              |
| 22 | <p><strong>void set(int year, int month, int date, int hour, int minute, int second)</strong><br>Задает значения для поля год, месяц, дату, час, минуту и секунду.</p>         |
| 23 | <p><strong>void setGregorianChange(Date date)</strong><br>Устанавливает дату изменения грегорианского календаря.</p>                                                           |
| 24 | <p><strong>void setTime(Date date)</strong><br>Устанавливает в соответствии с данным календарем текущее время с заданной датой.</p>                                            |
| 25 | <p><strong>void setTimeInMillis(long millis)</strong><br>Устанавливает в соответствии с данным календарем текущее время от заданного long значения.</p>                        |
| 26 | <p><strong>void setTimeZone(TimeZone value)</strong><br>Задает часовой пояс со значением заданного часового пояса.</p>                                                         |
| 27 | <p><strong>String toString()</strong><br>Возвращает строковое представление календаря.</p>                                                                                     |

### Пример 1: вывод текущей даты и времени, високосный год <a href="#primer-1-vyvod-tekuschey-daty-i-vremeni-visokosnyy-god" id="primer-1-vyvod-tekuschey-daty-i-vremeni-visokosnyy-god"></a>

```java
import java.util.*;

public class Test {

   public static void main(String args[]) {
      String months[] = {"Янв", "Фев", "Мар", "Апр", "Май", "Июн", "Июл", "Авг", "Сен", 
         "Окт", "Ноя", "Дек"};
      
      int year;
      // Создание григорианского календаря инициализированного
      // текущей датой и временем в
      // локализации и часовом поясе по умолчанию.
      
      GregorianCalendar gcalendar = new GregorianCalendar();
      
      // Вывод реального времени и даты
      System.out.print("Дата: ");
      System.out.print(months[gcalendar.get(Calendar.MONTH)]);
      System.out.print(" " + gcalendar.get(Calendar.DATE) + " ");
      System.out.println(year = gcalendar.get(Calendar.YEAR));
      System.out.print("Время: ");
      System.out.print(gcalendar.get(Calendar.HOUR) + ":");
      System.out.print(gcalendar.get(Calendar.MINUTE) + ":");
      System.out.println(gcalendar.get(Calendar.SECOND));

      // Тест если текущий год является високосным
      if(gcalendar.isLeapYear(year)) {
         System.out.println(year + " - високосный год");
      }else {
         System.out.println(year + " - не високосный год");
      }
   }
}
```

Получим следующий результат:

```
Дата: Ноя 13 2016
Время: 2:31:18
2016 - високосный год
```

Для изучения полного списка констант в классе календаря обратитесь к стандартной документации Java.

### Пример 2: получить день недели по дате <a href="#primer-2-poluchit-den-nedeli-po-date" id="primer-2-poluchit-den-nedeli-po-date"></a>

```java
import java.util.*;

public class Test {

   public static void main(String args[]) {
      String date = "17.11.2016";
        
      // Переводим строку в дату  
      SimpleDateFormat format = new SimpleDateFormat("dd.MM.yyyy");
      Date dayWeek = null;
      try {
          dayWeek = format.parse(date);
      } catch (Exception e) {
          e.printStackTrace();
      }
      
      // Вывод дня недели даты на экран
      System.out.println(new SimpleDateFormat("EEEE").format(dayWeek));
   }
}
```

Получим следующий результат:

```
четверг
```
