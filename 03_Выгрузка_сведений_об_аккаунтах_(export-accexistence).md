<!-- MarkdownTOC autolink="true" -->

- [Пример файла](#%D0%9F%D1%80%D0%B8%D0%BC%D0%B5%D1%80-%D1%84%D0%B0%D0%B9%D0%BB%D0%B0)
- [Описание элементов](#%D0%9E%D0%BF%D0%B8%D1%81%D0%B0%D0%BD%D0%B8%D0%B5-%D1%8D%D0%BB%D0%B5%D0%BC%D0%B5%D0%BD%D1%82%D0%BE%D0%B2)
    - [`ORG`](#org)
    - [`PersAcc`](#persacc)

<!-- /MarkdownTOC -->


Выгрузка данных производится программно по протоколу [обмена данными](01_Протокол_обмена.md).

Результат содержит сведения о лицевых счетах организации, существующих (уже загруженных) на сайте.

**Параметры запроса**:

|            | Возможные значения    |  Описание |
|----------- | --------------------- | --------  |
|**mode**    | `export`              | |
|**type**    | `accexistence`        | |
|**inn**     | Целое число           | ИНН организации. На сайте должен существовать *Объект управления* с указанным ИНН |

> Обязательные параметры выделены полужирным

# Пример файла

```xml
<?xml version="1.0" encoding="windows-1251"?>
<ORG inn="1215143804" filedate="14.01.2015 18:01:21" filetype="accexistence" version="3">
	<PersAcc kod_ls="1 TSGUz8Tz2N" login="" email=""></PersAcc>
	<PersAcc kod_ls="TSGU9rC3nR" login="" email=""></PersAcc>
	<PersAcc kod_ls="1 TSGsT2wL6w" login="demo" email="clients@vdgb-soft.ru"></PersAcc>
</ORG>
```

# Описание элементов

## `ORG`

Корневой элемент файла. Содержит элементы [`PersAcc`](#persacc).
	
**Атрибуты**

|             | Тип              | Описание |
| -------------| ---------------- | --- |
| **inn**      | Целое число      | ИНН организации, для которой запрашиваются данные |
| **filedate** | Дата и время     | Дата формирования выгрузки |
| **filetype** | Строка           | Содержит `accexistence` |
| **version**  | Целое число      | Содержит текущую версию формата обмена — `3` |

## `PersAcc`

Содержит сведения о лицевом счете, существующем на сайте.

**Атрибуты**

|              | Тип                | Описание |
| -------------| ------------------ | -------- |
| **kod_ls**   | Строка             | Код лицевого счета, соответсвует одноименному атрибуту в [файле загрузки данных по лицевомым счетам](07_Загрузка_данных_лицевых_счетов_(import-accounts).md) |
| login        | Строка             | Логин пользователя. Может быть пустым, если пользователь для лицевого счета не создан |
| email        | Строка             | E-mail пользователя. Может быть пустым, если пользователь для лицевого счета не создан или e-mail для него не указан |
