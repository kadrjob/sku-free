<a href="https://infostart.ru/1c/tools/sku-search-free/" title="Публикация на Инфостарте">
  <img src="https://infostart.ru/bitrix/templates/sandbox_empty/assets/tpl/abo/img/logo.svg" alt="Infostart" height="32">
</a>

---

# SKU Search Free — умный поиск дублей номенклатуры для 1С

[![Release](https://img.shields.io/github/v/release/kadrjob/sku-free)](https://github.com/kadrjob/sku-free/releases/latest)
[![Сайт](https://img.shields.io/badge/сайт-sku--search.online-blue)](https://sku-search.online)
[![Лицензия](https://img.shields.io/github/license/kadrjob/sku-free)](LICENSE)

SKU Search Free — это бесплатная поисковая подсистема рядом с 1С, которая помогает операторам и менеджерам не создавать дубли номенклатуры. Работает за 15–100 мс, ищет с опечатками, по артикулу, штрихкоду, коду и дополнительным полям. Один бинарник, без Java, Python, Docker и GPU.

**👉 Скачать Free:** [https://github.com/kadrjob/sku-free/releases/latest](https://github.com/kadrjob/sku-free/releases/latest)  
**👉 Узнать про PRO-версию и купить лицензию:** [https://sku-search.online/purchase/](https://sku-search.online/purchase/)  
**👉 Сайт и документация:** [https://sku-search.online](https://sku-search.online)

---

## Оглавление

- [Быстрый старт](#быстрый-старт-за-5-минут)
- [Что умеет Free](#что-умеет-free)
- [Free vs PRO](#free-vs-pro)
- [Скачать и установить](#скачать-и-установить)
- [Как подключить к 1С](#как-подключить-к-1с)
- [PRO-версия](#pro-версия)
- [FAQ](#faq)
- [Лицензия](#лицензия)

---

## Быстрый старт за 5 минут

1. Скачайте архив `sku-search-free.zip` из [последнего релиза](https://github.com/kadrjob/sku-free/releases/latest).
2. Распакуйте и переименуйте `config.toml.default` в `config.toml`.
3. Запустите: `./sku-service`.
4. Откройте в браузере [http://localhost:8080](http://localhost:8080).
5. Загрузите демо-каталог: `./sku-cli import --csv demo-data.csv`.
6. Введите в поисковой строке «молоко» или «болт м16».
7. Результат появится за 15–100 мс.

Готово — можно встраивать поиск в свои документы и обработки 1С.

---

## Что умеет Free

- **Полнотекстовый и нечёткий поиск** по названию, артикулу, штрихкоду, коду, GUID.
- **Опечатки и разные формы слов** — находит «болтом», «болты», «оцинк».
- **Синонимы** — «цинк» = «оцинкованный", настраиваются администратором.
- **Дополнительные поля** — бренд, поставщик, материал, размер, серийный номер.
- **Обучение на действиях операторов** — accept/reject улучшают качество поиска.
- **Встроенный веб-интерфейс, Swagger UI, CLI**.
- **Готовое расширение для 1С** (`SKU.epf` + `СКУПоиск.cfe`).

---

## Free vs PRO

| Возможность | Free | PRO |
|---|---|---|
| Полнотекстовый и fuzzy-поиск | ✅ | ✅ |
| Поиск по артикулу / штрихкоду / коду | ✅ | ✅ |
| Дополнительные поля и синонимы | ✅ | ✅ |
| Веб-интерфейс, Swagger, CLI | ✅ | ✅ |
| Расширение для 1С | ✅ | ✅ |
| Семантический поиск по смыслу | — | ✅ |
| Гибридный поиск (Tantivy + эмбеддинги) | — | ✅ |
| ONNX-модели (bge-m3, e5) | — | ✅ |
| Кросс-коды и аналоги | — | ✅ |
| Иерархические связи / BOM | — | ✅ |
| Аналитика запросов и рекомендации | — | ✅ |
| Фоновая индексация эмбеддингов | — | ✅ |
| Кэширование популярных запросов | — | ✅ |

**Free решает 95 % задач по поиску дублей.** Если нужны семантика, кросс-коды и аналитика — смотрите PRO.

---

## Скачать и установить

### Последний релиз

```bash
wget https://github.com/kadrjob/sku-free/releases/latest/download/sku-search-free.zip
unzip sku-search-free.zip -d sku-search-free
cd sku-search-free
cp config.toml.default config.toml
./sku-service
```

После запуска доступны:

- Главная: [http://localhost:8080](http://localhost:8080)
- Документация: [http://localhost:8080/docs](http://localhost:8080/docs)
- Swagger: [http://localhost:8080/swagger-ui](http://localhost:8080/swagger-ui)
- Health: [http://localhost:8080/health](http://localhost:8080/health)

### Что в архиве

```
sku-search-free/
├── sku-service           # сервис (Linux x86_64)
├── sku-cli               # CLI-утилита
├── demo-data.csv         # 10 000 демо-товаров
├── demo-data.zip         # демо-данные в архиве
├── config.toml.default   # пример конфига
├── setup.sh              # скрипт первичной настройки (Linux/macOS)
├── setup.cmd             # скрипт первичной настройки (Windows)
├── SKU.epf               # внешняя обработка для 1С
├── СКУПоиск.cfe          # расширение для 1С
├── Dockerfile
├── docker-compose.yml
├── LICENSE.md
└── README.md
```

---

## Как подключить к 1С

Сервис общается по HTTP/JSON. Минимальный пример:

```bsl
&НаСервере
Функция НайтиПохожиеТовары(Название)
    Соединение = Новый HTTPСоединение("localhost", 8080);
    Запрос = Новый HTTPЗапрос("/find");
    Запрос.Заголовки.Вставить("Content-Type", "application/json");
    Тело = "{ ""items"": [ { ""name"": """ + Название + """ } ] }";
    Запрос.УстановитьТелоИзСтроки(Тело);
    Ответ = Соединение.ОтправитьДляОбработки(Запрос);
    Возврат Ответ.ПолучитьТелоКакСтроку();
КонецФункции
```

В архиве идёт готовое расширение 1С, которое берёт на себя основной обмен с сервисом.

---

## PRO-версия

Если Free вам понравился, но нужно больше — переходите на PRO на нашем сайте:

👉 [https://sku-search.online/purchase/](https://sku-search.online/purchase/)

**Что добавляет PRO:**

- **Семантический поиск** — находит товары по смыслу, даже если слова не совпадают.
- **Гибридный поиск** — объединяет точность Tantivy и семантику ONNX-эмбеддингов.
- **Кросс-коды** — группы аналогов и заменителей.
- **Иерархические связи** — BOM / Where-Used разузлование.
- **Аналитика** — топ запросов, частые reject, рекомендации по настройке.
- **Фоновая индексация эмбеддингов** — `/add` отвечает быстро, векторы строятся в фоне.

**Стоимость:** 19 900 ₽ за 6 месяцев, продление — 9 000 ₽. Подробности, оплата и демо — на сайте [sku-search.online](https://sku-search.online).

---

## FAQ

**Ничего не находит**

- Данные загружены? Проверьте `/health` → `db_record_count`.
- Используете `id` (не `1c_id_in`) при импорте?

**Не находит с опечатками**

- Увеличьте `fuzzy_max_distance` в `config.toml` (0 — точное, 1 — одна ошибка, 2 — две).

**Находит не те товары**

- Подстройте порог `auto_match_threshold`.
- Добавьте стоп-слова и синонимы.

**Как искать только по бренду/материалу?**

- Передайте `"name": ""` и нужное extra-поле: `"brand": "Bosch"`.

**Почему «болтом» не находит «болт»?**

- По умолчанию `fuzzy_max_distance = 1`. Для морфологических форм установите `fuzzy_max_distance = 2`.

---

## Лицензия

SKU Search Free распространяется бесплатно и без ограничений по времени в рамках одной организации. Подробности — в файле [LICENSE.md](LICENSE.md).

PRO-версия — коммерческая лицензия с подпиской на обновления. Покупка и продление на сайте [sku-search.online](https://sku-search.online/purchase/).

---

**Связаться с нами:**

- Сайт: [https://sku-search.online](https://sku-search.online)
- Поддержка: [https://sku-search.online/support/](https://sku-search.online/support/)
- Релизы SKU Search (все редакции): [https://github.com/kadrjob/sku-search/releases](https://github.com/kadrjob/sku-search/releases)
