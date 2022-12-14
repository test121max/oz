# Backend тестирование <!-- {docsify-ignore} -->

## Вопросы

### Из чего состоит HTTP запрос?
Сложность: **низкая**
<details>
  <summary>
    Ответ
  </summary>
    Версия HTTP, метод, URL, заголовки и опционально - тело запроса
</details>

### Какие методы HTTP вы знаете?
Сложность: **низкая**
<details>
  <summary>
    Ответ
  </summary>
    GET, POST, DELETE, PUT, PATCH, HEAD, CONNECT, OPTIONS, TRACE
</details>

### В чем разница между GET и POST?
Сложность: **низкая**
<details>
  <summary>
    Ответ
  </summary>
    Смысловая: GET для получения данных, POST для добавления/изменения данных. По стандарту, GET должен быть идемпотентен (каждый запрос GET возвращает один и тот же результат), а POST не должен - это важно для правильной работы кеширования ответов. У GET в отличии от POST нет тела запроса.
</details>

### Какие есть коды состояния в ответе сервера?
Сложность: **низкая**
<details>
  <summary>
    Ответ
  </summary>
    1хх (информационные), 2хх (успешные), 3хх (перенаправление), 4хх (ошибка на стороне клиента), 5хх (ошибка на стороне сервера).
</details>

### В чем разница http и https?
Сложность: **низкая**
<details>
  <summary>
    Ответ
  </summary>
    HTTPS обеспечивает шифрование трафика между клиентом и сервером после установки защищенного соединения. Также гарантируется подлинность сервера - с помощью сертификатов.
</details>

### Как выбирать между POST, PUT и PATCH?
Сложность: **средняя** 
<details>
  <summary>
    Ответ
  </summary>
    POST нужен для создания данных, когда клиент не знает ID, например /users/create. PUT - когда клиент сам задаёт ID, например /users/create/1. В POST и PUT передаётся целиком вся сущность. PATCH нужно использовать, когда требуется отредактировать конкретные поля сущности, например имя у пользователя.
</details>

### Что такое cookie и для чего они могут быть использованы?
Сложность: **средняя**
<details>
  <summary>
    Ответ
  </summary>
    Сookie - данные, которые хранятся в браузере пользователя. Попадают они туда по просьбе сервера (хедер Set-Cookie) и хранятся заданное количество времени. Cookie нужны, например, для авторизации и работы с сессиями. Также в Cookie можно сохранить информацию, что пользователь увидел информационное сообщение на сайте, и больше его не показывать.
</details>

### Какие знаете библиотеки библиотеки для отправки запросов на сервер?
Сложность: **средняя**
<details>
  <summary>
    Ответ
  </summary>
    py - requests
    ts - axios
    go - net/http
    Какое у них API?
</details>


### Как инвалидировать кэш?
Сложность: **высокая**
<details>
  <summary>
  Ответ
  </summary>
    Least recently used - Вытеснение давно неиспользуемых
    Most Recently Used - Наиболее недавно использовавшийся
</details>

### Какие бывают виды тестовых дублеров?
Сложность: **высокая**
<details>
  <summary>
    Ответ
  </summary>
    Dummy - Объект, который передается, но никогда не используется
    Fake - Объекты, которые имеют некоторую имплементацию, но не могут использоваться в Prod (например In memory database)
    Stubs - Предоставляет готовые объекты по запросу
    Spies - Те же Stubs, только ещё записывают информацию о количестве вызовов
    Mocks - Предоставляет ответ в зависимости от полученого запроса
</details>

### Опишите преимущества gRPC
Сложность: **высокая**
<details>
  <summary>
    Ответ
  </summary>
    Кросс-платформеный (поддержвает 11 языков)
    Бинарная сериализация данных позволяет снизить нагрузку на сеть.
    Стриминг данных
    Tracing
    Распределение нагрузки
    Health checking
</details>

### Что такое deadlock?
Сложность: **высокая**
<details>
  <summary>
    Ответ
  </summary>
    deadlock или взаимная блокировка это состояния когда несколько одновременно запущенных процесса ожидают ответа или ресурса друг от друга, тем самым не могут продолжить свою работу
