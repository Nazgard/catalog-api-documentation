# Группы (groups)

## `GET /:type/:mark/:mark_short_name/:model_id/:modification_id`

Возвращает объект с двумя массивам groups и breadcrumbs

| Конечная точка | Описание |
| :---- | :--------------- |
| GET /CARS_FOREIGN/AFTERMARKET/AC/4211/12428 | Группы AC ACE 4.6 |

### Пример запроса

```bash
curl -H 'Authorization: <token>' \
-X GET https://acat.online/api/catalogs/CARS_FOREIGN/AFTERMARKET/AC/4211/12428
```

### Пример ответа

```json
{
    "numbers": [
        {
            "type": "CARS_FOREIGN",
            "mark": "AFTERMARKET",
            "mark_short_name": "AC",
            "model_id": 4211,
            "modification_id": 12428,
            "group_id": 12096,
            "number": "XLS011",
            "name": "Масло осевого редуктора",
            "article_id": 129385604,
            "provider": {
                "id": 11353,
                "name": "CARLUBE",
                "image": "AFTERMARKET/logos/11353"
            }
        },
        ...
    ],
    "breadcrumbs": [
        ...
        ,{
            "name": "Масла",
            "url": "12096"
        }
    ]
}
```

### Значения groups

| Имя точка | Тип | Используется в URL | Описание |
| :---- | :------: | :------: | :--------------- |
| type | string | - | Тип кузова |
| mark | string | - | Название каталога (всегда будет AFTERMARKET) |
| mark_short_name | string | - | Сокращенное название марки |
| model_id | integer | - | Идентифкационный номер модели |
| modification_id | integer | - | Идентифкационный номер модификации |
| group_id | integer | - | Идентифкационный номер группы |
| number | string | Да | Номер |
| name | string | - | Название детали |
| article_id | integer | Да | ID артикула |
| provider | object | - | Производитель |
| provider.id | integer | Да | ID производителя |
| provider.name | string | - | Название производителя |
| provider.image | string | - | Путь до изображения производителя |

### Значения breadcrumbs

| Имя точка | Тип | Описание |
| :---- | :------: | :--------------- |
| name | string | Имя хлебной крошки |
| url | string | Адрес текущей хлебной крошки |


## `GET /:type/:mark/:mark_short_name/:model_id/:modification_id/:group_id/:provider_id/:number/:article_id`

### Для перехода к описанию номера нужно передать provider.id, number и article_id в GET параметры