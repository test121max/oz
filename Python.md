## Python <!-- {docsify-ignore} -->

### Блиц

Сложность: **низкая**

<!--Автор: @AlexanderS -->

#### Вопрос:

Что может являться ключом словаря?

#### Ответ:

Только объекты, поддерживающие хеширование - неизменяемые;\
Не получится использовать как ключи - списки, другие словари, и т.п.

#### Дополнительные вопросы:

Q: *Где быстрее выполняется поиск элемента - в списках (list) или множестве (set)?*

A: Во множествах

Q: *Где быстрее выполняется поиск элемента - в списках (list) или словарях (dict)?*

A: В словаре

______________________________________________________________________

### Работа со строками: интерполяция строк

Сложность: **низкая**

<!--Автор: @AlexanderS @rogordeev -->

#### Вопрос:

Как собрать строку? лучше несколько решений сразу

#### Ответ:

- % operator: `'Hello, %s' % ("Ozon")`
- format `'Hello, {}'.format("Ozon")`
- f-строки `f'Hello, {"Ozon"}'`

______________________________________________________________________

### Работа со строками: символ в строке

Сложность: **низкая**

<!--Автор: @rogordeev -->

#### Вопрос:

Что выведут строки

```py
"1234567890"[6] = 7
"1234567890"[6] == 7
```

#### Ответ:

Ошибку в первом случае - потому что строка неизменяемый объект; во втором случае False

```py
>>> "1234567890"[6] = 7
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: 'str' object does not support item assignment
>>> "1234567890"[6] == 7
False
```

#### Дополнительные вопросы:

Q: *Как получить True?*

A:

```py
"1234567890"[6] == '7'
```

______________________________________________________________________

### Словари: квадраты чисел от 0 до 9

Сложность: **низкая**

<!--Автор: @AlexanderS -->

#### Вопрос:

Посчитать однострочником квадраты чисел от 0 до 9\
Как это сделать в pythonic way?

#### Ответ:

Использовать list comprehension

```py
[i*i for i in range(10)]

>>> [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```

#### Дополнительные вопросы:

Q: *Что можете рассказать про range(10)? Будет ли он хорошо работать, если там большое число?*

A: Будет, в Python 3.\* он работает как генератор, до Python 3.\* для этого предназначался `xrange()`

______________________________________________________________________

### Словари: `zip`

Сложность: **средняя**

<!--Автор: @rogordeev -->

#### Вопрос:

Представить результат команды zip
Что выведет выражение

```py
dict(zip(('a','b','c','d','e'),(1,2,3,4,5)))
```

#### Ответ:

```py
{'a': 1, 'b': 2, 'c': 3, 'd': 4, 'e': 5}
```

#### Дополнительные вопросы:

Q: *Зачем в нем нужен dict()?*

A: Без него мы увидим объект, возвращаемый zip

Q: *Что будет, если длины кортежей не равны?*

A: Ошибки не будет, zip возьмет одинаковое число элементов из обоих кортежей

```py
>>> dict(zip(('a','b','c','d','e'),(1,2)))
{'a': 1, 'b': 2}
```

______________________________________________________________________

### Словари: `sorted` и list comprehension

Сложность: **низкая**

<!--Автор: @AlexanderS @rogordeev -->

#### Вопрос:

Что выведет выражение

```py
D = {'a': 1, 'b': 2, 'c': 3, 'd': 4, 'e': 5}
sorted([D[s] for s in D])
```

#### Ответ:

```py
[1, 2, 3, 4, 5]
```

#### Дополнительные вопросы:

Q: *Что такое sorted?*

A: В питоне Batteries included - это встроенная функция

______________________________________________________________________

### Словари: Условие в list comprehension

Сложность: **низкая**

<!--Автор: @AlexanderS @rogordeev -->

#### Вопрос:

Что выведет выражение

```py
D = {'a': 1, 'b': 2, 'c': 3, 'd': 4, 'e': 5}
[i for i in range(10) if i in D.values()]
```

#### Ответ:

```py
[1, 2, 3, 4, 5]
```

______________________________________________________________________

### Декораторы: `@staticmethod`

Сложность: **низкая**

<!--Автор: @rogordeev -->