</details>

### Что такое race condition?
Сложность: **высокая**
<details>
  <summary>
    Ответ
  </summary>
    Состояние гонки возникает, когда результат работы программы зависит от последовательности или времени выполнения различных процесов или тредов в программе.
</details>

### Что происходит между вводом URL в браузер и полной отрисовкой веб страницы на экране, с точки зрения клиента?
Сложность: **высокая** 
<details>
  <summary>
    Ответ
  </summary>
    DNS - Распределенная система для получения информации о доменах, чеще всего используется для получения IP адреса по имени хоста
    Маршрутизация - процесс определения маршрута данных в сетях связи
    SSL/TLS - Криптографические протоколы, обеспечивающие защищённую передачу данных между узлами в сети Интернет
    HTTP - Протокол прикладного уровня передачи данных
    HTML - язык разметки документов для просмотра веб-страниц в браузере
    CSS - формальный язык описания внешнего вида документа
    JS - обычно используется как встраиваемый язык для программного доступа к объектам приложений. Наиболее широкое применение находит в браузерах как язык сценариев для придания интерактивности веб-страницам.
</details>

### Опишите верхнеуровнево архитектуру backend с его проекта?
Сложность: **высокая** 
<details>
  <summary>
    Ответ
  </summary>
    Кандидат должен ответить на следующие вопросы:
    Как обеспечивается распределение нагрузки?
    Как происходит кэширование?
    Как происходит индексация?
    Какой подход используется SQL или NoSQL?
    Есть ли proxy?
    Как происходит обновление данных? (Long-polling / WebSocet / Server-Side Events)
    Как спроектирована система URL?
    Есть ли распределенное хранилище?
    Как устроена система сборки мусора?
    Как устроена рекомендательная система?
</details>


## Задачи

### Текущий пользователь

Сложность: **низкая**

<!--Автор: @dkolesnik-->

#### Задача:

Есть метод получения информации о текущем пользователе. Напишите тест-план ваших проверок данного метода

Request:

```
GET /user
```

Response:

```json
{
  "phone": "string",
  "name": "string",
  "email": "string",
  "birthDate": "number",
  "img": "string",
}
```

#### Ответ:

<details><summary>Решение</summary>
<p>

Ожидается, что кандидат уточнит следующие вопросы:

- Как сервер понимает - кто текущий пользователь? (авторизационный токен в заголовке)
- Какие поля обязательные в ответе? (только `phone`)

На что стоит обратить внимание в первую очередь:

- Ответ для неавторизованного пользователя
- Пользователь авторизован, заполнен только `phone`
- Пользователь авторизован, заполнены все поля
- `birthDate` отображается корректно, с корректным time zone.

Что можно проверить ещё:

- `phone` соответствует маске
- `email` соответствует маске
- в `img` лежит ссылка
- при переходе по ссылке в `img` отображается валидная картинка
- `birthDate` валидный, не в прошлом, возраст адекватный (например: 6-99 лет)
- проверить максимальную длину поля (ввести очень длинное имя 100+ символов)

</p>
</details>

### Хлебные крошки

Сложность: **средняя**

<!--Автор: @igor.lyubin-->

#### Задача:

Разработчики выставили новую ручку, которая по item_id возвращает хлебные крошки категорий для указанного товара. Например: Бытовая техника > Техника для кухни > Чайники. Напишите тест-план ваших проверок.

Request:

```
GET /item-crumbs/{item_id}
```

`item_id` - число

Response:

```json
{
  "main": [
    {
      "name": "string",
      "url": "string"
    }
  ]
}
```

Пример ответа:

```json
{
  "main": [
    {
      "name": "Электроника",
      "url": "category/elektronika-15500/"
    },
    {
      "name": "Телефоны и смарт-часы",
      "url": "category/telefony-i-smart-chasy-15501/"
    },
    {
      "name": "Смартфоны",
      "url": "category/smartfony-15502/"
    },
    {
      "name": "Смартфоны Apple",
      "url": "category/smartfony-15502/apple-26303000/"
    }
  ]
}
```

