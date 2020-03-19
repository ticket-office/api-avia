Получение номеров билетов и обновление данных заказа
====================================================

Позволяет получить номера билетов после оплаты. Также позволяет обновить текущий статус заказа, в случае, если при оплате был получен статус paid, а выписка произошла в течение следующих 10 минут.

Запрос
------

* Роут - /orders/update
* HTTP метод запроса - GET

Параметры запроса:

1. **id** - *string*, обязательный. Идентификатор заказа, полученный при бронировании.

Пример запроса:

```php
https://api.radiustravel.uz/avia/v1/orders/update?id=2&token=klmnPYz52MUJPH1ZsPXw
```

Пример ответа:
--------------

Структура ответа идентична получаемому при бронировании рекомендации. Отличие в полях status и ticket_number, значения которых обновлены после оплаты и выписки билетов.

```php
{
    "success":true,
    "date":"2020-03-17 18:14",
    "execution_time":8.029,
    "data":{
        "order":{
            "id":"A-A1253619921-1272",
            "created":"2020-03-17 18:14",
            "status":"ticketed", // обновлен текущий статус заказа
            "auto_cancellation":"2020-03-24 18:04",
            "price":{
                "UZS":{
                    "total":3198484,
                }
            },
            "client":{
                "name":"Тимофей",
                "email":"salmin@salmin.com",
                "phone":"+380730247742",
                "bonus_card":null
            },
            "tickets":[
                {
                    "pnr":"3291TM",
                }
            ],
            "passengers":[
                {
                    "id":283109,
                    "first_name":"Tymofii",
                    "middle_name":null,
                    "last_name":"Salmin",
                    "email":"salmin@salmin.com",
                    "phone":"+380730247742",
                    "gender":"M",
                    "birthdate":"1977-01-06",
                    "citizenship":"UA",
                    "age":"adt",
                    "key":"SALMIN_TYMOFII_ER56987_06-01-1977",
                    "doc_type":"A",
                    "doc_number":"ER56987",
                    "doc_expire":"2021-11-25",
                    "bonus_card":null,
                    "ticket_number":"8014944083254", // получен номер билета
                    "ticket_price":1599175
                },{
                    "id":283110,
                    "first_name":"Alla",
                    "middle_name":null,
                    "last_name":"Petrova",
                    "email":"salmin@salmin.com",
                    "phone":"+380730247742",
                    "gender":"F",
                    "birthdate":"1983-10-12",
                    "citizenship":"UA",
                    "age":"adt",
                    "key":"PETROVA_ALLA_AR46182_12-10-1983",
                    "doc_type":"A",
                    "doc_number":"AR46182",
                    "doc_expire":"2021-11-14",
                    "bonus_card":null,
                    "ticket_number":"3121018443597", // получен номер билета
                    "ticket_price":1599309
                }
            ],
            "directions":[ // направления перелетов
                ... // структура и данные идентичны элементу directions при запросе списка рекомендаций
            ],
            "rules":[ // правила тарифа для сегментов перелета
                ... // структура и данные идентичны элементу rules при запросе данных и условий тарифа для отдельной рекомендации
            ],
        }
    }
}
```