#### Вопрос:

Что такое и зачем нужен `@staticmethod`?

#### Ответ:

Это декоратор для методов класса, которые не меняют его состояние/данные

#### Дополнительные вопросы:

Q: *Зачем это надо?*

A: Функцию не нужно импортировать отдельно; легче читать и понимать, что функция относится к классу

______________________________________________________________________

### ООП: сравнение инстансов №1

Сложность: **средняя**

<!--Автор: @rogordeev -->

#### Вопрос:

Что будет результатом?

```py
class C:
    pass
 
a = C()
b = C()

a == b
???
```

#### Ответ:

Будет `False`, это разные инстансы

#### Дополнительные вопросы:

Q: *А если так?*

```py
a = b = C()

a == b
???
```

A: Тогда `True`, они указывают на один и тот же объект

______________________________________________________________________

### ООП: сравнение инстансов №2

Сложность: **средняя**

<!--Автор: @rogordeev -->

#### Вопрос:

Как сравнить два экземпляра класса

#### Ответ:

Нужно описать магический метод `__eq__`
Вообще методов для сравнения много - `__lt__, __le__` и так далее

#### Дополнительные вопросы:

Q: *Пример кода?*

A:

```py
class MyComparableClass:

  def __init__(self, val):
     self.val = val

  def __eq__(self, other):
     return self.val == other.val
```

______________________________________________________________________

### Магические методы: `__str__`

Сложность: **сложная**

<!--Автор: @rogordeev -->

#### Вопрос:

Для чего используется `__str__`?

#### Ответ:

Отладка/просто строковое представление инстанса

```py
class IPAddress:
    def __init__(self, ip):
        self.ip = ip

    def __str__(self):
       return f"IPAddress: {self.ip}"
```

#### Дополнительные вопросы:

Q: *Что такое `__repr__()`?*

A: Ещё одно строковое представление, отображается при добавлении в контейнеры (например в списки)

Q: *В чем разница?*

A: `__str__()` используется, например, при `print()` или `str()` - оно должна быть readable, `__repr__()` чаще используют для отладки;

______________________________________________________________________

### Списки: list * 3

Сложность: **средняя**

<!--Автор: @AlexanderS -->

#### Вопрос:

Представить результаты выражений

```py
x = [[1,2,3,4]] * 3
```

что лежит в x?

#### Ответ:

```py
[[1, 2, 3, 4], [1, 2, 3, 4], [1, 2, 3, 4]]
```

там будет список исходных массивов

#### Дополнительные вопросы:

Q: *Что изменится при присвоении?*

```py
x[0][3] = 10
```

A: "Python has names" - у нас не три разных коробочки с числами

```py
[[1, 2, 3, 10], [1, 2, 3, 10], [1, 2, 3, 10]]

```

NB вот еще пример с инстансом, показывающий, как это работает

```py
class C:
    pass

a = C()
[a] * 3
[<__main__.C object at 0x110060670>, <__main__.C object at 0x110060670>, <__main__.C object at 0x110060670>]
```

______________________________________________________________________

### `None`

Сложность: **низкая**

<!--Автор: @AlexanderS -->

#### Вопрос:

Что вернет функция без `return`?

```py
def pprinter(string):
    print(string)
    
```

#### Ответ:

Она вернет `None`

```py
>>> a = pprinter("Hi")
Hi
>>> a
>>> type(a)
<class 'NoneType'>
```

#### Дополнительные вопросы:

Q: *Как проверить, что результат это `None`?*

A: Для этого есть ключевое слово `is`\
`if pprinter("Hello, Ozon!") is None: `

Q: *Какие реальные случаи применения могут быть?*

A: Неуспешное подключение к БД, например - может вернуть `None`

______________________________________________________________________

### `*args, **kwargs`

Сложность: **низкая**

<!--Автор: @AlexanderS @rogordeev -->

#### Вопрос:

Представить результаты выражений\\

```py
def func(val, *args, **kwargs):
    print(val)
    print(args)
    print(kwargs)
    

func("Hi", "Ozon", {"a":1, "b":2}, pi=3.14, e=2.71)
```

#### Ответ:

Функция ожидает первый аргумент, остальные упаковываются