#### Ответ:

<details><summary>Решение</summary>
<p>

**Анализ**

Здесь 2 сущности, которые стоит рассмотреть: категории и товары.

Перед решением задачи кандидату следует уточнить:

- Какие бывают категории?
- Какие бывают товары?
- Сколько всего категорий, товаров, категорий первого уровня?
- Может ли товар быть в нескольких категориях?

**Бизнес тесты**

Проведенный анализ может составить тест-план:

- Важно проверить товары в категориях первого уровня (от электроники до детских товаров)
- Проверить товар, который принадлежит корневой категории
- Товар в конечной категории. Проверить вложенность (от 1 до 5-7 крошек). Можно упомянуть кейс для фронтенда - что много крошек могут не умещаться на экране
- Товар в промежуточной категории. Проверить вложенность
- Товар может принадлежать нескольким категориям. Например: `азбука` - это и `детский товар` и `книги`. В этом случае в респонсе будет еще один набор крошек.
- Может быть товар без категории? Такого кейса нет - это ошибка в приложении
- Товар может быть распродан
- Товар может быть снят с продажи
- Товар может быть из супермаркета (express)
- Товаром может быть подписка или электронный товар
- Первой крошкой может быть хайлайт
- Первой крошкой может быть бренд
- Последняя крошка может быть брендом

**Технические тесты**

- Тестирование выхода. `url` в респонсе должны быть валидными, `name` не пустое
- Вызвать метод дважды
- item_id несуществующего товара
- item_id = 0
- item_id неправильного типа
- не передали item_id

</p>
</details>

#### Дополнительные вопросы:

Q: *Какой здесь самый первый тест?*

A: Самый первый тест - самый частый сценарий: передать item_id для популярного товара (например: iphone) и проверить что вернуться крошки его категорий.

______________________________________________________________________

### Добавление товаров в корзину

Сложность: **средняя**

<!--Автор: @igor.lyubin-->

#### Задача:

Пользователь добавляет товары в корзину. На бекенде есть ручка для этого. Надо тестировать. Ваши действия?

Request:

```
POST /items
```

Body:

```json
{
  "items": [
    {
      "id": "number",
      "quantity": "number"
    }
  ],
  "userData": {
    "sessionId": "string",
    "userId": "string"
  }
}
```

#### Ответ:

<details><summary>Решение</summary>
<p>

Перед решением задачи стоит задать вопросы:

- Какой ответ метода?
- Перечислены все ли параметры у запроса?

Далее стоит уточнить важные сущности. Если распишем эти сущности, они помогут составить тест-план:

- пользователь (авторизован/неавторизован, физик/юрик)
- корзина (пустая или с товарами)
- товары (в наличии или закончились, 1 товар или связка-товаров (bundle), категория товара (аптека, книги, ювелирка и проч.), тип товара(обычные, цифровые, подписки), тип доставки (супермаркет, свой товар, товар продавца и проч.))
- локация (в задаче ее нет, но это важный параметр, если о нем вспомнят, то +1 балл)

Здесь можно поговорить про то как уменьшить число комбинаций каждого с каждым.

В конце не забыть про чисто технические и негативные кейсы (кандидату не стоит начинать тестировать с них)

- Вызвать метод дважды
- Попробовать отправить запрос с несуществующими параметрами (несуществующий товар, несуществующего пользователя)
- Проверить верхние и нижние границы (quantity и общее число items)
- Попробовать отправить запрос с неправильными типами параметров
- Отправить только часть параметров
- Попробовать отправить пустой запрос

</p>
</details>

#### Дополнительные вопросы:

Q: *Какой здесь самый первый тест?*

A: Самый первый тест - самый частый сценарий: Авторизованный пользователь добавляет в пустую корзину книгу (любой другой товар), которая есть в наличии.

Q: *В каких ситуациях добавляется сразу несколько товаров в корзину?*

A: Если товары находятся в связке (bundle).

Q: *Как проверить, что метод отработал верно?*

