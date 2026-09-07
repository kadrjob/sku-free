# Лицензии используемых компонентов

Файл содержит сведения о лицензиях собственного кода сервиса и всех сторонних Rust-крейтов, включаемых в поставку.

## Nomenclature Search Service (sku-search)

**Основная лицензия:** MIT

Copyright (c) 2026 Dmitry S. <kadr78job@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

---

## Состав поставляемых зависимостей

Сервис собирается в нескольких редакциях:
- **Free** (`cargo build --release --no-default-features`) — только Tantivy, без эмбеддингов.
- **PRO** (`cargo build --release`, `features = ["pro", "lancedb"]`) — Tantivy + ONNX-эмбеддинги + LanceDB. Это режим по умолчанию и основная production-сборка.
- **FULL** (`cargo build --release --features full`) — PRO + опциональная поддержка Qdrant (`qdrant-client`, `tonic`).

| Режим | Уникальных крейтов |
|-------|-------------------|
| Free  | 436 |
| PRO   | 704 |
| FULL  | 728 |

PRO включает в себя все зависимости Free-режима. FULL добавляет 24 крейта для интеграции с Qdrant.

## Сводка по типам лицензий (PRO/режим по умолчанию)

Все зависимости относятся к пермиссивным или data-лицензиям; strong copyleft (GPL/AGPL) отсутствует.

| Лицензия | Количество крейтов | Примечание |
|----------|-------------------:|------------|
| `Apache-2.0 OR MIT` | 389 | |
| `MIT` | 135 | |
| `Apache-2.0` | 80 | |
| `Unicode-3.0` | 18 | |
| `Apache-2.0 OR Apache-2.0 WITH LLVM-exception OR MIT` | 17 | |
| `MIT OR Unlicense` | 15 | |
| `Apache-2.0 OR MIT OR Zlib` | 7 | |
| `ISC` | 6 | |
| `BSD-3-Clause` | 3 | |
| `Apache-2.0 OR ISC OR MIT` | 3 | |
| `BSD-3-Clause AND MIT` | 2 | |
| `BSD-3-Clause OR MIT` | 2 | |
| `Apache-2.0 OR CC0-1.0 OR MIT-0` | 2 | |
| `Zlib` | 2 | |
| `CC0-1.0` | 2 | |
| `Apache-2.0 OR LGPL-2.1-or-later OR MIT` | 2 | |
| `Apache-2.0 OR BSD-2-Clause OR MIT` | 2 | |
| `0BSD OR Apache-2.0 OR MIT` | 1 | |
| `BSD-2-Clause` | 1 | |
| `(Apache-2.0 OR ISC) AND ISC` | 1 | |
| `(Apache-2.0 OR ISC OR MIT) AND (Apache-2.0 OR ISC OR MIT-0) AND (Apache-2.0 OR ISC) AND Apache-2.0 AND BSD-3-Clause AND ISC AND MIT` | 1 | |
| `Apache-2.0 OR Apache-2.0 WITH LLVM-exception OR CC0-1.0` | 1 | |
| `(Apache-2.0 OR MIT) AND BSD-3-Clause` | 1 | |
| `MIT OR zlib-acknowledgement` | 1 | |
| `Apache-2.0 OR MIT OR MPL-2.0` | 1 | |
| `0BSD` | 1 | |
| `(Apache-2.0 OR MIT) AND Apache-2.0` | 1 | |
| `MPL-2.0` | 1 | |
| `Apache-2.0 AND ISC` | 1 | |
| `Apache-2.0 OR BSL-1.0` | 1 | |
| `NO-LICENSE` | 1 | |
| `(Apache-2.0 OR MIT) AND Unicode-3.0` | 1 | |
| `CDLA-Permissive-2.0` | 1 | |
| `BSL-1.0` | 1 | |

## Ключевые зависимости

| Крейт | Назначение | Лицензия |
|-------|-----------|----------|
| `axum` | Веб-фреймворк | `MIT` |
| `tokio` | Асинхронный runtime | `MIT` |
| `tower` | Мiddleware/composition | `MIT` |
| `tower-http` | HTTP middleware | `MIT` |
| `tracing` | Структурированное логирование | `MIT` |
| `tracing-subscriber` | Подписчик tracing | `MIT` |
| `tantivy` | Полнотекстовый поисковый движок | `MIT` |
| `serde` | Сериализация | `Apache-2.0 OR MIT` |
| `serde_json` | JSON сериализация | `Apache-2.0 OR MIT` |
| `clap` | CLI парсер | `Apache-2.0 OR MIT` |
| `clap_complete` | Автодополнение CLI | `Apache-2.0 OR MIT` |
| `clap_mangen` | Man-страницы CLI | `Apache-2.0 OR MIT` |
| `reqwest` | HTTP клиент | `Apache-2.0 OR MIT` |
| `rayon` | Параллелизм данных | `Apache-2.0 OR MIT` |
| `dashmap` | Конкурентный HashMap | `MIT` |
| `parking_lot` | Синхронизация | `Apache-2.0 OR MIT` |
| `lru` | LRU кэш | `MIT` |
| `moka` | Кэш | `(Apache-2.0 OR MIT) AND Apache-2.0` |
| `utoipa` | OpenAPI | `Apache-2.0 OR MIT` |
| `utoipa-swagger-ui` | Swagger UI | `Apache-2.0 OR MIT` |
| `config` | Загрузка конфигурации | `Apache-2.0 OR MIT` |
| `toml` | TOML парсер | `Apache-2.0 OR MIT` |
| `lancedb` | Векторное хранилище (PRO) | `Apache-2.0` |
| `ort` | ONNX Runtime (PRO) | `Apache-2.0 OR MIT` |
| `tokenizers` | Токенизация (PRO) | `Apache-2.0` |
| `ndarray` | N-мерные массивы (PRO) | `Apache-2.0 OR MIT` |
| `rusqlite` | SQLite (PRO) | `MIT` |
| `metrics` | Метрики (PRO) | `MIT` |
| `notify` | Hot-reload синонимов (PRO) | `CC0-1.0` |
| `arrow` | Apache Arrow (PRO) | `Apache-2.0` |
| `chrono` | Работа с датами/временем (PRO) | `Apache-2.0 OR MIT` |
| `uuid` | UUID | `Apache-2.0 OR MIT` |
| `sysinfo` | Информация о системе | `MIT` |
| `csv` | CSV парсер | `MIT OR Unlicense` |
| `anyhow` | Обработка ошибок | `Apache-2.0 OR MIT` |
| `thiserror` | Производные ошибки | `Apache-2.0 OR MIT` |
| `tempfile` | Временные файлы | `Apache-2.0 OR MIT` |
| `futures` | Асинхронные примитивы | `Apache-2.0 OR MIT` |
| `async-trait` | Async traits | `Apache-2.0 OR MIT` |
| `aho-corasick` | Множественный поиск строк | `MIT OR Unlicense` |

### Опциональные Qdrant-зависимости (только FULL)

| Крейт | Назначение | Лицензия |
|-------|-----------|----------|
| `qdrant-client` | Клиент Qdrant | `Apache-2.0` |
| `tonic` | gRPC клиент | `MIT` |

## Зависимости, требующие особого внимания

Ниже перечислены крейты с лицензиями, отличными от «Apache-2.0 OR MIT» или «MIT», которые необходимо сохранять в составе поставки и указывать в уведомлениях.

### `MPL-2.0`

| Крейт | Версия | Репозиторий |
|-------|--------|-------------|
| `htmlescape` | 0.3.1 | https://github.com/veddan/rust-htmlescape |
| `option-ext` | 0.2.0 | https://github.com/soc/option-ext.git |

### `BSL-1.0`

| Крейт | Версия | Репозиторий |
|-------|--------|-------------|
| `ryu` | 1.0.23 | https://github.com/dtolnay/ryu |
| `xxhash-rust` | 0.8.15 | https://github.com/DoumanAsh/xxhash-rust |

### `CDLA-Permissive-2.0`

| Крейт | Версия | Репозиторий |
|-------|--------|-------------|
| `webpki-root-certs` | 1.0.7 | https://github.com/rustls/webpki-roots |

### `Unicode-3.0`

| Крейт | Версия | Репозиторий |
|-------|--------|-------------|
| `icu_collections` | 2.2.0 | https://github.com/unicode-org/icu4x |
| `icu_locale_core` | 2.2.0 | https://github.com/unicode-org/icu4x |
| `icu_normalizer` | 2.2.0 | https://github.com/unicode-org/icu4x |
| `icu_normalizer_data` | 2.2.0 | https://github.com/unicode-org/icu4x |
| `icu_properties` | 2.2.0 | https://github.com/unicode-org/icu4x |
| `icu_properties_data` | 2.2.0 | https://github.com/unicode-org/icu4x |
| `icu_provider` | 2.2.0 | https://github.com/unicode-org/icu4x |
| `litemap` | 0.8.2 | https://github.com/unicode-org/icu4x |
| `potential_utf` | 0.1.5 | https://github.com/unicode-org/icu4x |
| `tinystr` | 0.8.3 | https://github.com/unicode-org/icu4x |
| `unicode-ident` | 1.0.24 | https://github.com/dtolnay/unicode-ident |
| `writeable` | 0.6.3 | https://github.com/unicode-org/icu4x |
| `yoke` | 0.8.2 | https://github.com/unicode-org/icu4x |
| `yoke-derive` | 0.8.2 | https://github.com/unicode-org/icu4x |
| `zerofrom` | 0.1.7 | https://github.com/unicode-org/icu4x |
| `zerofrom-derive` | 0.1.7 | https://github.com/unicode-org/icu4x |
| `zerotrie` | 0.2.4 | https://github.com/unicode-org/icu4x |
| `zerovec` | 0.11.6 | https://github.com/unicode-org/icu4x |
| `zerovec-derive` | 0.11.3 | https://github.com/unicode-org/icu4x |

### `CC0-1.0`

| Крейт | Версия | Репозиторий |
|-------|--------|-------------|
| `blake3` | 1.8.4 | https://github.com/BLAKE3-team/BLAKE3 |
| `constant_time_eq` | 0.4.2 | https://github.com/cesarb/constant_time_eq |
| `dunce` | 1.0.5 | https://gitlab.com/kornelski/dunce |
| `notify` | 8.2.0 | https://github.com/notify-rs/notify.git |
| `tiny-keccak` | 2.0.2 | — |

### `Apache-2.0 OR LGPL-2.1-or-later OR MIT`

| Крейт | Версия | Репозиторий |
|-------|--------|-------------|
| `r-efi` | 5.3.0 | https://github.com/r-efi/r-efi |
| `r-efi` | 6.0.0 | https://github.com/r-efi/r-efi |

### `Apache-2.0 OR BSL-1.0`

| Крейт | Версия | Репозиторий |
|-------|--------|-------------|
| `ryu` | 1.0.23 | https://github.com/dtolnay/ryu |

### `MIT OR zlib-acknowledgement`

| Крейт | Версия | Репозиторий |
|-------|--------|-------------|
| `fastdivide` | 0.4.2 | https://github.com/fulmicoton/fastdivide |

### `Apache-2.0 OR MIT OR MPL-2.0`

| Крейт | Версия | Репозиторий |
|-------|--------|-------------|
| `htmlescape` | 0.3.1 | https://github.com/veddan/rust-htmlescape |

### Примечания к особым лицензиям