- неименованные в кортеж `args`
- именованные в словарь `kwargs`

```py
Hi
('Ozon', {'a': 1, 'b': 2})
{'pi': 3.14, 'e': 2.71}
```

#### Дополнительные вопросы:

Q: *И зачем это может быть нужно?*

A: Если мы предоставляем библиотечную функцию - и не знаем, кто ее будет использовать; помогает в цепочках вызовов функций.

______________________________________________________________________

### Аргументы по-умолчанию

Сложность: **низкая**

<!--Автор: @rogordeev -->

#### Вопрос:

Написать функцию, которая печататет строку `<Name> на собеседовании в <company>`, по-умолчанию считаем, что компания это Ozon, но можно и свою компанию создать.

#### Ответ:

```py
def func(name, company='Ozon'):
    print(name, 'на собеседовании в', company)

func("Guido", "Microsoft")

Guido на собеседовании в Microsoft
```

______________________________________________________________________

### list append

Сложность: **низкая**

<!--Автор: @AlexanderS -->

#### Вопрос:

Представить результаты выражений

```py
def append_list(list=[]):
    list.append(len(list))
    return list

append_list(['a','b'])
```

#### Ответ:

```py
['a', 'b', 2]
```

#### Дополнительные вопросы:

Q: *`append_list()`*

A: вернет `[0]`

______________________________________________________________________

### list append №2

Сложность: **низкая**

<!--Автор: @AlexanderS -->

#### Вопрос:

Представить результаты выражений

```py
def append_list(val, list=[]):
    list.append(val)
    return list

list1 = append_list(10)
list2 = append_list(123,[])
list3 = append_list('a')
```

#### Ответ:

```py
list1, list2, list3
[10, 'a'], [123], [10, 'a']
```

Во втором случае передается объект списка, изменяет он, в первом и третьем изменяется тот, что был создан по-умолчанию

______________________________________________________________________

### `False or True`

Сложность: **средняя**

<!--Автор: @AlexanderS -->

#### Вопрос:

Представить результаты выражений

```py
>>> False and True
>>> 7 < 7 or True
>>> not 2 == 2
```

#### Ответ:

```py
>>> False and True
False
>>> 7 < 7 or True
True
>>> not 2 == 2
False
```

______________________________________________________________________

### `if __name__ == "__main__"`

Сложность: **низкая**

<!--Автор: @rogordeev -->

#### Вопрос:

Почему в скриптах есть это выражение
`if __name__ == "__main__"`

#### Ответ:

Это условие, которое проверит, запущен ли файл напрямую или нет

#### Дополнительные вопросы:

Q: *Зачем это проверять?*

A: чтобы не выполнять какой-то код при импорте этого файла как модуля. Часто после этой проверки выполняются отладочные принты или что-то подобное.

______________________________________________________________________

### Virtual environments

Сложность: **низкая**

<!--Автор: @rogordeev -->

#### Вопрос:

Что из себя представляет python virtual environment?

#### Ответ:

На диске это папка, в ней есть некоторая структура каталогов

#### Дополнительные вопросы:

Q: *Что еще внутри может быть?*

A: `pip` - пакетный менеджер, еще `easy_install`

Q: *Зачем это?*

A:

- избежать конфликты версий библиотек для разных проектов
- держать несколько версий Python с разными библиотеками
- изолировать окружение разработчика от хоста

Q: *Есть же докер/виртуалка?*

A: venv это инструмент инкапсулирования только зависимостей, используйте его для этого, если ничего больше не нужно;

______________________________________________________________________

### Типы пакетов - .whl

Сложность: **высокая**

<!--Автор: @rogordeev -->

#### Вопрос:

Рассказать про whl пакетирование, и то, какие задачи оно решает.
В 2012 году вышел PEP 427, наверное начиная с этого времени Wheel это стандарт пакетирования в Python
Когда для одного проекта собираютcя разные/одинаковые whl?

#### Ответ:

platform wheel:

- сборка может включать бинарные файлы - например адаптер psycopg2 - тогда под каждую платформу будет свой пакет

```
psycopg2-2.8.6-cp27-cp27m-win32.whl
psycopg2-2.8.6-cp27-cp27m-win_amd64.whl
```