A: Нужно убедиться, что товар действительно добавлен. Для этого смотрим в базу или дергаем метод GET, который вернет товары корзины.

______________________________________________________________________

### Смена локации

Сложность: **средняя**

<!--Автор: @igor.lyubin-->

#### Задача:

Пользователь на сайте меняет в левом верхнем углу меняет город. Когда он это делает дергается ручка location. Надо протестировать ручку. Как будете действовать?

Request:

```
POST /location
```

Body:

```json
{
  "user_id": "number",
  "address_uid": "string"
}
```

#### Ответ:

<details><summary>Решение</summary>
<p>

Перед решением задачи стоит задать вопросы:

- Как быть если пользователь не авторизован? Тогда вместо user_id передается параметр session
- Что такое address_uid? Это uuid какого-то адреса, населеного пункта.

Важные сущности здесь:

- пользователь (авторизован/неавторизован, физик/юрик)
- адреса - важно уточнить, что 2 адреса есть: **С** какого меняем **НА** какой

Адреса могут быть:

- Москва
- Санкт-Петербург
- Подмосковные города - Некрасовка
- Города милионники - Казань, Новосибирск...
- Поселки в республиках - Васильево
- Города из СНГ - Минск
- Города из зарубежья - Нью-Йорк

В конце не забыть про чисто технические и негативные кейсы (кандидату не стоит начинать тестировать с инх)

- Вызвать метод дважды
- Попробовать отправить запрос с несуществующими параметрами (несуществующий адрес, несуществующего пользователя)
- Попробовать отправить запрос с неправильными типами параметров
- Отправить только часть параметров
- Попробовать отправить пустой запрос

</p>
</details>

#### Дополнительные вопросы:

Q: *Какой здесь самый первый тест?*

A: Самый первый тест - самый частый сценарий. Например: с Москвы меняем на город миллионик.

### Данные банковской карты

Сложность: **средняя**

<!--Автор: @a.urlapova-->

#### Задача:

Есть метод REST API, получение карточных данных пользователя из БД.
Как проверить?

Request:

```
POST /v1/get-card
```

Body:

```json
{
  "token": [
    {
      "type": "string",
      "value": "string"
    }
  ],
  "masked": "bool"
}
```

#### Ответ:

<details><summary>Решение</summary>
<p>
Если нужно уточнить требования:
- нет авторизации, потому что метод работает в закрытом контуре, 
секьюрность осуществляется на уровне платформы
- тип токена - строка, есть несколько типов, велью - уникальный идентификатор(uuid)

Провести функциональные проверки:

- вызвать метод с правильными параметрами получить ответ 200
- вызвать метод по несуществующей карточке, получить ошибку (409 или 404)
- при использовании параметра masked данные возвращаются маскированными,
  нужно для дополнительной безопасности передачи данных. В некоторых случаях полные данные не нужны.
- используем POST для чтения, чтобы защитить данные - не сохранять передаваемые данные и не кешировать.

Дополнительные вопросы:

- проверка load, можно через jmeter или я.танк, попросить у девов/аналитиков профиль нагрузки

</p>
</details>

### Последний заказ

Сложность: **средняя**

<!--Автор: @emikryukov-->

#### Задача:

Есть handler для отрисовки последнего заказа в личном кабинете клиента.
Ниже представлена структура ответа из swagger. Какие 3 бизнес сценария ты проверил бы в первую очередь?

Request:

```json
GET /client/last_order?client_id={client_id}
```

Response:

```json
{  
  "client_id": "integer",
  "order_id": "integer",
  "order":[  
    {  
      "item_id": "integer",
      "item_qty": "integer",
      "item_price": "number",
    }
  ],
  "order_price": "number"
}
```

#### Ответ:

<details><summary>Решение</summary>
<p>

1. Существующий пользователь с 2 заказами
1. Существующий пользователь без заказов
1. Несуществующий пользователь

</p>
</details>

#### Наводки:

С (Candidate): Надо вместо client_id подставить string

I (Interviewer): *Контракт строго утвержден, ничего крому integer не может прилететь*

______________________________________________________________________

