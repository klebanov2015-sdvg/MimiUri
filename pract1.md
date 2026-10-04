## Безумно можно кодить

1. Знакомство с языком
```
1. Запишите число 42 с помощью 10 различных способов, чем разнообразнее, тем лучше. Использовать литеральную запись, без арифметики и функций. В любом варианте должно соблюдаться == 42.

1)	42	десятичная	4×10 + 2 = 42
2)	0x2A	шестнадцатеричная	2×16 + 10 = 42
3)	0b101010	двоичная	32+8+2 = 42
4)	0o52	восьмеричная	5×8 + 2 = 42
5)	XLII	римская	(50−10)+1+1 = 42
6)	*	ASCII-код символа *	В таблице ASCII символ * имеет десятичный код 42
7)	U+002A	Кодовая позиция Unicode	U+002A — шестнадцатеричное 2A = 42 в десятичной
8)	a = 4 b = 2 print('4' + '2')
9) int a = 1456;
int b = 182;

// 2-й символ числа 1456 (индекс 1)
char c1 = a.ToString()[1]; // '4'

// 3-й символ числа 182 (индекс 2)
char c2 = b.ToString()[2]; // '2'

Console.WriteLine(c1); // 4
Console.WriteLine(c2); // 2
10)	FORTY-TWO	Английское словесное написание	Проверяется по любому словарю: forty = 40, two = 2
```
```
1.2. Есть ли ограничения на диапазон чисел в Питоне? Как насчет чисел с плавающей запятой? Какое максимальное значение вы сумели получить до переполнения?
Для int переменных ограничений по кол-ву символов числа нет, только память. В старой версии питона есть такое понятие
Для float  максимальное число = 1.7976931348623157e+308 , минимальное число = 2.2250738585072014e-308
```
```
1.3. Найдите в документации встроенную (builtin) арифметическую функцию, которая возвращает не одно, а два значения разом.
Встроенная функция, которая возвращает два значения разом, — это divmod().
divmod(7, 3) возвращает (2, 1)
```
```
1.4. C приведенным ниже циклом что-то не так. Как это исправить?
from decimal import Decimal
a = Decimal("10")
summator = 0
while a != 0:
    a -= Decimal("0.1")
    summator +=1
print(summator)
```
```
1.5  почему зависает программа?
z = 1
z <<= 40
2 ** z
Итог: программа не «зависла» в смысле бага — она выполняет корректную, но физически неподъёмную операцию. Это прямое следствие того, что z <<= 40 даёт ~10¹², а 2 ** z — это число с ~330 миллиардами цифр.
```
```
1.6  Почему этот код зацикливается?
i = 0
while i < 10:
    print(i)
    ++i
Ответ: потому что в яп питоне нет префиксного и постфиксного инкремента. программа пытается к 0 прибавить 0
```
```
1.7 Что за странное выражение и странный результат?
(True * 2 + False) * -True
Ответ: -2
1	True * 2	2	True как 1 → 1 × 2 = 2
2	2 + False	2	False как 0 → 2 + 0 = 2
3	(2) * -True	-2	-True = −1 → 2 × (−1) = −2
```
```
1.8 В Питоне можно использовать цепочки операций сравнения. Рассмотрите следующие примеры и попробуйте объяснить код:
x = 5
1 < x < 10
True
x = 5
1 < (x < 10)
False
Ответ: потому что в первом примере происходит последовательное сравнение, получается true and true,  а во втором примере сначала в скобках true = 1, вне скобок тоже true = 1 после чего идет сравнение 1<1 = false
```
2. Сообщения об ошибках
```
2.1
SyntaxError: invalid syntax - в c# если после значения переменной не поставить ";"/ в python - elsee:	Опечатка в ключевом слове else
```
```
2.2
SyntaxError: cannot assign to literal - 10 = x	Перепутаны местами: переменная должна быть слева, значение — справа
```
```
2.3. NameError: name ... is not defined - Опечатка в имени	pritn("hi")	Написано pritn, а функция называется print
```
```
2.4 SyntaxError: unterminated string literal - Забыта закрывающая кавычка	s = "hello	Открыта ", но нет закрывающей "
```
```
2.5 TypeError: unsupported operand type(s) for ... - Смешивание типов в арифметике	5 + "10"	Нельзя сложить число и строку без явного преобразования
```
```
2.6 IndentationError: expected an indented block -
if x > 0:
print("positive")	Нет отступа после if
```
```
2.7 IndentationError: unindent does not match any outer indentation level - «уменьшение отступа не совпадает ни с одним внешним уровнем». Причина: строка имеет отступ, не соответствующий ни одному из существующих уровней вложенности. Решение: выровнять отступы внутри блока, не смешивать пробелы и табы, использовать 4 пробела на уровень.
```
```
2.8 ValueError: math domain error - Корень из отрицательного числа	math.sqrt(-5)	Квадратный корень из отрицательного числа не является вещественным числом
```
```
2.9 OverflowError: math range error - Ошибка OverflowError: math range error возникает, когда результат математической функции из модуля math выходит за пределы диапазона, который может представить число с плавающей запятой (тип float). Для типа int предел числа определяется кол-вом оперативной памяти, в которое оно будет записано
```
3. Арифметика
```
3.1 Умножение на 12. Используйте 4 сложения.
    def multiply_by_12(x):
    x2 = x + x        # 1-е сложение: x2 = 2x
    x4 = x2 + x2      # 2-е сложение: x4 = 4x
    x8 = x4 + x4      # 3-е сложение: x8 = 8x
    result = x8 + x4  # 4-е сложение: result = 12x
    return result
```
```
3.2 Умножение на 16. Используйте 4 сложения.
def multiply_by_16(x):
    x2 = x + x        # 1-е сложение: x2 = 2x
    x4 = x2 + x2      # 2-е сложение: x4 = 4x
    x8 = x4 + x4      # 3-е сложение: x8 = 8x
    x16 = x8 + x8     # 4-е сложение: x16 = 16x
    return x16
```
```
3.3 Умножение на 15. Используйте 3 сложения и 2 вычитания.
def multiply_by_15(x):
    x2  = x + x          # 1 сложение: 2x
    x4  = x2 + x2        # 2 сложение: 4x
    x8  = x4 + x4        # 3 сложение: 8x
    x16 = x8 + x8        # 4 сложение: 16x
    result = x16 - x     # 1 вычитание: 16x - x = 15x
    return result        # Проверка: при x = 5: 2x = 10, 4x = 20, 8x = 40, 16x = 80, 80 − 5 = 75 = 15 × 5
```
```
3.4 Добавьте к naive_mul автоматическое тестирование на случайных данных. Сравнивайте с встроенным умножением, используя конструкцию assert.
using System;
using System.Diagnostics;

class Program
{
    static int NaiveMul(int x, int y)
    {
        int r = 0;
        for (int i = 0; i < y; i++)
        {
            r = r + x;
        }
        return r;
    }

    static void Main()
    {
        Random rand = new Random();

        for (int t = 0; t < 1000; t++)
        {
             int x = rand.Next(0, 101);   // 0..100
             int y = rand.Next(0, 101);   // 0..100
          
             int expected = x * y;
             int actual = NaiveMul(x, y);

             if (actual != expected)
             {
                 throw new Exception($"Ошибка: {x} * {y} = {expected}, получено {actual}");
             }
         
        }

        Console.WriteLine("Все тесты пройдены");
    }
```
```
3.5 Реализуйте функцию fast_mul в соответствии с алгоритмом двоичного умножения в столбик (без рекурсии!). Добавьте автоматическое тестирование, как в случае с naive_mul.
using System;

class Program
{
    static int NaiveMul(int x, int y)
    {
        int r = 0;
        for (int i = 0; i < y; i++)
        {
            r = r + x;
        }
        return r;
    }

    static int FastMul(int x, int y)
    {
        int result = 0;
        while (y > 0)
        {
            if ((y & 1) == 1)      // если младший бит y равен 1 — проверка младшего бита. Побитовое И с 1 даёт 1, если число нечётное.
            {
                result = result + x;
            }
            x = x + x;             // x = x * 2 (сдвиг влево) — удвоение, эквивалент сдвига влево. Можно также писать x <<= 1, но x + x ближе к теме «умножение через сложение».
            y = y >> 1;            // y = y / 2 (сдвиг вправо)
        }
        return result;
    }

    static void Main()
    {
        Random rand = new Random();

        // Тестирование naive_mul
        for (int t = 0; t < 1000; t++)
        {
            int x = rand.Next(0, 101);
            int y = rand.Next(0, 101);

            int expected = x * y;
            int actual = NaiveMul(x, y);

            if (actual != expected)
            {
                throw new Exception($"[naive_mul] Ошибка: {x} * {y} = {expected}, получено {actual}");
            }
        }
        Console.WriteLine("naive_mul: все тесты пройдены");

        // Тестирование fast_mul
        for (int t = 0; t < 1000; t++)
        {
            int x = rand.Next(0, 101);
            int y = rand.Next(0, 101);

            int expected = x * y;
            int actual = FastMul(x, y);

            if (actual != expected)
            {
                throw new Exception($"[fast_mul] Ошибка: {x} * {y} = {expected}, получено {actual}");
            }
        }
        Console.WriteLine("fast_mul: все тесты пройдены");
    }
}
```
```
3.6 Реализуйте аналогичную функцию fast_pow для возведения в степень. Решение необходимо получить только с помощью небольших модификаций предыдущего решения.
using System;

class Program
{
    static int NaiveMul(int x, int y)
    {
        int r = 0;
        for (int i = 0; i < y; i++)
        {
            r = r + x;
        }
        return r;
    }

    static int FastMul(int x, int y)
    {
        int result = 0;
        while (y > 0)
        {
            if ((y & 1) == 1)
            {
                result = result + x;
            }
            x = x + x;
            y = y >> 1;
        }
        return result;
    }

    static int FastPow(int x, int y)
    {
        int result = 1;
        while (y > 0)
        {
            if ((y & 1) == 1)
            {
                result = result * x;
            }
            x = x * x;
            y = y >> 1;
        }
        return result;
    }

    static void Main()
    {
        Random rand = new Random();

        // Тестирование naive_mul
        for (int t = 0; t < 1000; t++)
        {
            int x = rand.Next(0, 101);
            int y = rand.Next(0, 101);
            int expected = x * y;
            int actual = NaiveMul(x, y);
            if (actual != expected)
                throw new Exception($"[naive_mul] Ошибка: {x} * {y} = {expected}, получено {actual}");
        }
        Console.WriteLine("naive_mul: все тесты пройдены");

        // Тестирование fast_mul
        for (int t = 0; t < 1000; t++)
        {
            int x = rand.Next(0, 101);
            int y = rand.Next(0, 101);
            int expected = x * y;
            int actual = FastMul(x, y);
            if (actual != expected)
                throw new Exception($"[fast_mul] Ошибка: {x} * {y} = {expected}, получено {actual}");
        }
        Console.WriteLine("fast_mul: все тесты пройдены");

        // Тестирование fast_pow
        for (int t = 0; t < 1000; t++)
        {
            int x = rand.Next(0, 6);    // основание 0..5
            int y = rand.Next(0, 8);    // степень 0..7 (чтобы не было переполнения int)
            int expected = (int)Math.Pow(x, y);
            int actual = FastPow(x, y);
            if (actual != expected)
                throw new Exception($"[fast_pow] Ошибка: {x} ^ {y} = {expected}, получено {actual}");
        }
        Console.WriteLine("fast_pow: все тесты пройдены");
    }
}

```
4. Пиксельные шейдеры
```
4.1 Изобразите свою версию знаменитого «Черного квадрата».
import math
import tkinter as tk


def draw(shader, width, height):
    image = bytearray((0, 0, 0) * width * height)
    for y in range(height):
        for x in range(width):
            pos = (width * y + x) * 3
            color = shader(x / width, y / height)
            normalized = [max(min(int(c * 255), 255), 0) for c in color]
            image[pos:pos + 3] = normalized
    header = bytes(f'P6\n{width} {height}\n255\n', 'ascii')
    return header + image


def main(shader):
    label = tk.Label()
    img = tk.PhotoImage(data=draw(shader, 256, 256)).zoom(2, 2)
    label.pack()
    label.config(image=img)
    tk.mainloop()


def shader(x, y):
    return 0, 0, 0


main(shader)
```
