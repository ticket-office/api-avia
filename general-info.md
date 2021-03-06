Общая информация
=================

* Версия API: 1.1.0
* Базовый URL тестовой среды - https://test.radiustravel.uz/v1
* В заголовках запроса необходимо передавать параметр Accept-Encoding: gzip
* В качестве транспорта используется HTTP протокол.
* Все ответы приходят в виде JSON структур.

Структура ответа
----------------

Каждый ответ содержит следующие поля:

1. **success** - *boolean*, статус выполнения запроса.
2. **date** - *string*, дата и время формирования ответа по Гринвичу.
3. **execution_time** - *float*, время выполнения запроса, секунд.
4. **data** - *array*, блок данных.

Пример ответа:

```php
{
    "success":true,
    "date":"2020-03-17 11:05",
    "execution_time":4.828,
    "data":{
        "found":100,
        "flights":[...]
    }
}
```

Обработка ошибок
----------------

В случае возникновения ошибки сервер вернет ответ, у которого в поле data будет массив, содержащий 2 элемента:

1. **code** - *integer*, код ошибки. Допустимые значения указаны в [справочнике](guide.md).
2. **message** - *string*, текстовое описание ошибки.

Пример ответа:

```php
{
    "success":false,
    "date":"2020-03-17 11:31",
    "execution_time":0.086,
    "data":{
        "code":2,
        "message":"Неверный формат запроса."
    }
}
```