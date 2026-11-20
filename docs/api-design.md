# REST API проєкту TechPulse

Базова адреса: `http://localhost:3000/api`

| # | Ресурс | Метод | Призначення | Успіх | Помилки |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 1 | `/rubrics` | GET | перелік рубрик | 200 | 500 |
| 2 | `/rubrics/:id` | GET | одна рубрика | 200 | 404 |
| 3 | `/rubrics/:id/articles` | GET | статті певної рубрики | 200 | 404 |
| 4 | `/articles` | GET | перелік статей із фільтрацією | 200 | 400 |
| 5 | `/articles/:id` | GET | картка статті | 200 | 404 |
| 6 | `/articles` | POST | створення статті (адмін) | 201 | 422 |
| 7 | `/articles/:id` | PUT | повне оновлення статті (адмін) | 200 | 404, 422 |
| 8 | `/articles/:id` | DELETE | видалення статті (адмін) | 204 | 404 |
| 9 | `/articles/:id/comments` | GET | коментарі до статті | 200 | 404 |
| 10 | `/articles/:id/comments` | POST | додавання коментаря | 201 | 422 |
| 11 | `/users/login` | POST | авторизація користувача | 200 | 401, 422 |

## Параметри GET /articles
| Параметр | Тип | Приклад | Опис |
| :--- | :--- | :--- | :--- |
| `rubric_id` | int | `?rubric_id=2` | фільтр за рубрикою |
| `author_id` | int | `?author_id=5` | фільтр за автором |
| `q` | string | `?q=javascript` | пошук за назвою або текстом |
| `sort` | enum | `?sort=date_desc` | сортування (`date_asc`, `date_desc`) |
| `page` | int | `?page=2` | номер сторінки |
| `limit` | int | `?limit=10` | кількість записів на сторінці |

## Формат помилки
```json
{
  "error": "VALIDATION_FAILED",
  "details": {
    "text": "Коментар не може бути порожнім",
    "email": "Невірний формат email"
  }
}
text