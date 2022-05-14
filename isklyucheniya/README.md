# Исключения



[Ссылка на статью](http://proglang.su/java/exceptions)

#### Иерархия исключений

![](<../.gitbook/assets/изображение (3) (1).png>)

### Методы исключений <a href="#metody-isklyucheniy" id="metody-isklyucheniy"></a>

Далее представлен список важных методов, доступных в классе Throwable.

| № | Метод и описание                                                                                                                                                                                                                                                 |
| - | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | <p><strong>public String getMessage()</strong><br>Возврат подробного сообщения о произошедшем исключении. Инициализация данного сообщения производится в конструкторе Throwable.</p>                                                                             |
| 2 | <p><strong>public Throwable getCause()</strong><br>Возврат причины исключения, представленной объектом Throwable.</p>                                                                                                                                            |
| 3 | <p><strong>public String toString()</strong><br>Возврат имени класса, соединенного с результатом getMessage().</p>                                                                                                                                               |
| 4 | <p><strong>public void printStackTrace()</strong><br>Выведение результата toString() совместно с трассировкой стека в System.err, поток вывода ошибок.</p>                                                                                                       |
| 5 | <p><strong>public StackTraceElement [] getStackTrace()</strong><br>Возврат массива, содержащего каждый элемент в трассировке стека. Элемент с номером 0 представляет вершину стека вызовов, последний элемент массива отображает метод на дне стека вызовов.</p> |
| 6 | <p><strong>public Throwable fillInStackTrace()</strong><br>Заполняет трассировку стека данного объекта Throwable текущей трассировкой стека, дополняя какую-либо предшествующую информацию в трассировке стека.</p>                                              |

### Обработка исключений — try и catch <a href="#obrabotka-isklyucheniy-try-i-catch" id="obrabotka-isklyucheniy-try-i-catch"></a>

Метод производит обработку исключения при использовании ключевых слов **try** и **catch**.

#### Описание <a href="#opisanie" id="opisanie"></a>

Блок try/catch размещается в начале и конце кода, который может сгенерировать исключение. Код в составе блока try/catch является защищенным кодом, синтаксис использования try/catch выглядит следующим образом:

```java
try {
   // Защищенный код
}catch(НазваниеИсключения e1) {
   // Блок catch
}
```

Код, предрасположенный к исключениям, размещается в блоке try. В случае возникновения исключения, обработка данного исключения будет производиться соответствующим блоком catch. За каждым блоком try должен немедленно следовать блок catch либо блок finally.

Оператор catch включает объявление типа исключения, которое предстоит обработать. При возникновении исключения в защищенном коде, блок catch (либо блоки), следующий за try, будет проверен. В случае, если тип произошедшего исключения представлен в блоке catch, исключение передается в блок catch аналогично тому, как аргумент передается в параметр метода.

#### Пример <a href="#primer" id="primer"></a>

Ниже представлен массив с заявленными двумя элементами. Попытка кода получить доступ к третьему элементу массива повлечет за собой генерацию исключения.

```java
import java.io.*;

public class Test {

   public static void main(String args[]) {
      try {
         int array[] = new int[2];
         System.out.println("Доступ к третьему элементу:" + array[3]);
      }catch(ArrayIndexOutOfBoundsException e) {
         System.out.println("Исключение:" + e);
      }
      System.out.println("Вне блока");
   }
}
```

Вследствие этого будет получен следующий результат:

```
Исключение:java.lang.ArrayIndexOutOfBoundsException: 3
Вне блока
```

### Ключевые слова throws/throw <a href="#klyuchevye-slova-throws-throw" id="klyuchevye-slova-throws-throw"></a>

В случае если метод не может осуществить обработку контролируемого исключения, производится соответствующее уведомление при использовании ключевого слова throws в Java. Ключевое слово throws появляется в конце сигнатуры метода.

При использовании ключевого слова throw вы можете произвести обработку вновь выявленного исключения либо исключения, которое было только что перехвачено.

Следует внимательно различать ключевые слова throw и throws в Java, так как throws используется для отложенной обработки контролируемого исключения, а throw, в свою очередь, используется для вызова заданного исключения.

Представленный ниже метод отображает, что им генерируется RemoteException:

#### Пример 1 <a href="#primer-1" id="primer-1"></a>

```java
import java.rmi.RemoteException;
public class Test {

   public void deposit(double amount) throws RemoteException {
      // Реализация метода
      throw new RemoteException();
   }
   // Остаток определения класса
}
```

Метод также может объявить о том, что им генерируется более чем одно исключение, в случае чего исключения представляются в виде перечня, отделенные друг от друга запятыми. К примеру, следующий метод оповещает о том, что им генерируются RemoteException и InsufficientFundsException:

#### Пример 2 <a href="#primer-2" id="primer-2"></a>

```java
import java.rmi.RemoteException;
public class Test {

   public void withdraw(double amount) throws RemoteException, 
      InsufficientFundsException {
      // Реализация метода
   }
   // Остаток определения класса
}
```

### Блок finally <a href="#blok-finally" id="blok-finally"></a>

В Java finally следует за блоком try либо блоком catch. Блок finally в коде выполняется всегда независимо от наличия исключения.

Использование блока finally позволяет запустить какой-либо оператор, предназначенный для очистки, не зависимо от того, что происходит в защищенном коде.

Блок finally в Java появляется по окончании блоков catch, его синтаксис выглядит следующим образом:

#### Синтаксис <a href="#sintaksis" id="sintaksis"></a>

```java
try {
   // Защищенный код
}catch(ИсключениеТип1 e1) {
   // Блок catch
}catch(ИсключениеТип2 e2) {
   // Блок catch
}catch(ИсключениеТип3 e3) {
   // Блок catch
}finally {
   // Блок finally всегда выполняется.
}
```

#### Пример <a href="#primer" id="primer"></a>

```java
public class Test {

   public static void main(String args[]) {
      int array[] = new int[2];
      try {
         System.out.println("Доступ к третьему элементу:" + array[3]);
      }catch(ArrayIndexOutOfBoundsException e) {
         System.out.println("Исключение:" + e);
      }finally {
         array[0] = 6;
         System.out.println("Значение первого элемента: " + array[0]);
         System.out.println("Оператор finally выполнен.");
      }
   }
}
```

Вследствие этого будет получен следующий результат:

```
Исключение:java.lang.ArrayIndexOutOfBoundsException: 3
Значение первого элемента: 6
Оператор finally выполнен.
```

Следует помнить, что:

* Выражение catch не может существовать без оператора try.
* При наличии блока try/catch, выражение finally не является обязательным.
* Блок try не может существовать при отсутствии выражения catch либо выражения finally.
* Существование какого-либо кода в промежутке между блоками try, catch, finally является невозможным.

### Конструкция try-with-resources <a href="#konstrukciya-try-with-resources" id="konstrukciya-try-with-resources"></a>

В норме, при использовании различных видов ресурсов, таких как потоки, соединения и др., нам предстоит закрыть их непосредственно при использовании блока finally. В программе, представленной ниже, нами производится считывание данных из файла при использовании FileReader, после чего он закрывается блоком finally.

#### Пример 1 <a href="#primer-1" id="primer-1"></a>

```java
import java.io.FileReader;
import java.io.File;
import java.io.IOException;

public class Test {

   public static void main(String args[]) {
      FileReader fr = null;		
      try {
         File f = new File("file.txt");
         fr = new FileReader(f); 
         char [] array = new char[10];
         fr.read(array);   // чтение содержимого массива
         for(char c : array)
         System.out.print(c);   // вывод символов на экран, один за одним
      }catch(IOException e1) {
         e1.printStackTrace();
      }finally {
         try {
            fr.close();
         }catch(IOException e2) {		
            e2.printStackTrace();
         }
      }
   }
}
```

Конструкция try-with-resources, также именуемая как **автоматическое управление ресурсами**, представляет новый механизм обработки исключений, который был представлен в 7-ой версии Java, осуществляя автоматическое закрытие всех ресурсов, используемых в рамках блока try catch.

Чтобы воспользоваться данным оператором, вам всего лишь нужно разместить заданные ресурсы в круглых скобках, после чего созданный ресурс будет автоматически закрыт по окончании блока. Ниже представлен синтаксис конструкции try-with-resources.

#### Синтаксис <a href="#sintaksis" id="sintaksis"></a>

```java
try(FileReader fr = new FileReader("Путь к файлу")) {
   // использование ресурса
   }catch() {
      // тело catch 
   }
}
```

Программа ниже производит считывание данных в файле, используя конструкцию try-with-resources.

#### Пример 2 <a href="#primer-2" id="primer-2"></a>

```
import java.io.FileReader;
import java.io.IOException;

public class Test {

   public static void main(String args[]) {
      try(FileReader fr = new FileReader("E://Soft/NetBeans 8.2/Projects/test/test/file.txt")) {
         char [] array = new char[10];
         fr.read(array);   // чтение содержимого массива
         for(char c : array)
         System.out.print(c);   // вывод символов на экран, один за одним
      }catch(IOException e) {
         e.printStackTrace();
      }
   }
}
```

При работе с конструкцией try-with-resources следует принимать во внимание следующие нюансы:

* С целью использования конструкции try-with-resources следует реализовать интерфейс AutoCloseable, после чего соответствующий метод close() будет вызван автоматически во время выполнения.
* В конструкции try-with-resources возможно указание одного и более классов.
* При указании нескольких классов в блоке try конструкции try-with-resources, закрытие данных классов будет производиться в обратном порядке.
* За исключением внесения ресурсов в скобки, все элементы являются равными аналогично нормальному блоку try/catch в составе блока try.
* Ресурсы, внесенные в try, конкретизируются до запуска блока try.
* Ресурсы непосредственно в составе блока try указываются как окончательные.

### Создание своих собственных исключений <a href="#sozdanie-svoih-sobstvennyh-isklyucheniy" id="sozdanie-svoih-sobstvennyh-isklyucheniy"></a>

Вы можете создать свои собственные исключения в среде Java. При записи собственных классов исключений следует принимать во внимание следующие аспекты:

* Все исключения должны быть дочерними элементами Throwable.
* Если вы планируете произвести запись контролируемого исключения с автоматическим использованием за счет правила обработки или объявления, вам следует расширить класс Exception.
* Если вы хотите произвести запись исключения на этапе выполнения, вам следует расширить класс RuntimeException.

Вы можете определить собственный класс исключений, как показано ниже:

```java
class MyException extends Exception {
}
```

Вам лишь необходимо расширить предопределенный класс Exception с целью создания собственного исключения. Данная категория относится к контролируемым исключениям. Следующий класс InsufficientFundsException исключительных ситуаций, определяемых пользователем, расширяет класс Exception, делая его контролируемым исключением. Класс исключений, подобно всем остальным классам, содержит используемые области и методы.

#### Пример <a href="#primer" id="primer"></a>

```java
// Название файла InsufficientFundsException.java
import java.io.*;

public class InsufficientFundsException extends Exception {
   private double amount;
   
   public InsufficientFundsException(double amount) {
      this.amount = amount;
   }
   
   public double getAmount() {
      return amount;
   }
}
```

С целью демонстрации наших исключений, определяемых пользователем, следующий класс Checking содержит метод withdraw(), генерирующий InsufficientFundsException.

```java
// Название файла Checking.java
import java.io.*;

public class Checking {
   private int number;
   private double balance;
   
   public Checking(int number) {
      this.number = number;
   }
   
   public void deposit(double amount) {
      balance += amount;
   }
   
   public void withdraw(double amount) throws InsufficientFundsException {
      if(amount <= balance) {
         balance -= amount;
      }else {
         double needs = amount - balance;
         throw new InsufficientFundsException(needs);
      }
   }
   
   public double getBalance() {
      return balance;
   }
   
   public int getNumber() {
      return number;
   }
}
```