- сборка может зависеть так же от версии Python / abi

```
psycopg2-2.8.6-cp27-cp27m-win_amd64.whl
psycopg2-2.8.6-cp34-cp34m-win_amd64.whl
```

- но при этом Wheel не содержит .pyc файлов, если код совместим с Python 2 и 3 пакет может быть один и тот же - universal wheel
- может быть так же пакет, который зависит от версии Python и только - pure-Python wheel

#### Дополнительные вопросы:

Q: *А еще есть .egg?*

A: Да, но это более старый формат, наверное его лучше избегать в современном окружении

______________________________________________________________________

### setuptools/distutils

Сложность: **высокая**

<!--Автор: @rogordeev -->

#### Вопрос:

Показать знакомство с фундаментом сборки и дистрибуции пакетов.
Что такое Setuptools в двух словах?

#### Ответ:

Пакет для сборки и дистрибуции других пакетов

#### Дополнительные вопросы:

Q: *Какое отношение имеет к distutils?*

A: Можно сказать, что Setuptools это удобная надстройка над более старым distutils

Q: *Внутри проекта, который собирается Setuptools есть setup.cfg - зачем он?*

A: Setuptools предлагает перейти от формата с setup.py к декларативной конфигурации

Q: *В setup что может быть описано?*

A:

- в нем есть метаданные - имя, версия пакета
- описаны зависимости
- могут быть описаны entry_points - скрипты, которые автоматически создадутся после установки

```ini
[options.entry_points]
console_scripts =
    main = mypkg:some_func

```

- могут быть data files (конфиги, например)

______________________________________________________________________

### Генератор - пример и код

Сложность: **средняя**

<!--Автор: @rogordeev -->

#### Вопрос:

Что такое генератор? Пример кода напишите, пожалуйста.

#### Ответ:

Это функция, ее можно приостановить и продолжить ее выполнение, внутри нее `yield` вместо `return`.
Нужна она как lazy итератор, чтобы более эффективно использовать память.
Использовать - для генерации бесконечных последовательностей, итерации по большим данным etc.

```py
def gen(n):
    for i in range(n):
        yield i
```

#### Дополнительные вопросы:

Q: *Что вернет `next(gen)`?*

A: Следующий элемент в списке

Q: *Что будет, когда элементы закончатся?*

A: Вернется exception `StopIteration`

Q: *А достать N-th элемент по индексу можно?*

A: Нет

______________________________________________________________________

### Что такое декораторы?

Сложность: **средняя**

<!--Автор: @AlexanderS @rogordeev -->

#### Вопрос:

Что принимает в параметрах и что возвращает декоратор?

#### Ответ:

Декоратор примет параметром декорируемую функцию, вернет тоже функцию (может исходную или задекорированную).

#### Дополнительные вопросы:

Q: *Примеры, зачем используется?*

A:

- логирование
- проверка коннекта к бд
- валидация параметров Django @require_http_methods(\["GET", "POST"\])
- валидация состояния Flask @login_required
- регистрация эндпоинта Flask @app.route('/secret_page')

______________________________________________________________________

### Что такое contextmanager?

Сложность: **средняя**

<!--Автор: @rogordeev -->

#### Вопрос:

Что такое и зачем нужны context managers? нужен пример, и описание, как работает выход из блока с ним.

#### Ответ:

Это хорошо знакомая конструкция

```py
with open('1.txt', 'w') as file:
    file.write("Hello, Ozon!")
```

после завершения блока? - файл "закроется" в любом случае, даже если будет внутри Exception

______________________________________________________________________

### Написать contextmanager

Сложность: **сложная**

<!--Автор: @rogordeev -->

#### Вопрос:

Напишите/расскажите как написать свой contextmanager

#### Ответ:

Достаточно реализовать магические методы `__enter__, __exit__, __open__`

```py
class MyManager:
    def __enter__(self):
        pass   
 
	def __exit__(self, type, value, traceback):
        pass

with MyManager as mgr:
    pass
```

есть вариант с библиотекой contextlib

```py
from contextlib import contextmanager

@contextmanager
def tag(name):
    print(f'<{name}>')
    yield
    print(f'<{name}>')

with tag('h1'):
	print('Hello, Ozon!')
```

