<!-- MarkdownTOC autolink="true" -->

- [Пример файла](#%D0%9F%D1%80%D0%B8%D0%BC%D0%B5%D1%80-%D1%84%D0%B0%D0%B9%D0%BB%D0%B0)
- [Описание элементов](#%D0%9E%D0%BF%D0%B8%D1%81%D0%B0%D0%BD%D0%B8%D0%B5-%D1%8D%D0%BB%D0%B5%D0%BC%D0%B5%D0%BD%D1%82%D0%BE%D0%B2)
    - [`responsible_users`](#responsible_users)
    - [`responsible_user`](#responsible_user)

<!-- /MarkdownTOC -->


Загрузка данных производится на странице *Сервисы — ТСЖ: Аварийно-диспетчерская служба — Импорт подрядных организаций* в [административной части](http://dev.1c-bitrix.ru/learning/course/index.php?COURSE_ID=35&LESSON_ID=2833#admin) сайта.

На сайте будут созданы (или обновлены) данные пользователей, указанных в файле.

# Пример файла

```xml
<?xml version="1.0" encoding="windows-1251"?>
<responsible_users filetype=”contractors”>
    <responsible_user kod="S0000003" email="support_user@mail.ru" name="ООО «Подрядная организация» " />
    <responsible_user kod="S0000004" email="support_user_2@mail.ru" name="Еще одна подрядная организация" />
</responsible_users>
```

# Описание элементов

## `responsible_users`

Корневой элемент файла. Содержит элементы [`responsible_user`](#responsible_user).

**Атрибуты**

|              | Тип              | Описание |
| -------------| ---------------- | --- |
| filetype     | Строка           | Содержит `contractors` |

## `responsible_user`

Представляет собой элемент с полями подрядной организации.

**Атрибуты**

|              | Тип                | Описание |
| -------------| ------------------ | -------- |
| **kod**      | Строка             | Уникальный идентификатор пользователя |
| **email**    | Строка             | E-mail пользователя |
| **name**     | Строка             | Наименование организации |

Логин пользователя на сайте будет сформирован как **support_`kod`**, пароль — сгенерирован случайным образом и записан на вкладке *Заметки администратора* на форме редактирования пользователя.