- **MPL-2.0** (`option-ext`, тянется через `lancedb` → `dirs` → `dirs-sys`): Mozilla Public License 2.0 является «weak copyleft». При статической линковке в бинарный файл сервиса она не распространяет copyleft на код `sku-search`, но требует сохранения текста лицензии и предоставления исходного кода самого `option-ext` при его модификации. Мы используем неизменённую библиотеку.
- **BSL-1.0** (`xxhash-rust`, тянется через `lancedb`): Boost Software License — пермиссивная лицензия, требует сохранения уведомлений об авторских правах.
- **CDLA-Permissive-2.0** (`webpki-root-certs`, `webpki-roots`): лицензия на наборы данных (корневые сертификаты). Пермиссивная, требует атрибуции.
- **Unicode-3.0** (ICU-крейты, `unicode-ident` и др.): лицензия Unicode, пермиссивная, требует сохранения уведомлений о лицензии и отказа от ответственности.
- **CC0-1.0** (`notify`, `tiny-keccak`, `blake3`/`constant_time_eq`/`dunce` в некоторых путях): общественное достояние, пермиссивная для любого использования.
- **Apache-2.0 OR LGPL-2.1-or-later OR MIT** (`r-efi`): мы используем крейт на условиях Apache-2.0 или MIT, исключая LGPL-вариант.
- **Apache-2.0 OR BSL-1.0** (`ryu`): используем на условиях Apache-2.0.
- **Apache-2.0 OR MIT OR MPL-2.0** (`htmlescape`): используем на условиях MIT/Apache-2.0.
- **MIT OR zlib-acknowledgement** (`fastdivide`): используем на условиях MIT.

## Полнотекстовые лицензии, применимые к зависимостям

Полные тексты лицензий доступны в официальных репозиториях соответствующих проектов. Для пермиссивных лицензий (MIT, Apache-2.0, BSD, ISC, Zlib) требуется сохранение уведомлений об авторских правах.

### MIT License (выдержка)
```
Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
```