______________________________________________________________________

### Конструкция try/catch

Сложность: **низкая**

<!--Автор: @rogordeev -->

#### Вопрос:

Представить результат выполнения кода
Описать, как работает эта конструкция.

```py
try:
    n = 1 + 'A'
except:
    n = 1
finally:
    print('H, Ozon')
```

#### Ответ:

Напечатается 'Hi, Ozon', в n будет 1
`finally` выполнится в любом случае, блок except если что-то пойдет не так в `try`

#### Дополнительные вопросы:

Q: *Если мы хотим выполнить обработку исключения в `except`?*

A: То есть мы хотим выполнить его только при определенной ошибке? надо написать синтаксис:

```py
except TypeError:
    n = 1
```

______________________________________________________________________

### Python 3.6+: аннотации типов

Сложность: **сложная**

<!--Автор: @rogordeev -->

#### Вопрос:

У нас новый питон, в нем можно писать аннотации типов, но они не избавляют нас от ошибок.

Что будет в результате выполнения?

```py
def sum(a: int, b: int) -> int:
    return a+b
    
sum("A", 1)
```

#### Ответ:

Упадет, уже внутри функции - аннотации не проверяют типы. Python - язык с динамической типизацией. Но это нужно - чтобы статический анализатор мог найти ошибку, например

______________________________________________________________________

### Python 3.6+: строки в Python3

Сложность: **средняя**

<!--Автор: @rogordeev -->

#### Вопрос:

Рассказать про отличия в строках между 2 и 3 версиями

#### Ответ:

В Python 3 есть строковый тип str - он хранит Unicode, \*есть также байтовые типы - bytes, bytearray;
в Python 2 str хранит строки в ASCII и вообще байтовые строки, \*есть unicode, и есть bytearray

______________________________________________________________________

### Сommon libs: файлы в папке

Сложность: **средняя**

<!--Автор: @rogordeev -->

#### Вопрос:

Как собрать файлы в папке (рекурсивно)

#### Ответ:

Нужна библиотека glob

```py
import glob

glob.glob('test[0-9].txt', recursive=True)
```

______________________________________________________________________

### Common libs: pickle

Сложность: **средняя**

<!--Автор: @rogordeev -->

#### Вопрос:

Что такое pickle? код можете написать?

#### Ответ:

Это модуль для сериализации и десереализации объектов. Например, чтобы передать объект или сохранить его между запусками.

```py
import pickle

d = {'a': 1}

with open('file.p', 'wb') as f:
    pickle.dump(d, f)

with open('file.p', 'rb') as f:
    loaded_d = pickle.load(f)

print(loaded_d)
```

______________________________________________________________________

### pytest: фикстуры

Сложность: **средняя**

<!--Автор: @AlexanderS @rogordeev -->

#### Вопрос:

Рассказать, что такое `pseudo_lock()` в файле test_ozon.py:

```py
import os, pytest


@pytest.fixture
def pseudo_lock():
    filename = "file.lock"
    with open(filename, "w+") as f:
        f.write("tests are going on")
        yield
    os.remove(filename)


def test_open_base_url(pseudo_lock):
    print("Hello, tests!")
    assert True == True
```

#### Ответ:

Это фикстура (fixture) - механизм, который предлагает pytest для инициализации тестов, параметризации запуска и очистки окружения после них (в терминах arrange/act/assert/cleanup это arrange и cleanup). В предложенном коде создастся файл и управление вернется в тесты, после окончания тестов выполнится файл закроется и удалится.

#### Дополнительные вопросы:

Q: *как запустить тест?*

A: для запуска достаточно выполнить команду `pytest` в директории с файлом или в родительских. Pytest находит файлы с префиксом test\_\*.   Можно также указать файл как аргумент - `pytest test_ozon.py` или запустить, вызвав модуль pytest `python -m pytest test_ozon.py`

Q: *в чем разница между созданием файла в тесте и в фикстуре?*

A: ошибка инициализации (например у нас файл уже существует) в фикстуре вернет `ERROR test_ozon.py::...`, если это произойдет в тесте - тест будет помечен как FAIL.

______________________________________________________________________
