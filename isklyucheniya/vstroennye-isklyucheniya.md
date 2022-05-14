# Встроенные исключения

Java определяет несколько классов исключений внутри стандартного пакета **java.lang**.

Наиболее общие из этих исключений являются подклассами стандартного типа <mark style="color:orange;">**RuntimeException**</mark>. Поскольку **java.lang** неявно импортируется во все java-программы, то большинство исключений, полученных из <mark style="color:orange;">**RuntimeException**</mark>, автоматические.

Java определяет несколько других типов исключений, которые относятся к его различным библиотекам класса. Ниже приведен список неконтролируемых исключений на этапе выполнения (Unchecked RuntimeException).

#### <mark style="color:green;">Unchecked RuntimeException</mark>

| №  | Исключение и описание                                                                                                                        |
| -- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| 1  | <p><strong>java.lang.ArithmeticException</strong><br>Арифметическая ошибка, например, деление на ноль.</p>                                   |
| 2  | <p><strong>java.lang.ArrayIndexOutOfBoundsException</strong><br>Индекс массива выходит за пределы.</p>                                       |
| 3  | <p><strong>java.lang.ArrayStoreException</strong><br>Присвоение элементу массива несовместимого типа.</p>                                    |
| 4  | <p><strong>java.lang.ClassCastException</strong><br>Недопустимое приведение типов.</p>                                                       |
| 5  | <p><strong>java.lang.IllegalArgumentException</strong><br>Недопустимый аргумент, используемый для вызова метода.</p>                         |
| 6  | <p><strong>java.lang.IllegalMonitorStateException</strong><br>Недопустимая работа монитора, например, ожидание разблокированного потока.</p> |
| 7  | <p><strong>java.lang.IllegalStateException</strong><br>Окружающая обстановка или приложение находится в неправильном состоянии.</p>          |
| 8  | <p><strong>java.lang.IllegalThreadStateException</strong><br>Запрошенная операция несовместима с текущим состоянием потока.</p>              |
| 9  | <p><strong>java.lang.IndexOutOfBoundsException</strong><br>Некоторый тип индекса находится за пределом.</p>                                  |
| 10 | <p><strong>java.lang.NegativeArraySizeException</strong><br>Массив создан с отрицательным размером.</p>                                      |
| 11 | <p><strong>java.lang.NullPointerException</strong><br>Недопустимое использование нулевой ссылки.</p>                                         |
| 12 | <p><strong>java.lang.NumberFormatException</strong><br>Неверное преобразование строки в числовой формат.</p>                                 |
| 13 | <p><strong>java.lang.SecurityException</strong><br>Попытка нарушить безопасность.</p>                                                        |
| 14 | <p><strong>java.lang.StringIndexOutOfBounds</strong><br>Попытка индексирования за пределами строки.</p>                                      |
| 15 | <p><strong>java.lang.UnsupportedOperationException</strong><br>Была обнаружена неподдерживаемая операция.</p>                                |

Ниже приведен список контролируемых исключений (Checked Exceptions) в Java, определенных в java.lang.

#### <mark style="color:green;">Checked Exceptions</mark>

| № | Исключение и описание                                                                                                                 |
| - | ------------------------------------------------------------------------------------------------------------------------------------- |
| 1 | <p><strong>java.lang.ClassNotFoundException</strong><br>Класс не найден.</p>                                                          |
| 2 | <p><strong>java.lang.CloneNotSupportedException</strong><br>Попытка клонировать объект, который не реализует Cloneable интерфейс.</p> |
| 3 | <p><strong>java.lang.IllegalAccessException</strong><br>Запрещен доступ к классу.</p>                                                 |
| 4 | <p><strong>java.lang.InstantiationException</strong><br>Попытка создать объект абстрактного класса или интерфейса.</p>                |
| 5 | <p><strong>java.lang.InterruptedException</strong><br>Один поток был прерван другим потоком.</p>                                      |
| 6 | <p><strong>java.lang.NoSuchFieldException</strong><br>Запрошенное поле не существует.</p>                                             |
| 7 | <p><strong>java.lang.NoSuchMethodException</strong><br>Запрошенный метод не существует.</p>                                           |