### Apache License 2.0 (выдержка)
```
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

### MPL-2.0 (краткое содержание)
Mozilla Public License 2.0 допускает статическую линковку с проприетарным кодом при условии, что исходный код самого MPL-лицензированного файла остаётся доступным. Код `sku-search` не попадает под действие MPL-2.0.

## Полный список зависимостей PRO-режима

| Крейт | Версия | Лицензия | Репозиторий |
|-------|--------|----------|-------------|
| `adler2` | 2.0.1 | `0BSD OR Apache-2.0 OR MIT` | https://github.com/oyvindln/adler2 |
| `ahash` | 0.8.12 | `Apache-2.0 OR MIT` | https://github.com/tkaitchuck/ahash |
| `aho-corasick` | 1.1.4 | `MIT OR Unlicense` | https://github.com/BurntSushi/aho-corasick |
| `alloc-no-stdlib` | 2.0.4 | `BSD-3-Clause` | https://github.com/dropbox/rust-alloc-no-stdlib |
| `alloc-stdlib` | 0.2.2 | `BSD-3-Clause` | https://github.com/dropbox/rust-alloc-no-stdlib |
| `allocator-api2` | 0.2.21 | `Apache-2.0 OR MIT` | https://github.com/zakarumych/allocator-api2 |
| `android_system_properties` | 0.1.5 | `Apache-2.0 OR MIT` | https://github.com/nical/android_system_properties |
| `anstream` | 1.0.0 | `Apache-2.0 OR MIT` | https://github.com/rust-cli/anstyle.git |
| `anstyle` | 1.0.14 | `Apache-2.0 OR MIT` | https://github.com/rust-cli/anstyle.git |
| `anstyle-parse` | 1.0.0 | `Apache-2.0 OR MIT` | https://github.com/rust-cli/anstyle.git |
| `anstyle-query` | 1.1.5 | `Apache-2.0 OR MIT` | https://github.com/rust-cli/anstyle.git |
| `anstyle-wincon` | 3.0.11 | `Apache-2.0 OR MIT` | https://github.com/rust-cli/anstyle.git |
| `anyhow` | 1.0.102 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/anyhow |
| `arbitrary` | 1.4.2 | `Apache-2.0 OR MIT` | https://github.com/rust-fuzz/arbitrary/ |
| `arc-swap` | 1.9.1 | `Apache-2.0 OR MIT` | https://github.com/vorner/arc-swap |
| `arraydeque` | 0.5.1 | `Apache-2.0 OR MIT` | https://github.com/andylokandy/arraydeque |
| `arrayref` | 0.3.9 | `BSD-2-Clause` | https://github.com/droundy/arrayref |
| `arrayvec` | 0.7.6 | `Apache-2.0 OR MIT` | https://github.com/bluss/arrayvec |
| `arrow` | 57.3.0 | `Apache-2.0` | https://github.com/apache/arrow-rs |
| `arrow-arith` | 57.3.0 | `Apache-2.0` | https://github.com/apache/arrow-rs |
| `arrow-array` | 57.3.0 | `Apache-2.0` | https://github.com/apache/arrow-rs |
| `arrow-buffer` | 57.3.0 | `Apache-2.0` | https://github.com/apache/arrow-rs |
| `arrow-cast` | 57.3.0 | `Apache-2.0` | https://github.com/apache/arrow-rs |
| `arrow-csv` | 57.3.0 | `Apache-2.0` | https://github.com/apache/arrow-rs |
| `arrow-data` | 57.3.0 | `Apache-2.0` | https://github.com/apache/arrow-rs |
| `arrow-ipc` | 57.3.0 | `Apache-2.0` | https://github.com/apache/arrow-rs |
| `arrow-json` | 57.3.0 | `Apache-2.0` | https://github.com/apache/arrow-rs |
| `arrow-ord` | 57.3.0 | `Apache-2.0` | https://github.com/apache/arrow-rs |
| `arrow-row` | 57.3.0 | `Apache-2.0` | https://github.com/apache/arrow-rs |
| `arrow-schema` | 57.3.0 | `Apache-2.0` | https://github.com/apache/arrow-rs |
| `arrow-select` | 57.3.0 | `Apache-2.0` | https://github.com/apache/arrow-rs |
| `arrow-string` | 57.3.0 | `Apache-2.0` | https://github.com/apache/arrow-rs |
| `async-channel` | 2.5.0 | `Apache-2.0 OR MIT` | https://github.com/smol-rs/async-channel |
| `async-compression` | 0.4.41 | `Apache-2.0 OR MIT` | https://github.com/Nullus157/async-compression |
| `async-lock` | 3.4.2 | `Apache-2.0 OR MIT` | https://github.com/smol-rs/async-lock |
| `async-recursion` | 1.1.1 | `Apache-2.0 OR MIT` | https://github.com/dcchut/async-recursion |
| `async-trait` | 0.1.89 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/async-trait |
| `async_cell` | 0.2.3 | `MIT` | https://gitlab.com/samsartor/async_cell |
| `atoi` | 2.0.0 | `MIT` | https://github.com/pacman82/atoi-rs |
| `atomic-waker` | 1.1.2 | `Apache-2.0 OR MIT` | https://github.com/smol-rs/atomic-waker |
| `autocfg` | 1.5.0 | `Apache-2.0 OR MIT` | https://github.com/cuviper/autocfg |
| `aws-lc-rs` | 1.16.3 | `(Apache-2.0 OR ISC) AND ISC` | https://github.com/aws/aws-lc-rs |
| `aws-lc-sys` | 0.40.0 | `(Apache-2.0 OR ISC OR MIT) AND (Apache-2.0 OR ISC OR MIT-0) AND (Apache-2.0 OR ISC) AND Apache-2.0 AND BSD-3-Clause AND ISC AND MIT` | https://github.com/aws/aws-lc-rs |
| `axum` | 0.7.9 | `MIT` | https://github.com/tokio-rs/axum |
| `axum-core` | 0.4.5 | `MIT` | https://github.com/tokio-rs/axum |
| `base64` | 0.13.1 | `Apache-2.0 OR MIT` | https://github.com/marshallpierce/rust-base64 |
| `base64` | 0.22.1 | `Apache-2.0 OR MIT` | https://github.com/marshallpierce/rust-base64 |
| `base64ct` | 1.8.3 | `Apache-2.0 OR MIT` | https://github.com/RustCrypto/formats |
| `bigdecimal` | 0.4.10 | `Apache-2.0 OR MIT` | https://github.com/akubera/bigdecimal-rs |
| `bitflags` | 1.3.2 | `Apache-2.0 OR MIT` | https://github.com/bitflags/bitflags |
| `bitflags` | 2.11.1 | `Apache-2.0 OR MIT` | https://github.com/bitflags/bitflags |
| `bitpacking` | 0.9.3 | `MIT` | https://github.com/quickwit-oss/bitpacking |
| `bitvec` | 1.0.1 | `MIT` | https://github.com/bitvecto-rs/bitvec |
| `blake2` | 0.10.6 | `Apache-2.0 OR MIT` | https://github.com/RustCrypto/hashes |
| `blake3` | 1.8.4 | `Apache-2.0 OR Apache-2.0 WITH LLVM-exception OR CC0-1.0` | https://github.com/BLAKE3-team/BLAKE3 |
| `block-buffer` | 0.10.4 | `Apache-2.0 OR MIT` | https://github.com/RustCrypto/utils |
| `bon` | 3.9.1 | `Apache-2.0 OR MIT` | https://github.com/elastio/bon |
| `bon-macros` | 3.9.1 | `Apache-2.0 OR MIT` | https://github.com/elastio/bon |
| `brotli` | 8.0.2 | `BSD-3-Clause AND MIT` | https://github.com/dropbox/rust-brotli |
| `brotli-decompressor` | 5.0.0 | `BSD-3-Clause OR MIT` | https://github.com/dropbox/rust-brotli-decompressor |
| `bumpalo` | 3.20.2 | `Apache-2.0 OR MIT` | https://github.com/fitzgen/bumpalo |
| `bytemuck` | 1.25.0 | `Apache-2.0 OR MIT OR Zlib` | https://github.com/Lokathor/bytemuck |
| `byteorder` | 1.5.0 | `MIT OR Unlicense` | https://github.com/BurntSushi/byteorder |
| `bytes` | 1.11.1 | `MIT` | https://github.com/tokio-rs/bytes |
| `cc` | 1.2.60 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/cc-rs |
| `census` | 0.4.2 | `MIT` | https://github.com/quickwit-inc/census |
| `cesu8` | 1.1.0 | `Apache-2.0 OR MIT` | https://github.com/emk/cesu8-rs |
| `cfg-if` | 1.0.4 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/cfg-if |
| `cfg_aliases` | 0.2.1 | `MIT` | https://github.com/katharostech/cfg_aliases |
| `chacha20` | 0.10.0 | `Apache-2.0 OR MIT` | https://github.com/RustCrypto/stream-ciphers |
| `chrono` | 0.4.44 | `Apache-2.0 OR MIT` | https://github.com/chronotope/chrono |
| `chrono-tz` | 0.10.4 | `Apache-2.0 OR MIT` | https://github.com/chronotope/chrono-tz |
| `clap` | 4.6.1 | `Apache-2.0 OR MIT` | https://github.com/clap-rs/clap |
| `clap_builder` | 4.6.0 | `Apache-2.0 OR MIT` | https://github.com/clap-rs/clap |
| `clap_complete` | 4.6.2 | `Apache-2.0 OR MIT` | https://github.com/clap-rs/clap |
| `clap_derive` | 4.6.1 | `Apache-2.0 OR MIT` | https://github.com/clap-rs/clap |
| `clap_lex` | 1.1.0 | `Apache-2.0 OR MIT` | https://github.com/clap-rs/clap |
| `clap_mangen` | 0.2.33 | `Apache-2.0 OR MIT` | https://github.com/clap-rs/clap |
| `cmake` | 0.1.58 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/cmake-rs |
| `colorchoice` | 1.0.5 | `Apache-2.0 OR MIT` | https://github.com/rust-cli/anstyle.git |
| `combine` | 4.6.7 | `MIT` | https://github.com/Marwes/combine |
| `comfy-table` | 7.2.2 | `MIT` | https://github.com/nukesor/comfy-table |
| `compression-codecs` | 0.4.37 | `Apache-2.0 OR MIT` | https://github.com/Nullus157/async-compression |
| `compression-core` | 0.4.31 | `Apache-2.0 OR MIT` | https://github.com/Nullus157/async-compression |
| `concurrent-queue` | 2.5.0 | `Apache-2.0 OR MIT` | https://github.com/smol-rs/concurrent-queue |
| `config` | 0.15.22 | `Apache-2.0 OR MIT` | https://github.com/rust-cli/config-rs |
| `console` | 0.15.11 | `MIT` | https://github.com/console-rs/console |
| `console` | 0.16.3 | `MIT` | https://github.com/console-rs/console |
| `const-random` | 0.1.18 | `Apache-2.0 OR MIT` | https://github.com/tkaitchuck/constrandom |
| `const-random-macro` | 0.1.16 | `Apache-2.0 OR MIT` | https://github.com/tkaitchuck/constrandom |
| `constant_time_eq` | 0.4.2 | `Apache-2.0 OR CC0-1.0 OR MIT-0` | https://github.com/cesarb/constant_time_eq |
| `convert_case` | 0.6.0 | `MIT` | https://github.com/rutrum/convert-case |
| `core-foundation` | 0.9.4 | `Apache-2.0 OR MIT` | https://github.com/servo/core-foundation-rs |
| `core-foundation` | 0.10.1 | `Apache-2.0 OR MIT` | https://github.com/servo/core-foundation-rs |
| `core-foundation-sys` | 0.8.7 | `Apache-2.0 OR MIT` | https://github.com/servo/core-foundation-rs |
| `cpufeatures` | 0.2.17 | `Apache-2.0 OR MIT` | https://github.com/RustCrypto/utils |
| `cpufeatures` | 0.3.0 | `Apache-2.0 OR MIT` | https://github.com/RustCrypto/utils |
| `crc32fast` | 1.5.0 | `Apache-2.0 OR MIT` | https://github.com/srijs/rust-crc32fast |
| `crossbeam-channel` | 0.5.15 | `Apache-2.0 OR MIT` | https://github.com/crossbeam-rs/crossbeam |
| `crossbeam-deque` | 0.8.6 | `Apache-2.0 OR MIT` | https://github.com/crossbeam-rs/crossbeam |
| `crossbeam-epoch` | 0.9.18 | `Apache-2.0 OR MIT` | https://github.com/crossbeam-rs/crossbeam |
| `crossbeam-queue` | 0.3.12 | `Apache-2.0 OR MIT` | https://github.com/crossbeam-rs/crossbeam |
| `crossbeam-skiplist` | 0.1.3 | `Apache-2.0 OR MIT` | https://github.com/crossbeam-rs/crossbeam |
| `crossbeam-utils` | 0.8.21 | `Apache-2.0 OR MIT` | https://github.com/crossbeam-rs/crossbeam |
| `crunchy` | 0.2.4 | `MIT` | https://github.com/eira-fransham/crunchy |
| `crypto-common` | 0.1.7 | `Apache-2.0 OR MIT` | https://github.com/RustCrypto/traits |
| `csv` | 1.4.0 | `MIT OR Unlicense` | https://github.com/BurntSushi/rust-csv |
| `csv-core` | 0.1.13 | `MIT OR Unlicense` | https://github.com/BurntSushi/rust-csv |
| `darling` | 0.20.11 | `MIT` | https://github.com/TedDriggs/darling |
| `darling` | 0.23.0 | `MIT` | https://github.com/TedDriggs/darling |
| `darling_core` | 0.20.11 | `MIT` | https://github.com/TedDriggs/darling |
| `darling_core` | 0.23.0 | `MIT` | https://github.com/TedDriggs/darling |
| `darling_macro` | 0.20.11 | `MIT` | https://github.com/TedDriggs/darling |
| `darling_macro` | 0.23.0 | `MIT` | https://github.com/TedDriggs/darling |
| `dashmap` | 6.1.0 | `MIT` | https://github.com/xacrimon/dashmap |
| `datafusion` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-catalog` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-catalog-listing` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-common` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-common-runtime` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-datasource` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-datasource-arrow` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-datasource-csv` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-datasource-json` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-doc` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-execution` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-expr` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-expr-common` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-functions` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-functions-aggregate` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-functions-aggregate-common` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-functions-nested` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-functions-table` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-functions-window` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-functions-window-common` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-macros` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-optimizer` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-physical-expr` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-physical-expr-adapter` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-physical-expr-common` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-physical-optimizer` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-physical-plan` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-pruning` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-session` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datafusion-sql` | 52.5.0 | `Apache-2.0` | https://github.com/apache/datafusion |
| `datasketches` | 0.2.0 | `Apache-2.0` | https://github.com/apache/datasketches-rust |
| `deepsize` | 0.2.0 | `MIT` | https://github.com/Aeledfyr/deepsize/ |
| `deepsize_derive` | 0.1.2 | `MIT` | https://github.com/Aeledfyr/deepsize/ |
| `der` | 0.8.0 | `Apache-2.0 OR MIT` | https://github.com/RustCrypto/formats |
| `deranged` | 0.5.8 | `Apache-2.0 OR MIT` | https://github.com/jhpratt/deranged |
| `derive_arbitrary` | 1.4.2 | `Apache-2.0 OR MIT` | https://github.com/rust-fuzz/arbitrary |
| `derive_builder` | 0.20.2 | `Apache-2.0 OR MIT` | https://github.com/colin-kiegel/rust-derive-builder |
| `derive_builder_core` | 0.20.2 | `Apache-2.0 OR MIT` | https://github.com/colin-kiegel/rust-derive-builder |
| `derive_builder_macro` | 0.20.2 | `Apache-2.0 OR MIT` | https://github.com/colin-kiegel/rust-derive-builder |
| `digest` | 0.10.7 | `Apache-2.0 OR MIT` | https://github.com/RustCrypto/traits |
| `dirs` | 6.0.0 | `Apache-2.0 OR MIT` | https://github.com/soc/dirs-rs |
| `dirs-sys` | 0.5.0 | `Apache-2.0 OR MIT` | https://github.com/dirs-dev/dirs-sys-rs |
| `displaydoc` | 0.2.5 | `Apache-2.0 OR MIT` | https://github.com/yaahc/displaydoc |
| `dlv-list` | 0.5.2 | `Apache-2.0 OR MIT` | https://github.com/sgodwincs/dlv-list-rs |
| `downcast-rs` | 2.0.2 | `Apache-2.0 OR MIT` | https://github.com/marcianx/downcast-rs |
| `dunce` | 1.0.5 | `Apache-2.0 OR CC0-1.0 OR MIT-0` | https://gitlab.com/kornelski/dunce |
| `dyn-clone` | 1.0.20 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/dyn-clone |
| `either` | 1.15.0 | `Apache-2.0 OR MIT` | https://github.com/rayon-rs/either |
| `encode_unicode` | 1.0.0 | `Apache-2.0 OR MIT` | https://github.com/tormol/encode_unicode |
| `encoding_rs` | 0.8.35 | `(Apache-2.0 OR MIT) AND BSD-3-Clause` | https://github.com/hsivonen/encoding_rs |
| `equivalent` | 1.0.2 | `Apache-2.0 OR MIT` | https://github.com/indexmap-rs/equivalent |
| `erased-serde` | 0.4.10 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/erased-serde |
| `errno` | 0.3.14 | `Apache-2.0 OR MIT` | https://github.com/lambda-fairy/rust-errno |
| `esaxx-rs` | 0.1.10 | `Apache-2.0` | https://github.com/Narsil/esaxx-rs |
| `ethnum` | 1.5.3 | `Apache-2.0 OR MIT` | https://github.com/nlordell/ethnum-rs |
| `event-listener` | 5.4.1 | `Apache-2.0 OR MIT` | https://github.com/smol-rs/event-listener |
| `event-listener-strategy` | 0.5.4 | `Apache-2.0 OR MIT` | https://github.com/smol-rs/event-listener-strategy |
| `fallible-iterator` | 0.3.0 | `Apache-2.0 OR MIT` | https://github.com/sfackler/rust-fallible-iterator |
| `fallible-streaming-iterator` | 0.1.9 | `Apache-2.0 OR MIT` | https://github.com/sfackler/fallible-streaming-iterator |
| `fast-float2` | 0.2.3 | `Apache-2.0 OR MIT` | https://github.com/Alexhuszagh/fast-float-rust |
| `fastdivide` | 0.4.2 | `MIT OR zlib-acknowledgement` | https://github.com/fulmicoton/fastdivide |
| `fastrand` | 2.4.1 | `Apache-2.0 OR MIT` | https://github.com/smol-rs/fastrand |
| `find-msvc-tools` | 0.1.9 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/cc-rs |
| `fixedbitset` | 0.5.7 | `Apache-2.0 OR MIT` | https://github.com/petgraph/fixedbitset |
| `flatbuffers` | 25.12.19 | `Apache-2.0` | https://github.com/google/flatbuffers |
| `flate2` | 1.1.9 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/flate2-rs |
| `fnv` | 1.0.7 | `Apache-2.0 OR MIT` | https://github.com/servo/rust-fnv |
| `foldhash` | 0.1.5 | `Zlib` | https://github.com/orlp/foldhash |
| `foldhash` | 0.2.0 | `Zlib` | https://github.com/orlp/foldhash |
| `foreign-types` | 0.3.2 | `Apache-2.0 OR MIT` | https://github.com/sfackler/foreign-types |
| `foreign-types-shared` | 0.1.1 | `Apache-2.0 OR MIT` | https://github.com/sfackler/foreign-types |
| `form_urlencoded` | 1.2.2 | `Apache-2.0 OR MIT` | https://github.com/servo/rust-url |
| `fs2` | 0.4.3 | `Apache-2.0 OR MIT` | https://github.com/danburkert/fs2-rs |
| `fs4` | 0.8.4 | `Apache-2.0 OR MIT` | https://github.com/al8n/fs4-rs |
| `fs4` | 0.13.1 | `Apache-2.0 OR MIT` | https://github.com/al8n/fs4-rs |
| `fs_extra` | 1.3.0 | `MIT` | https://github.com/webdesus/fs_extra |
| `fsevent-sys` | 4.1.0 | `MIT` | https://github.com/octplane/fsevent-rust/tree/master/fsevent-sys |
| `fsst` | 4.0.0 | `Apache-2.0` | https://github.com/lance-format/lance |
| `fst` | 0.4.7 | `MIT OR Unlicense` | https://github.com/BurntSushi/fst |
| `funty` | 2.0.0 | `MIT` | https://github.com/myrrlyn/funty |
| `futures` | 0.3.32 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/futures-rs |
| `futures-channel` | 0.3.32 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/futures-rs |
| `futures-core` | 0.3.32 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/futures-rs |
| `futures-executor` | 0.3.32 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/futures-rs |
| `futures-io` | 0.3.32 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/futures-rs |
| `futures-macro` | 0.3.32 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/futures-rs |
| `futures-sink` | 0.3.32 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/futures-rs |
| `futures-task` | 0.3.32 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/futures-rs |
| `futures-util` | 0.3.32 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/futures-rs |
| `generator` | 0.8.8 | `Apache-2.0 OR MIT` | https://github.com/Xudong-Huang/generator-rs.git |
| `generic-array` | 0.14.7 | `MIT` | https://github.com/fizyk20/generic-array.git |
| `getrandom` | 0.2.17 | `Apache-2.0 OR MIT` | https://github.com/rust-random/getrandom |
| `getrandom` | 0.3.4 | `Apache-2.0 OR MIT` | https://github.com/rust-random/getrandom |
| `getrandom` | 0.4.2 | `Apache-2.0 OR MIT` | https://github.com/rust-random/getrandom |
| `glob` | 0.3.3 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/glob |
| `h2` | 0.4.13 | `MIT` | https://github.com/hyperium/h2 |
| `half` | 2.7.1 | `Apache-2.0 OR MIT` | https://github.com/VoidStarKat/half-rs |
| `hashbrown` | 0.12.3 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/hashbrown |
| `hashbrown` | 0.14.5 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/hashbrown |
| `hashbrown` | 0.15.5 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/hashbrown |
| `hashbrown` | 0.16.1 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/hashbrown |
| `hashbrown` | 0.17.0 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/hashbrown |
| `hashlink` | 0.9.1 | `Apache-2.0 OR MIT` | https://github.com/kyren/hashlink |
| `hashlink` | 0.10.0 | `Apache-2.0 OR MIT` | https://github.com/kyren/hashlink |
| `heck` | 0.5.0 | `Apache-2.0 OR MIT` | https://github.com/withoutboats/heck |
| `hermit-abi` | 0.5.2 | `Apache-2.0 OR MIT` | https://github.com/hermit-os/hermit-rs |
| `hex` | 0.4.3 | `Apache-2.0 OR MIT` | https://github.com/KokaKiwi/rust-hex |
| `hmac-sha256` | 1.1.14 | `ISC` | https://github.com/jedisct1/rust-hmac-sha256 |
| `htmlescape` | 0.3.1 | `Apache-2.0 OR MIT OR MPL-2.0` | https://github.com/veddan/rust-htmlescape |
| `http` | 1.4.0 | `Apache-2.0 OR MIT` | https://github.com/hyperium/http |
| `http-body` | 1.0.1 | `MIT` | https://github.com/hyperium/http-body |
| `http-body-util` | 0.1.3 | `MIT` | https://github.com/hyperium/http-body |
| `http-range-header` | 0.4.2 | `MIT` | https://github.com/MarcusGrass/parse-range-headers |
| `httparse` | 1.10.1 | `Apache-2.0 OR MIT` | https://github.com/seanmonstar/httparse |
| `httpdate` | 1.0.3 | `Apache-2.0 OR MIT` | https://github.com/pyfisch/httpdate |
| `humantime` | 2.3.0 | `Apache-2.0 OR MIT` | https://github.com/chronotope/humantime |
| `hyper` | 1.9.0 | `MIT` | https://github.com/hyperium/hyper |
| `hyper-rustls` | 0.27.9 | `Apache-2.0 OR ISC OR MIT` | https://github.com/rustls/hyper-rustls |
| `hyper-util` | 0.1.20 | `MIT` | https://github.com/hyperium/hyper-util |
| `hyperloglogplus` | 0.4.1 | `MIT` | https://github.com/tabac/hyperloglog.rs |
| `iana-time-zone` | 0.1.65 | `Apache-2.0 OR MIT` | https://github.com/strawlab/iana-time-zone |
| `iana-time-zone-haiku` | 0.1.2 | `Apache-2.0 OR MIT` | https://github.com/strawlab/iana-time-zone |
| `icu_collections` | 2.2.0 | `Unicode-3.0` | https://github.com/unicode-org/icu4x |
| `icu_locale_core` | 2.2.0 | `Unicode-3.0` | https://github.com/unicode-org/icu4x |
| `icu_normalizer` | 2.2.0 | `Unicode-3.0` | https://github.com/unicode-org/icu4x |
| `icu_normalizer_data` | 2.2.0 | `Unicode-3.0` | https://github.com/unicode-org/icu4x |
| `icu_properties` | 2.2.0 | `Unicode-3.0` | https://github.com/unicode-org/icu4x |
| `icu_properties_data` | 2.2.0 | `Unicode-3.0` | https://github.com/unicode-org/icu4x |
| `icu_provider` | 2.2.0 | `Unicode-3.0` | https://github.com/unicode-org/icu4x |
| `id-arena` | 2.3.0 | `Apache-2.0 OR MIT` | https://github.com/fitzgen/id-arena |
| `ident_case` | 1.0.1 | `Apache-2.0 OR MIT` | https://github.com/TedDriggs/ident_case |
| `idna` | 1.1.0 | `Apache-2.0 OR MIT` | https://github.com/servo/rust-url/ |
| `idna_adapter` | 1.2.1 | `Apache-2.0 OR MIT` | https://github.com/hsivonen/idna_adapter |
| `indexmap` | 1.9.3 | `Apache-2.0 OR MIT` | https://github.com/bluss/indexmap |
| `indexmap` | 2.14.0 | `Apache-2.0 OR MIT` | https://github.com/indexmap-rs/indexmap |
| `indicatif` | 0.17.11 | `MIT` | https://github.com/console-rs/indicatif |
| `indicatif` | 0.18.4 | `MIT` | https://github.com/console-rs/indicatif |
| `inotify` | 0.11.1 | `ISC` | https://github.com/hannobraun/inotify |
| `inotify-sys` | 0.1.5 | `ISC` | https://github.com/hannobraun/inotify-sys |
| `inventory` | 0.3.24 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/inventory |
| `ipnet` | 2.12.0 | `Apache-2.0 OR MIT` | https://github.com/krisprice/ipnet |
| `iri-string` | 0.7.12 | `Apache-2.0 OR MIT` | https://github.com/lo48576/iri-string |
| `is_terminal_polyfill` | 1.70.2 | `Apache-2.0 OR MIT` | https://github.com/polyfill-rs/is_terminal_polyfill |
| `itertools` | 0.11.0 | `Apache-2.0 OR MIT` | https://github.com/rust-itertools/itertools |
| `itertools` | 0.12.1 | `Apache-2.0 OR MIT` | https://github.com/rust-itertools/itertools |
| `itertools` | 0.13.0 | `Apache-2.0 OR MIT` | https://github.com/rust-itertools/itertools |
| `itertools` | 0.14.0 | `Apache-2.0 OR MIT` | https://github.com/rust-itertools/itertools |
| `itoa` | 1.0.18 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/itoa |
| `jiff` | 0.2.24 | `MIT OR Unlicense` | https://github.com/BurntSushi/jiff |
| `jiff-static` | 0.2.24 | `MIT OR Unlicense` | https://github.com/BurntSushi/jiff |
| `jiff-tzdb` | 0.1.6 | `MIT OR Unlicense` | https://github.com/BurntSushi/jiff |
| `jiff-tzdb-platform` | 0.1.3 | `MIT OR Unlicense` | https://github.com/BurntSushi/jiff |
| `jni` | 0.21.1 | `Apache-2.0 OR MIT` | https://github.com/jni-rs/jni-rs |
| `jni-sys` | 0.3.1 | `Apache-2.0 OR MIT` | https://github.com/jni-rs/jni-sys |
| `jni-sys` | 0.4.1 | `Apache-2.0 OR MIT` | https://github.com/jni-rs/jni-sys |
| `jni-sys-macros` | 0.4.1 | `Apache-2.0 OR MIT` | https://github.com/jni-rs/jni-sys |
| `jobserver` | 0.1.34 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/jobserver-rs |
| `js-sys` | 0.3.95 | `Apache-2.0 OR MIT` | https://github.com/wasm-bindgen/wasm-bindgen/tree/master/crates/js-sys |
| `json5` | 0.4.1 | `ISC` | https://github.com/callum-oakley/json5-rs |
| `jsonb` | 0.5.6 | `Apache-2.0` | https://github.com/databendlabs/jsonb |
| `kqueue` | 1.1.1 | `MIT` | https://gitlab.com/rust-kqueue/rust-kqueue |
| `kqueue-sys` | 1.0.4 | `MIT` | https://gitlab.com/rust-kqueue/rust-kqueue-sys |
| `lance` | 4.0.0 | `Apache-2.0` | https://github.com/lance-format/lance |
| `lance-arrow` | 4.0.0 | `Apache-2.0` | https://github.com/lance-format/lance |
| `lance-bitpacking` | 4.0.0 | `Apache-2.0` | https://github.com/lance-format/lance |
| `lance-core` | 4.0.0 | `Apache-2.0` | https://github.com/lance-format/lance |
| `lance-datafusion` | 4.0.0 | `Apache-2.0` | https://github.com/lance-format/lance |
| `lance-datagen` | 4.0.0 | `Apache-2.0` | https://github.com/lance-format/lance |
| `lance-encoding` | 4.0.0 | `Apache-2.0` | https://github.com/lance-format/lance |
| `lance-file` | 4.0.0 | `Apache-2.0` | https://github.com/lance-format/lance |
| `lance-index` | 4.0.0 | `Apache-2.0` | https://github.com/lance-format/lance |
| `lance-io` | 4.0.0 | `Apache-2.0` | https://github.com/lance-format/lance |
| `lance-linalg` | 4.0.0 | `Apache-2.0` | https://github.com/lance-format/lance |
| `lance-namespace` | 4.0.0 | `Apache-2.0` | https://github.com/lance-format/lance |
| `lance-namespace-impls` | 4.0.0 | `Apache-2.0` | https://github.com/lance-format/lance |
| `lance-namespace-reqwest-client` | 0.6.1 | `Apache-2.0` | — |
| `lance-table` | 4.0.0 | `Apache-2.0` | https://github.com/lance-format/lance |
| `lance-testing` | 4.0.0 | `Apache-2.0` | https://github.com/lance-format/lance |
| `lancedb` | 0.27.2 | `Apache-2.0` | https://github.com/lancedb/lancedb |
| `lazy_static` | 0.2.11 | `Apache-2.0 OR MIT` | https://github.com/rust-lang-nursery/lazy-static.rs |
| `lazy_static` | 1.5.0 | `Apache-2.0 OR MIT` | https://github.com/rust-lang-nursery/lazy-static.rs |
| `leb128fmt` | 0.1.0 | `Apache-2.0 OR MIT` | https://github.com/bluk/leb128fmt |
| `levenshtein_automata` | 0.2.1 | `MIT` | https://github.com/tantivy-search/levenshtein-automata |
| `lexical-core` | 1.0.6 | `Apache-2.0 OR MIT` | https://github.com/Alexhuszagh/rust-lexical |
| `lexical-parse-float` | 1.0.6 | `Apache-2.0 OR MIT` | https://github.com/Alexhuszagh/rust-lexical |
| `lexical-parse-integer` | 1.0.6 | `Apache-2.0 OR MIT` | https://github.com/Alexhuszagh/rust-lexical |
| `lexical-util` | 1.0.7 | `Apache-2.0 OR MIT` | https://github.com/Alexhuszagh/rust-lexical |
| `lexical-write-float` | 1.0.6 | `Apache-2.0 OR MIT` | https://github.com/Alexhuszagh/rust-lexical |
| `lexical-write-integer` | 1.0.6 | `Apache-2.0 OR MIT` | https://github.com/Alexhuszagh/rust-lexical |
| `libc` | 0.2.186 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/libc |
| `libm` | 0.2.16 | `MIT` | https://github.com/rust-lang/compiler-builtins |
| `libredox` | 0.1.16 | `MIT` | https://gitlab.redox-os.org/redox-os/libredox.git |
| `libsqlite3-sys` | 0.30.1 | `MIT` | https://github.com/rusqlite/rusqlite |
| `linux-raw-sys` | 0.4.15 | `Apache-2.0 OR Apache-2.0 WITH LLVM-exception OR MIT` | https://github.com/sunfishcode/linux-raw-sys |
| `linux-raw-sys` | 0.12.1 | `Apache-2.0 OR Apache-2.0 WITH LLVM-exception OR MIT` | https://github.com/sunfishcode/linux-raw-sys |
| `litemap` | 0.8.2 | `Unicode-3.0` | https://github.com/unicode-org/icu4x |
| `lock_api` | 0.4.14 | `Apache-2.0 OR MIT` | https://github.com/Amanieu/parking_lot |
| `log` | 0.4.29 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/log |
| `loom` | 0.7.2 | `MIT` | https://github.com/tokio-rs/loom |
| `lru` | 0.12.5 | `MIT` | https://github.com/jeromefroe/lru-rs.git |
| `lru` | 0.16.4 | `MIT` | https://github.com/jeromefroe/lru-rs.git |
| `lru` | 0.17.0 | `MIT` | https://github.com/jeromefroe/lru-rs.git |
| `lru-slab` | 0.1.2 | `Apache-2.0 OR MIT OR Zlib` | https://github.com/Ralith/lru-slab |
| `lz4` | 1.28.1 | `MIT` | https://github.com/10xGenomics/lz4-rs |
| `lz4-sys` | 1.11.1+lz4-1.10.0 | `MIT` | https://github.com/10xGenomics/lz4-rs |
| `lz4_flex` | 0.11.6 | `MIT` | https://github.com/pseitz/lz4_flex |
| `lz4_flex` | 0.12.1 | `MIT` | https://github.com/pseitz/lz4_flex |
| `lz4_flex` | 0.13.1 | `MIT` | https://github.com/pseitz/lz4_flex |
| `lzma-rust2` | 0.15.7 | `Apache-2.0` | https://github.com/hasenbanck/lzma-rust2/ |
| `macro_rules_attribute` | 0.2.2 | `Apache-2.0 OR MIT OR Zlib` | https://github.com/danielhenrymantilla/macro_rules_attribute-rs |
| `macro_rules_attribute-proc_macro` | 0.2.2 | `Apache-2.0 OR MIT OR Zlib` | https://github.com/danielhenrymantilla/macro_rules_attribute-rs |
| `matchers` | 0.2.0 | `MIT` | https://github.com/hawkw/matchers |
| `matchit` | 0.7.3 | `BSD-3-Clause AND MIT` | https://github.com/ibraheemdev/matchit |
| `matrixmultiply` | 0.3.10 | `Apache-2.0 OR MIT` | https://github.com/bluss/matrixmultiply/ |
| `md-5` | 0.10.6 | `Apache-2.0 OR MIT` | https://github.com/RustCrypto/hashes |
| `measure_time` | 0.9.0 | `MIT` | https://github.com/PSeitz/rust_measure_time |
| `memchr` | 2.8.0 | `MIT OR Unlicense` | https://github.com/BurntSushi/memchr |
| `memmap2` | 0.9.10 | `Apache-2.0 OR MIT` | https://github.com/RazrFalcon/memmap2-rs |
| `metrics` | 0.22.4 | `MIT` | https://github.com/metrics-rs/metrics |
| `mime` | 0.3.17 | `Apache-2.0 OR MIT` | https://github.com/hyperium/mime |
| `mime_guess` | 2.0.5 | `MIT` | https://github.com/abonander/mime_guess |
| `minimal-lexical` | 0.2.1 | `Apache-2.0 OR MIT` | https://github.com/Alexhuszagh/minimal-lexical |
| `miniz_oxide` | 0.8.9 | `Apache-2.0 OR MIT OR Zlib` | https://github.com/Frommi/miniz_oxide/tree/master/miniz_oxide |
| `mio` | 1.2.0 | `MIT` | https://github.com/tokio-rs/mio |
| `mock_instant` | 0.6.0 | `0BSD` | https://github.com/museun/mock_instant |
| `moka` | 0.12.15 | `(Apache-2.0 OR MIT) AND Apache-2.0` | https://github.com/moka-rs/moka |
| `monostate` | 0.1.18 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/monostate |
| `monostate-impl` | 0.1.18 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/monostate |
| `multimap` | 0.10.1 | `Apache-2.0 OR MIT` | https://github.com/havarnov/multimap |
| `murmurhash32` | 0.3.1 | `MIT` | https://github.com/quickwit-inc/murmurhash32 |
| `native-tls` | 0.2.18 | `Apache-2.0 OR MIT` | https://github.com/rust-native-tls/rust-native-tls |
| `ndarray` | 0.16.1 | `Apache-2.0 OR MIT` | https://github.com/rust-ndarray/ndarray |
| `ndarray` | 0.17.2 | `Apache-2.0 OR MIT` | https://github.com/rust-ndarray/ndarray |
| `nom` | 7.1.3 | `MIT` | https://github.com/Geal/nom |
| `nom` | 8.0.0 | `MIT` | https://github.com/rust-bakery/nom |
| `notify` | 8.2.0 | `CC0-1.0` | https://github.com/notify-rs/notify.git |
| `notify-types` | 2.1.0 | `Apache-2.0 OR MIT` | https://github.com/notify-rs/notify.git |
| `ntapi` | 0.4.3 | `Apache-2.0 OR MIT` | https://github.com/MSxDOS/ntapi |
| `nu-ansi-term` | 0.50.3 | `MIT` | https://github.com/nushell/nu-ansi-term |
| `num-bigint` | 0.4.6 | `Apache-2.0 OR MIT` | https://github.com/rust-num/num-bigint |
| `num-complex` | 0.4.6 | `Apache-2.0 OR MIT` | https://github.com/rust-num/num-complex |
| `num-conv` | 0.2.1 | `Apache-2.0 OR MIT` | https://github.com/jhpratt/num-conv |
| `num-integer` | 0.1.46 | `Apache-2.0 OR MIT` | https://github.com/rust-num/num-integer |
| `num-traits` | 0.2.19 | `Apache-2.0 OR MIT` | https://github.com/rust-num/num-traits |
| `num_cpus` | 1.17.0 | `Apache-2.0 OR MIT` | https://github.com/seanmonstar/num_cpus |
| `number_prefix` | 0.4.0 | `MIT` | https://github.com/ogham/rust-number-prefix |
| `object_store` | 0.12.5 | `Apache-2.0 OR MIT` | https://github.com/apache/arrow-rs-object-store |
| `once_cell` | 1.21.4 | `Apache-2.0 OR MIT` | https://github.com/matklad/once_cell |
| `once_cell_polyfill` | 1.70.2 | `Apache-2.0 OR MIT` | https://github.com/polyfill-rs/once_cell_polyfill |
| `oneshot` | 0.1.13 | `Apache-2.0 OR MIT` | https://github.com/faern/oneshot |
| `onig` | 6.5.1 | `MIT` | https://github.com/iwillspeak/rust-onig |
| `onig_sys` | 69.9.1 | `MIT` | https://github.com/iwillspeak/rust-onig |
| `openssl` | 0.10.78 | `Apache-2.0` | https://github.com/rust-openssl/rust-openssl |
| `openssl-macros` | 0.1.1 | `Apache-2.0 OR MIT` | — |
| `openssl-probe` | 0.2.1 | `Apache-2.0 OR MIT` | https://github.com/rustls/openssl-probe |
| `openssl-sys` | 0.9.114 | `MIT` | https://github.com/rust-openssl/rust-openssl |
| `option-ext` | 0.2.0 | `MPL-2.0` | https://github.com/soc/option-ext.git |
| `ordered-float` | 5.3.0 | `MIT` | https://github.com/reem/rust-ordered-float |
| `ordered-multimap` | 0.7.3 | `MIT` | https://github.com/sgodwincs/ordered-multimap-rs |
| `ort` | 2.0.0-rc.12 | `Apache-2.0 OR MIT` | https://github.com/pykeio/ort |
| `ort-sys` | 2.0.0-rc.12 | `Apache-2.0 OR MIT` | https://github.com/pykeio/ort |
| `ownedbytes` | 0.9.0 | `MIT` | https://github.com/quickwit-oss/tantivy |
| `parking` | 2.2.1 | `Apache-2.0 OR MIT` | https://github.com/smol-rs/parking |
| `parking_lot` | 0.12.5 | `Apache-2.0 OR MIT` | https://github.com/Amanieu/parking_lot |
| `parking_lot_core` | 0.9.12 | `Apache-2.0 OR MIT` | https://github.com/Amanieu/parking_lot |
| `paste` | 1.0.15 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/paste |
| `path-clean` | 1.0.1 | `Apache-2.0 OR MIT` | https://github.com/danreeves/path-clean |
| `path_abs` | 0.5.1 | `Apache-2.0 OR MIT` | https://github.com/vitiral/path_abs |
| `pathdiff` | 0.2.3 | `Apache-2.0 OR MIT` | https://github.com/Manishearth/pathdiff |
| `pem-rfc7468` | 1.0.0 | `Apache-2.0 OR MIT` | https://github.com/RustCrypto/formats |
| `percent-encoding` | 2.3.2 | `Apache-2.0 OR MIT` | https://github.com/servo/rust-url/ |
| `permutation` | 0.4.1 | `Apache-2.0 OR MIT` | https://github.com/jeremysalwen/rust-permutations |
| `pest` | 2.8.6 | `Apache-2.0 OR MIT` | https://github.com/pest-parser/pest |
| `pest_derive` | 2.8.6 | `Apache-2.0 OR MIT` | https://github.com/pest-parser/pest |
| `pest_generator` | 2.8.6 | `Apache-2.0 OR MIT` | https://github.com/pest-parser/pest |
| `pest_meta` | 2.8.6 | `Apache-2.0 OR MIT` | https://github.com/pest-parser/pest |
| `petgraph` | 0.8.3 | `Apache-2.0 OR MIT` | https://github.com/petgraph/petgraph |
| `phf` | 0.12.1 | `MIT` | https://github.com/rust-phf/rust-phf |
| `phf_shared` | 0.12.1 | `MIT` | https://github.com/rust-phf/rust-phf |
| `pin-project` | 1.1.11 | `Apache-2.0 OR MIT` | https://github.com/taiki-e/pin-project |
| `pin-project-internal` | 1.1.11 | `Apache-2.0 OR MIT` | https://github.com/taiki-e/pin-project |
| `pin-project-lite` | 0.2.17 | `Apache-2.0 OR MIT` | https://github.com/taiki-e/pin-project-lite |
| `pkg-config` | 0.3.33 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/pkg-config-rs |
| `portable-atomic` | 1.13.1 | `Apache-2.0 OR MIT` | https://github.com/taiki-e/portable-atomic |
| `portable-atomic-util` | 0.2.7 | `Apache-2.0 OR MIT` | https://github.com/taiki-e/portable-atomic-util |
| `potential_utf` | 0.1.5 | `Unicode-3.0` | https://github.com/unicode-org/icu4x |
| `powerfmt` | 0.2.0 | `Apache-2.0 OR MIT` | https://github.com/jhpratt/powerfmt |
| `ppv-lite86` | 0.2.21 | `Apache-2.0 OR MIT` | https://github.com/cryptocorrosion/cryptocorrosion |
| `prettyplease` | 0.2.37 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/prettyplease |
| `proc-macro2` | 1.0.106 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/proc-macro2 |
| `prost` | 0.14.3 | `Apache-2.0` | https://github.com/tokio-rs/prost |
| `prost-build` | 0.14.3 | `Apache-2.0` | https://github.com/tokio-rs/prost |
| `prost-derive` | 0.14.3 | `Apache-2.0` | https://github.com/tokio-rs/prost |
| `prost-types` | 0.14.3 | `Apache-2.0` | https://github.com/tokio-rs/prost |
| `quinn` | 0.11.9 | `Apache-2.0 OR MIT` | https://github.com/quinn-rs/quinn |
| `quinn-proto` | 0.11.14 | `Apache-2.0 OR MIT` | https://github.com/quinn-rs/quinn |
| `quinn-udp` | 0.5.14 | `Apache-2.0 OR MIT` | https://github.com/quinn-rs/quinn |
| `quote` | 1.0.45 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/quote |
| `r-efi` | 5.3.0 | `Apache-2.0 OR LGPL-2.1-or-later OR MIT` | https://github.com/r-efi/r-efi |
| `r-efi` | 6.0.0 | `Apache-2.0 OR LGPL-2.1-or-later OR MIT` | https://github.com/r-efi/r-efi |
| `radium` | 0.7.0 | `MIT` | https://github.com/bitvecto-rs/radium |
| `rand` | 0.8.6 | `Apache-2.0 OR MIT` | https://github.com/rust-random/rand |
| `rand` | 0.9.4 | `Apache-2.0 OR MIT` | https://github.com/rust-random/rand |
| `rand` | 0.10.1 | `Apache-2.0 OR MIT` | https://github.com/rust-random/rand |
| `rand_chacha` | 0.3.1 | `Apache-2.0 OR MIT` | https://github.com/rust-random/rand |
| `rand_chacha` | 0.9.0 | `Apache-2.0 OR MIT` | https://github.com/rust-random/rand |
| `rand_core` | 0.6.4 | `Apache-2.0 OR MIT` | https://github.com/rust-random/rand |
| `rand_core` | 0.9.5 | `Apache-2.0 OR MIT` | https://github.com/rust-random/rand |
| `rand_core` | 0.10.1 | `Apache-2.0 OR MIT` | https://github.com/rust-random/rand_core |
| `rand_distr` | 0.4.3 | `Apache-2.0 OR MIT` | https://github.com/rust-random/rand |
| `rand_distr` | 0.5.1 | `Apache-2.0 OR MIT` | https://github.com/rust-random/rand_distr |
| `rand_xoshiro` | 0.7.0 | `Apache-2.0 OR MIT` | https://github.com/rust-random/rngs |
| `random_word` | 0.5.2 | `MIT` | https://github.com/MitchellRhysHall/random_word |
| `rangemap` | 1.7.1 | `Apache-2.0 OR MIT` | https://github.com/jeffparsons/rangemap |
| `rawpointer` | 0.2.1 | `Apache-2.0 OR MIT` | https://github.com/bluss/rawpointer/ |
| `rayon` | 1.12.0 | `Apache-2.0 OR MIT` | https://github.com/rayon-rs/rayon |
| `rayon-cond` | 0.3.0 | `Apache-2.0 OR MIT` | https://github.com/cuviper/rayon-cond |
| `rayon-core` | 1.13.0 | `Apache-2.0 OR MIT` | https://github.com/rayon-rs/rayon |
| `redox_syscall` | 0.5.18 | `MIT` | https://gitlab.redox-os.org/redox-os/syscall |
| `redox_users` | 0.5.2 | `MIT` | https://gitlab.redox-os.org/redox-os/users |
| `ref-cast` | 1.0.25 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/ref-cast |
| `ref-cast-impl` | 1.0.25 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/ref-cast |
| `regex` | 1.12.3 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/regex |
| `regex-automata` | 0.4.14 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/regex |
| `regex-syntax` | 0.8.10 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/regex |
| `reqwest` | 0.12.28 | `Apache-2.0 OR MIT` | https://github.com/seanmonstar/reqwest |
| `reqwest` | 0.13.2 | `Apache-2.0 OR MIT` | https://github.com/seanmonstar/reqwest |
| `ring` | 0.17.14 | `Apache-2.0 AND ISC` | https://github.com/briansmith/ring |
| `roaring` | 0.11.3 | `Apache-2.0 OR MIT` | https://github.com/RoaringBitmap/roaring-rs |
| `roff` | 1.1.1 | `Apache-2.0 OR MIT` | https://github.com/rust-cli/roff-rs |
| `ron` | 0.12.1 | `Apache-2.0 OR MIT` | https://github.com/ron-rs/ron |
| `rusqlite` | 0.32.1 | `MIT` | https://github.com/rusqlite/rusqlite |
| `rust-embed` | 8.11.0 | `MIT` | https://pyrossh.dev/repos/rust-embed |
| `rust-embed-impl` | 8.11.0 | `MIT` | https://pyrossh.dev/repos/rust-embed |
| `rust-embed-utils` | 8.11.0 | `MIT` | https://pyrossh.dev/repos/rust-embed |
| `rust-ini` | 0.21.3 | `MIT` | https://github.com/zonyitoo/rust-ini |
| `rust-stemmers` | 1.2.0 | `BSD-3-Clause OR MIT` | https://github.com/CurrySoftware/rust-stemmers |
| `rustc-hash` | 2.1.2 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/rustc-hash |
| `rustc_version` | 0.4.1 | `Apache-2.0 OR MIT` | https://github.com/djc/rustc-version-rs |
| `rustix` | 0.38.44 | `Apache-2.0 OR Apache-2.0 WITH LLVM-exception OR MIT` | https://github.com/bytecodealliance/rustix |
| `rustix` | 1.1.4 | `Apache-2.0 OR Apache-2.0 WITH LLVM-exception OR MIT` | https://github.com/bytecodealliance/rustix |
| `rustls` | 0.23.39 | `Apache-2.0 OR ISC OR MIT` | https://github.com/rustls/rustls |
| `rustls-native-certs` | 0.8.3 | `Apache-2.0 OR ISC OR MIT` | https://github.com/rustls/rustls-native-certs |
| `rustls-pki-types` | 1.14.0 | `Apache-2.0 OR MIT` | https://github.com/rustls/pki-types |
| `rustls-platform-verifier` | 0.6.2 | `Apache-2.0 OR MIT` | https://github.com/rustls/rustls-platform-verifier |
| `rustls-platform-verifier-android` | 0.1.1 | `Apache-2.0 OR MIT` | https://github.com/rustls/rustls-platform-verifier |
| `rustls-webpki` | 0.103.13 | `ISC` | https://github.com/rustls/webpki |
| `rustversion` | 1.0.22 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/rustversion |
| `ryu` | 1.0.23 | `Apache-2.0 OR BSL-1.0` | https://github.com/dtolnay/ryu |
| `same-file` | 1.0.6 | `MIT OR Unlicense` | https://github.com/BurntSushi/same-file |
| `schannel` | 0.1.29 | `MIT` | https://github.com/steffengy/schannel-rs |
| `schemars` | 0.9.0 | `MIT` | https://github.com/GREsau/schemars |
| `schemars` | 1.2.1 | `MIT` | https://github.com/GREsau/schemars |
| `scoped-tls` | 1.0.1 | `Apache-2.0 OR MIT` | https://github.com/alexcrichton/scoped-tls |
| `scopeguard` | 1.2.0 | `Apache-2.0 OR MIT` | https://github.com/bluss/scopeguard |
| `security-framework` | 3.7.0 | `Apache-2.0 OR MIT` | https://github.com/kornelski/rust-security-framework |
| `security-framework-sys` | 2.17.0 | `Apache-2.0 OR MIT` | https://github.com/kornelski/rust-security-framework |
| `semver` | 1.0.28 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/semver |
| `seq-macro` | 0.3.6 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/seq-macro |
| `serde` | 1.0.228 | `Apache-2.0 OR MIT` | https://github.com/serde-rs/serde |
| `serde-untagged` | 0.1.9 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/serde-untagged |
| `serde_core` | 1.0.228 | `Apache-2.0 OR MIT` | https://github.com/serde-rs/serde |
| `serde_derive` | 1.0.228 | `Apache-2.0 OR MIT` | https://github.com/serde-rs/serde |
| `serde_json` | 1.0.149 | `Apache-2.0 OR MIT` | https://github.com/serde-rs/json |
| `serde_path_to_error` | 0.1.20 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/path-to-error |
| `serde_repr` | 0.1.20 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/serde-repr |
| `serde_spanned` | 0.6.9 | `Apache-2.0 OR MIT` | https://github.com/toml-rs/toml |
| `serde_spanned` | 1.1.1 | `Apache-2.0 OR MIT` | https://github.com/toml-rs/toml |
| `serde_urlencoded` | 0.7.1 | `Apache-2.0 OR MIT` | https://github.com/nox/serde_urlencoded |
| `serde_with` | 3.18.0 | `Apache-2.0 OR MIT` | https://github.com/jonasbb/serde_with/ |
| `serde_with_macros` | 3.18.0 | `Apache-2.0 OR MIT` | https://github.com/jonasbb/serde_with/ |
| `sha2` | 0.10.9 | `Apache-2.0 OR MIT` | https://github.com/RustCrypto/hashes |
| `sharded-slab` | 0.1.7 | `MIT` | https://github.com/hawkw/sharded-slab |
| `shlex` | 1.3.0 | `Apache-2.0 OR MIT` | https://github.com/comex/rust-shlex |
| `signal-hook-registry` | 1.4.8 | `Apache-2.0 OR MIT` | https://github.com/vorner/signal-hook |
| `simd-adler32` | 0.3.9 | `MIT` | https://github.com/mcountryman/simd-adler32 |
| `simdutf8` | 0.1.5 | `Apache-2.0 OR MIT` | https://github.com/rusticstuff/simdutf8 |
| `siphasher` | 1.0.2 | `Apache-2.0 OR MIT` | https://github.com/jedisct1/rust-siphash |
| `sketches-ddsketch` | 0.3.1 | `Apache-2.0` | https://github.com/mheffner/rust-sketches-ddsketch |
| `sketches-ddsketch` | 0.4.0 | `Apache-2.0` | https://github.com/mheffner/rust-sketches-ddsketch |
| `sku-search` | 0.2.3 | `NO-LICENSE` | — |
| `slab` | 0.4.12 | `MIT` | https://github.com/tokio-rs/slab |
| `smallvec` | 1.15.1 | `Apache-2.0 OR MIT` | https://github.com/servo/rust-smallvec |
| `snafu` | 0.8.9 | `Apache-2.0 OR MIT` | https://github.com/shepmaster/snafu |
| `snafu` | 0.9.0 | `Apache-2.0 OR MIT` | https://github.com/shepmaster/snafu |
| `snafu-derive` | 0.8.9 | `Apache-2.0 OR MIT` | https://github.com/shepmaster/snafu |
| `snafu-derive` | 0.9.0 | `Apache-2.0 OR MIT` | https://github.com/shepmaster/snafu |
| `socket2` | 0.6.3 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/socket2 |
| `socks` | 0.3.4 | `Apache-2.0 OR MIT` | https://github.com/sfackler/rust-socks |
| `spm_precompiled` | 0.1.4 | `Apache-2.0` | https://github.com/huggingface/spm_precompiled |
| `sqlparser` | 0.59.0 | `Apache-2.0` | https://github.com/apache/datafusion-sqlparser-rs |
| `sqlparser_derive` | 0.3.0 | `Apache-2.0` | https://github.com/sqlparser-rs/sqlparser-rs |
| `stable_deref_trait` | 1.2.1 | `Apache-2.0 OR MIT` | https://github.com/storyyeller/stable_deref_trait |
| `std_prelude` | 0.2.12 | `MIT` | https://github.com/vitiral/std_prelude |
| `stfu8` | 0.2.7 | `Apache-2.0 OR MIT` | https://github.com/vitiral/stfu8 |
| `strsim` | 0.11.1 | `MIT` | https://github.com/rapidfuzz/strsim-rs |
| `strum` | 0.26.3 | `MIT` | https://github.com/Peternator7/strum |
| `strum_macros` | 0.26.4 | `MIT` | https://github.com/Peternator7/strum |
| `subtle` | 2.6.1 | `BSD-3-Clause` | https://github.com/dalek-cryptography/subtle |
| `symlink` | 0.1.0 | `Apache-2.0 OR MIT` | https://gitlab.com/chris-morgan/symlink |
| `syn` | 1.0.109 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/syn |
| `syn` | 2.0.117 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/syn |
| `syn` | 3.0.3 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/syn |
| `sync_wrapper` | 1.0.2 | `Apache-2.0` | https://github.com/Actyx/sync_wrapper |
| `synstructure` | 0.13.2 | `MIT` | https://github.com/mystor/synstructure |
| `sysinfo` | 0.32.1 | `MIT` | https://github.com/GuillaumeGomez/sysinfo |
| `system-configuration` | 0.7.0 | `Apache-2.0 OR MIT` | https://github.com/mullvad/system-configuration-rs |
| `system-configuration-sys` | 0.6.0 | `Apache-2.0 OR MIT` | https://github.com/mullvad/system-configuration-rs |
| `tagptr` | 0.2.0 | `Apache-2.0 OR MIT` | https://github.com/oliver-giersch/tagptr.git |
| `tantivy` | 0.24.2 | `MIT` | https://github.com/quickwit-oss/tantivy |
| `tantivy` | 0.26.1 | `MIT` | https://github.com/quickwit-oss/tantivy |
| `tantivy-bitpacker` | 0.8.0 | `MIT` | https://github.com/quickwit-oss/tantivy |
| `tantivy-bitpacker` | 0.10.0 | `MIT` | https://github.com/quickwit-oss/tantivy |
| `tantivy-columnar` | 0.5.0 | `MIT` | https://github.com/quickwit-oss/tantivy |
| `tantivy-columnar` | 0.7.0 | `MIT` | https://github.com/quickwit-oss/tantivy |
| `tantivy-common` | 0.9.0 | `MIT` | https://github.com/quickwit-oss/tantivy |
| `tantivy-common` | 0.11.0 | `MIT` | https://github.com/quickwit-oss/tantivy |
| `tantivy-fst` | 0.5.0 | `MIT OR Unlicense` | https://github.com/quickwit-inc/fst |
| `tantivy-query-grammar` | 0.24.0 | `MIT` | https://github.com/quickwit-oss/tantivy |
| `tantivy-query-grammar` | 0.26.0 | `MIT` | https://github.com/quickwit-oss/tantivy |
| `tantivy-sstable` | 0.5.0 | `MIT` | https://github.com/quickwit-oss/tantivy |
| `tantivy-sstable` | 0.7.0 | `MIT` | https://github.com/quickwit-oss/tantivy |
| `tantivy-stacker` | 0.5.0 | `MIT` | https://github.com/quickwit-oss/tantivy |
| `tantivy-stacker` | 0.7.0 | `MIT` | https://github.com/quickwit-oss/tantivy |
| `tantivy-tokenizer-api` | 0.5.0 | `MIT` | https://github.com/quickwit-oss/tantivy |
| `tantivy-tokenizer-api` | 0.7.0 | `MIT` | https://github.com/quickwit-oss/tantivy |
| `tap` | 1.0.1 | `MIT` | https://github.com/myrrlyn/tap |
| `tempfile` | 3.27.0 | `Apache-2.0 OR MIT` | https://github.com/Stebalien/tempfile |
| `thiserror` | 1.0.69 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/thiserror |
| `thiserror` | 2.0.18 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/thiserror |
| `thiserror-impl` | 1.0.69 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/thiserror |
| `thiserror-impl` | 2.0.18 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/thiserror |
| `thread-tree` | 0.3.3 | `Apache-2.0 OR MIT` | https://github.com/bluss/thread-tree |
| `thread_local` | 1.1.9 | `Apache-2.0 OR MIT` | https://github.com/Amanieu/thread_local-rs |
| `time` | 0.3.47 | `Apache-2.0 OR MIT` | https://github.com/time-rs/time |
| `time-core` | 0.1.8 | `Apache-2.0 OR MIT` | https://github.com/time-rs/time |
| `time-macros` | 0.2.27 | `Apache-2.0 OR MIT` | https://github.com/time-rs/time |
| `tiny-keccak` | 2.0.2 | `CC0-1.0` | — |
| `tinystr` | 0.8.3 | `Unicode-3.0` | https://github.com/unicode-org/icu4x |
| `tinyvec` | 1.11.0 | `Apache-2.0 OR MIT OR Zlib` | https://github.com/Lokathor/tinyvec |
| `tinyvec_macros` | 0.1.1 | `Apache-2.0 OR MIT OR Zlib` | https://github.com/Soveu/tinyvec_macros |
| `tokenizers` | 0.19.1 | `Apache-2.0` | https://github.com/huggingface/tokenizers |
| `tokio` | 1.52.1 | `MIT` | https://github.com/tokio-rs/tokio |
| `tokio-macros` | 2.7.0 | `MIT` | https://github.com/tokio-rs/tokio |
| `tokio-rustls` | 0.26.4 | `Apache-2.0 OR MIT` | https://github.com/rustls/tokio-rustls |
| `tokio-stream` | 0.1.18 | `MIT` | https://github.com/tokio-rs/tokio |
| `tokio-util` | 0.7.18 | `MIT` | https://github.com/tokio-rs/tokio |
| `toml` | 0.8.23 | `Apache-2.0 OR MIT` | https://github.com/toml-rs/toml |
| `toml` | 1.1.2+spec-1.1.0 | `Apache-2.0 OR MIT` | https://github.com/toml-rs/toml |
| `toml_datetime` | 0.6.11 | `Apache-2.0 OR MIT` | https://github.com/toml-rs/toml |
| `toml_datetime` | 1.1.1+spec-1.1.0 | `Apache-2.0 OR MIT` | https://github.com/toml-rs/toml |
| `toml_edit` | 0.22.27 | `Apache-2.0 OR MIT` | https://github.com/toml-rs/toml |
| `toml_parser` | 1.1.2+spec-1.1.0 | `Apache-2.0 OR MIT` | https://github.com/toml-rs/toml |
| `toml_write` | 0.1.2 | `Apache-2.0 OR MIT` | https://github.com/toml-rs/toml |
| `tower` | 0.5.3 | `MIT` | https://github.com/tower-rs/tower |
| `tower-http` | 0.5.2 | `MIT` | https://github.com/tower-rs/tower-http |
| `tower-http` | 0.6.8 | `MIT` | https://github.com/tower-rs/tower-http |
| `tower-layer` | 0.3.3 | `MIT` | https://github.com/tower-rs/tower |
| `tower-service` | 0.3.3 | `MIT` | https://github.com/tower-rs/tower |
| `tracing` | 0.1.44 | `MIT` | https://github.com/tokio-rs/tracing |
| `tracing-appender` | 0.2.5 | `MIT` | https://github.com/tokio-rs/tracing |
| `tracing-attributes` | 0.1.31 | `MIT` | https://github.com/tokio-rs/tracing |
| `tracing-core` | 0.1.36 | `MIT` | https://github.com/tokio-rs/tracing |
| `tracing-log` | 0.2.0 | `MIT` | https://github.com/tokio-rs/tracing |
| `tracing-serde` | 0.2.0 | `MIT` | https://github.com/tokio-rs/tracing |
| `tracing-subscriber` | 0.3.23 | `MIT` | https://github.com/tokio-rs/tracing |
| `try-lock` | 0.2.5 | `MIT` | https://github.com/seanmonstar/try-lock |
| `twox-hash` | 2.1.2 | `MIT` | https://github.com/shepmaster/twox-hash |
| `typeid` | 1.0.3 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/typeid |
| `typenum` | 1.20.0 | `Apache-2.0 OR MIT` | https://github.com/paholg/typenum |
| `typetag` | 0.2.23 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/typetag |
| `typetag-impl` | 0.2.23 | `Apache-2.0 OR MIT` | https://github.com/dtolnay/typetag |
| `ucd-trie` | 0.1.7 | `Apache-2.0 OR MIT` | https://github.com/BurntSushi/ucd-generate |
| `unicase` | 2.9.0 | `Apache-2.0 OR MIT` | https://github.com/seanmonstar/unicase |
| `unicode-ident` | 1.0.24 | `(Apache-2.0 OR MIT) AND Unicode-3.0` | https://github.com/dtolnay/unicode-ident |
| `unicode-normalization-alignments` | 0.1.12 | `Apache-2.0 OR MIT` | https://github.com/n1t0/unicode-normalization |
| `unicode-segmentation` | 1.13.2 | `Apache-2.0 OR MIT` | https://github.com/unicode-rs/unicode-segmentation |
| `unicode-width` | 0.2.2 | `Apache-2.0 OR MIT` | https://github.com/unicode-rs/unicode-width |
| `unicode-xid` | 0.2.6 | `Apache-2.0 OR MIT` | https://github.com/unicode-rs/unicode-xid |
| `unicode_categories` | 0.1.1 | `Apache-2.0 OR MIT` | https://github.com/swgillespie/unicode-categories |
| `unit-prefix` | 0.5.2 | `MIT` | https://codeberg.org/commons-rs/unit-prefix |
| `untrusted` | 0.9.0 | `ISC` | https://github.com/briansmith/untrusted |
| `ureq` | 3.3.0 | `Apache-2.0 OR MIT` | https://github.com/algesten/ureq |
| `ureq-proto` | 0.6.0 | `Apache-2.0 OR MIT` | https://github.com/algesten/ureq-proto |
| `url` | 2.5.8 | `Apache-2.0 OR MIT` | https://github.com/servo/rust-url |
| `utf8-ranges` | 1.0.5 | `MIT OR Unlicense` | https://github.com/BurntSushi/utf8-ranges |
| `utf8-zero` | 0.8.1 | `Apache-2.0 OR MIT` | https://github.com/algesten/utf8-zero |
| `utf8_iter` | 1.0.4 | `Apache-2.0 OR MIT` | https://github.com/hsivonen/utf8_iter |
| `utf8parse` | 0.2.2 | `Apache-2.0 OR MIT` | https://github.com/alacritty/vte |
| `utoipa` | 5.5.0 | `Apache-2.0 OR MIT` | https://github.com/juhaku/utoipa |
| `utoipa-gen` | 5.5.0 | `Apache-2.0 OR MIT` | https://github.com/juhaku/utoipa |
| `utoipa-swagger-ui` | 8.1.0 | `Apache-2.0 OR MIT` | https://github.com/juhaku/utoipa |
| `uuid` | 1.23.1 | `Apache-2.0 OR MIT` | https://github.com/uuid-rs/uuid |
| `valuable` | 0.1.1 | `MIT` | https://github.com/tokio-rs/valuable |
| `vcpkg` | 0.2.15 | `Apache-2.0 OR MIT` | https://github.com/mcgoo/vcpkg-rs |
| `version_check` | 0.9.5 | `Apache-2.0 OR MIT` | https://github.com/SergioBenitez/version_check |
| `walkdir` | 2.5.0 | `MIT OR Unlicense` | https://github.com/BurntSushi/walkdir |
| `want` | 0.3.1 | `MIT` | https://github.com/seanmonstar/want |
| `wasi` | 0.11.1+wasi-snapshot-preview1 | `Apache-2.0 OR Apache-2.0 WITH LLVM-exception OR MIT` | https://github.com/bytecodealliance/wasi |
| `wasip2` | 1.0.3+wasi-0.2.9 | `Apache-2.0 OR Apache-2.0 WITH LLVM-exception OR MIT` | https://github.com/bytecodealliance/wasi-rs |
| `wasip3` | 0.4.0+wasi-0.3.0-rc-2026-01-06 | `Apache-2.0 OR Apache-2.0 WITH LLVM-exception OR MIT` | https://github.com/bytecodealliance/wasi-rs |
| `wasm-bindgen` | 0.2.118 | `Apache-2.0 OR MIT` | https://github.com/wasm-bindgen/wasm-bindgen |
| `wasm-bindgen-futures` | 0.4.68 | `Apache-2.0 OR MIT` | https://github.com/wasm-bindgen/wasm-bindgen/tree/master/crates/futures |
| `wasm-bindgen-macro` | 0.2.118 | `Apache-2.0 OR MIT` | https://github.com/wasm-bindgen/wasm-bindgen/tree/master/crates/macro |
| `wasm-bindgen-macro-support` | 0.2.118 | `Apache-2.0 OR MIT` | https://github.com/wasm-bindgen/wasm-bindgen/tree/master/crates/macro-support |
| `wasm-bindgen-shared` | 0.2.118 | `Apache-2.0 OR MIT` | https://github.com/wasm-bindgen/wasm-bindgen/tree/master/crates/shared |
| `wasm-encoder` | 0.244.0 | `Apache-2.0 OR Apache-2.0 WITH LLVM-exception OR MIT` | https://github.com/bytecodealliance/wasm-tools/tree/main/crates/wasm-encoder |
| `wasm-metadata` | 0.244.0 | `Apache-2.0 OR Apache-2.0 WITH LLVM-exception OR MIT` | https://github.com/bytecodealliance/wasm-tools/tree/main/crates/wasm-metadata |
| `wasm-streams` | 0.4.2 | `Apache-2.0 OR MIT` | https://github.com/MattiasBuelens/wasm-streams/ |
| `wasmparser` | 0.244.0 | `Apache-2.0 OR Apache-2.0 WITH LLVM-exception OR MIT` | https://github.com/bytecodealliance/wasm-tools/tree/main/crates/wasmparser |
| `web-sys` | 0.3.95 | `Apache-2.0 OR MIT` | https://github.com/wasm-bindgen/wasm-bindgen/tree/master/crates/web-sys |
| `web-time` | 1.1.0 | `Apache-2.0 OR MIT` | https://github.com/daxpedda/web-time |
| `webpki-root-certs` | 1.0.7 | `CDLA-Permissive-2.0` | https://github.com/rustls/webpki-roots |
| `winapi` | 0.3.9 | `Apache-2.0 OR MIT` | https://github.com/retep998/winapi-rs |
| `winapi-i686-pc-windows-gnu` | 0.4.0 | `Apache-2.0 OR MIT` | https://github.com/retep998/winapi-rs |
| `winapi-util` | 0.1.11 | `MIT OR Unlicense` | https://github.com/BurntSushi/winapi-util |
| `winapi-x86_64-pc-windows-gnu` | 0.4.0 | `Apache-2.0 OR MIT` | https://github.com/retep998/winapi-rs |
| `windows` | 0.57.0 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows-core` | 0.57.0 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows-core` | 0.62.2 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows-implement` | 0.57.0 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows-implement` | 0.60.2 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows-interface` | 0.57.0 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows-interface` | 0.59.3 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows-link` | 0.2.1 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows-registry` | 0.6.1 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows-result` | 0.1.2 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows-result` | 0.4.1 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows-strings` | 0.5.1 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows-sys` | 0.45.0 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows-sys` | 0.52.0 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows-sys` | 0.59.0 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows-sys` | 0.60.2 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows-sys` | 0.61.2 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows-targets` | 0.42.2 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows-targets` | 0.52.6 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows-targets` | 0.53.5 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows_aarch64_gnullvm` | 0.42.2 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows_aarch64_gnullvm` | 0.52.6 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows_aarch64_gnullvm` | 0.53.1 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows_aarch64_msvc` | 0.42.2 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows_aarch64_msvc` | 0.52.6 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows_aarch64_msvc` | 0.53.1 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows_i686_gnu` | 0.42.2 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows_i686_gnu` | 0.52.6 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows_i686_gnu` | 0.53.1 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows_i686_gnullvm` | 0.52.6 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows_i686_gnullvm` | 0.53.1 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows_i686_msvc` | 0.42.2 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows_i686_msvc` | 0.52.6 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows_i686_msvc` | 0.53.1 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows_x86_64_gnu` | 0.42.2 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows_x86_64_gnu` | 0.52.6 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows_x86_64_gnu` | 0.53.1 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows_x86_64_gnullvm` | 0.42.2 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows_x86_64_gnullvm` | 0.52.6 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows_x86_64_gnullvm` | 0.53.1 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows_x86_64_msvc` | 0.42.2 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows_x86_64_msvc` | 0.52.6 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `windows_x86_64_msvc` | 0.53.1 | `Apache-2.0 OR MIT` | https://github.com/microsoft/windows-rs |
| `winnow` | 0.7.15 | `MIT` | https://github.com/winnow-rs/winnow |
| `winnow` | 1.0.2 | `MIT` | https://github.com/winnow-rs/winnow |
| `wit-bindgen` | 0.51.0 | `Apache-2.0 OR Apache-2.0 WITH LLVM-exception OR MIT` | https://github.com/bytecodealliance/wit-bindgen |
| `wit-bindgen` | 0.57.1 | `Apache-2.0 OR Apache-2.0 WITH LLVM-exception OR MIT` | https://github.com/bytecodealliance/wit-bindgen |
| `wit-bindgen-core` | 0.51.0 | `Apache-2.0 OR Apache-2.0 WITH LLVM-exception OR MIT` | https://github.com/bytecodealliance/wit-bindgen |
| `wit-bindgen-rust` | 0.51.0 | `Apache-2.0 OR Apache-2.0 WITH LLVM-exception OR MIT` | https://github.com/bytecodealliance/wit-bindgen |
| `wit-bindgen-rust-macro` | 0.51.0 | `Apache-2.0 OR Apache-2.0 WITH LLVM-exception OR MIT` | https://github.com/bytecodealliance/wit-bindgen |
| `wit-component` | 0.244.0 | `Apache-2.0 OR Apache-2.0 WITH LLVM-exception OR MIT` | https://github.com/bytecodealliance/wasm-tools/tree/main/crates/wit-component |
| `wit-parser` | 0.244.0 | `Apache-2.0 OR Apache-2.0 WITH LLVM-exception OR MIT` | https://github.com/bytecodealliance/wasm-tools/tree/main/crates/wit-parser |
| `writeable` | 0.6.3 | `Unicode-3.0` | https://github.com/unicode-org/icu4x |
| `wyz` | 0.5.1 | `MIT` | https://github.com/myrrlyn/wyz |
| `xxhash-rust` | 0.8.15 | `BSL-1.0` | https://github.com/DoumanAsh/xxhash-rust |
| `yaml-rust2` | 0.10.4 | `Apache-2.0 OR MIT` | https://github.com/Ethiraric/yaml-rust2 |
| `yoke` | 0.8.2 | `Unicode-3.0` | https://github.com/unicode-org/icu4x |
| `yoke-derive` | 0.8.2 | `Unicode-3.0` | https://github.com/unicode-org/icu4x |
| `zerocopy` | 0.8.48 | `Apache-2.0 OR BSD-2-Clause OR MIT` | https://github.com/google/zerocopy |
| `zerocopy-derive` | 0.8.48 | `Apache-2.0 OR BSD-2-Clause OR MIT` | https://github.com/google/zerocopy |
| `zerofrom` | 0.1.7 | `Unicode-3.0` | https://github.com/unicode-org/icu4x |
| `zerofrom-derive` | 0.1.7 | `Unicode-3.0` | https://github.com/unicode-org/icu4x |
| `zeroize` | 1.8.2 | `Apache-2.0 OR MIT` | https://github.com/RustCrypto/utils |
| `zerotrie` | 0.2.4 | `Unicode-3.0` | https://github.com/unicode-org/icu4x |
| `zerovec` | 0.11.6 | `Unicode-3.0` | https://github.com/unicode-org/icu4x |
| `zerovec-derive` | 0.11.3 | `Unicode-3.0` | https://github.com/unicode-org/icu4x |
| `zip` | 2.4.2 | `MIT` | https://github.com/zip-rs/zip2.git |
| `zmij` | 1.0.21 | `MIT` | https://github.com/dtolnay/zmij |
| `zopfli` | 0.8.3 | `Apache-2.0` | https://github.com/zopfli-rs/zopfli |
| `zstd` | 0.13.3 | `MIT` | https://github.com/gyscos/zstd-rs |
| `zstd-safe` | 7.2.4 | `Apache-2.0 OR MIT` | https://github.com/gyscos/zstd-rs |
| `zstd-sys` | 2.0.16+zstd.1.5.7 | `Apache-2.0 OR MIT` | https://github.com/gyscos/zstd-rs |

## Дополнительные зависимости FULL-режима (Qdrant)

| Крейт | Версия | Лицензия | Репозиторий |
|-------|--------|----------|-------------|
| `async-stream` | 0.3.6 | `MIT` | https://github.com/tokio-rs/async-stream |
| `async-stream-impl` | 0.3.6 | `MIT` | https://github.com/tokio-rs/async-stream |
| `axum` | 0.6.20 | `MIT` | https://github.com/tokio-rs/axum |
| `axum-core` | 0.3.4 | `MIT` | https://github.com/tokio-rs/axum |
| `base64` | 0.21.7 | `Apache-2.0 OR MIT` | https://github.com/marshallpierce/rust-base64 |
| `h2` | 0.3.27 | `MIT` | https://github.com/hyperium/h2 |
| `http` | 0.2.12 | `Apache-2.0 OR MIT` | https://github.com/hyperium/http |
| `http-body` | 0.4.6 | `MIT` | https://github.com/hyperium/http-body |
| `hyper` | 0.14.32 | `MIT` | https://github.com/hyperium/hyper |
| `hyper-timeout` | 0.4.1 | `Apache-2.0 OR MIT` | https://github.com/hjr3/hyper-timeout |
| `hyper-timeout` | 0.5.2 | `Apache-2.0 OR MIT` | https://github.com/hjr3/hyper-timeout |
| `prost` | 0.12.6 | `Apache-2.0` | https://github.com/tokio-rs/prost |
| `prost` | 0.13.5 | `Apache-2.0` | https://github.com/tokio-rs/prost |
| `prost-derive` | 0.13.5 | `Apache-2.0` | https://github.com/tokio-rs/prost |
| `prost-types` | 0.13.5 | `Apache-2.0` | https://github.com/tokio-rs/prost |
| `qdrant-client` | 1.17.0 | `Apache-2.0` | https://github.com/qdrant/rust-client |
| `rustls-pemfile` | 2.2.0 | `Apache-2.0 OR ISC OR MIT` | https://github.com/rustls/pemfile |
| `socket2` | 0.5.10 | `Apache-2.0 OR MIT` | https://github.com/rust-lang/socket2 |
| `sync_wrapper` | 0.1.2 | `Apache-2.0` | https://github.com/Actyx/sync_wrapper |
| `tokio-io-timeout` | 1.2.1 | `Apache-2.0 OR MIT` | https://github.com/sfackler/tokio-io-timeout |
| `tonic` | 0.11.0 | `MIT` | https://github.com/hyperium/tonic |
| `tonic` | 0.12.3 | `MIT` | https://github.com/hyperium/tonic |
| `tower` | 0.4.13 | `MIT` | https://github.com/tower-rs/tower |
| `webpki-roots` | 1.0.7 | `CDLA-Permissive-2.0` | https://github.com/rustls/webpki-roots |

---

## Сборка и распространение

При распространении бинарных версий Nomenclature Search Service все вышеуказанные лицензии должны быть соблюдены. В состав поставки должен входить настоящий файл `LICENSES.md`.

## Сторонние данные

- **Стоп-слова (`stopwords.txt`)**: созданы на основе анализа реальных номенклатурных баз и не содержат лицензионных ограничений.
- **Демо-данные (`demo-items.csv`)**: сгенерированы искусственно и не содержат реальных товарных позиций. Могут использоваться для тестирования без ограничений.

## Контакты для лицензионных вопросов

- **Email:** kadr78job@gmail.com
- **Telegram:** @kadr78job
- **GitHub:** https://github.com/yourname/nomenclature-search

---

*Последнее обновление: 29 июля 2026 г.*