C: Нужно проверить первого клиента, последнего и посередине

I: *В чем отличия данных клиентов?*

______________________________________________________________________

C: Задумался и ничего не может предложить

I: *Представь, у тебя есть доступ к базе, в которой есть клиенты, заказы, связи между ними. У тебя есть реализованные автотесты, можешь сам написать. Какие бы ты 3 бизнес сценария проверил бы? (Подсказка в лоб: на каких данных ты бы проверил 3 сценария)*

______________________________________________________________________

C: Нужно проверить структуру ответа на типы данных

I: *Еще раз нужно повторить и акцентировать внимание, что нас интересует бизнес логика. Какие 3 сценария по бизнесу ты бы проверил?*

#### Дополнительные вопросы:

Q: *Что бы ты проверял в первом сценарии?*

A: Помимо данных надо проверить и структуру ответа, можно проверить значение order_price и количество данных в блоке order

______________________________________________________________________

Q: *Какой http-шный код ответа ожидаешь во втором сценарии? Каковым будет структура ответа?*

A: 200 код ошибки. Блок order пустой.

______________________________________________________________________

Q: *Какой http-шный код ответа ожидаешь в третьем сценарии?*

A: 404 с текстом ошибки

______________________________________________________________________

*Примечания:*

- Если кандидат во втором сценарии скажет 404. *А какой-то другой код бы вернул?*
- Если во 2 и 3 ответах 404 код. *А как различить эти 404?*
- Если первый сценарий назвал верно, а во втором проверяет схему. *Можно ли объедить эти 2 сценария?*

### Создание заказа

Сложность: **сложная**

<!--Автор: @dkolesnik-->

#### Задача:

Метод оформляет заказ на сайте. На вход принимает список отправлений с товарами и ожидаемую дату получения для каждого отправления. Адрес получения с комментариями. Платежный метод, например банковскую карту.

Request:

```json
POST /order
{
  "shipments": [ // отправления/коробки с товарами
    {
      "id": "number",
      "date": "number" // Ожидаемая дата доставки
    }
  ],
  "adress": {
    "id": "number",
    "comment": "string",
    "is_leave_at_door": "boolean" // оставить у двери
  },
  "payment_method": "string"
}
```

#### Ответ:

<details><summary>Решение</summary>
<p>

Перед решением задачи стоит задать вопросы:

- какой должен быть ответ? (304 на страницу оплаты. После либо 200, либо 400)
- как формируются отправления? (формируется автоматически исходя из корзины пользователя)
- как заполняется адрес? (Пользователь добавляет себе адрес. После используется id нужного адреса)

Важные сущности:

- платежный метод
- адрес
- отправления

Что проверять:

- Платежный метод:
  - у пользователя нет заполненых платежных методов
  - Есть один заполненый (например банковская карта)
  - Проверить разные варианты оплаты: оплата банковской картой, 3-D Secure и т.д.
  - Есть несколько (выбран один)
  - Передать невалидный платежный метод
  - Не передавать платежный метод
  - Проверить успешную оплату
  - Проверить неуспешную оплату
  - Оформить заказ, но не оплачивать. После истечения некоторого времени заказ должен быть отменен
- Адрес:
  - Валидный адрес без комментария
  - Проверка валидности комментария
  - Проверка оставить у двери
  - Невалидный адрес
  - Слишком длинный комментарий (например, > 3000 символов)
- Отправления:
  - Одно валидное отправление
  - Несколько отправлений
  - Без отправлений
  - Невалидные, несуществующие отправления
  - Минимально доступная дата принятия
  - Дата в будующем
  - Дата в прошлом
  - Разные даты для разных отправлений
  - Нужно проверить остатки товаров. После оформления заказа - товары должны резервироваться и быть недоступными для заказа. В случае неудачной оплаты - остатки должны возвращаться назад.
  - Крупногабаритные отправления
  - Проверить отправления без доступных дат для отправки
- Отправить запрос повторно
- Запрос без обязательных полей
- Отправить запрос с неверным типом полей
- Запрос отправляет неавторизованный пользователь

</p>
</details>
