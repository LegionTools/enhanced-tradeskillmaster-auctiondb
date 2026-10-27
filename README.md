# TradeSkillMaster_AuctionDB (Enhanced)

An enhanced fork of TradeSkillMaster's AuctionDB module. All credit for the original addon goes to the TradeSkillMaster team; this fork adds a local historical-price feature and fixes a data-wiping schema bug on top.

## What changed

- **`PriceHistory` module** — locally populates the `DBHistorical` price source (previously only ever filled in by the official TSM Desktop App) from a per-item, per-calendar-day running average of market value, written to a new `TSM.db.realm.priceHistoryDaily` field. The averaging window is configurable (1 / 3 / 7 / 30 / 90 days, new "Historical Price Averaging Period" dropdown in the module's General Settings, default 7 days) via the new `historicalPricePeriodDays` schema field.
- **Fixed a schema-version bug that silently wiped all scan data.** New realm-scope keys were tagged with `lastModifiedVersion` matching the *existing* schema `version` number instead of a bumped one — `TSMAPI.Settings` wipes the whole database on load whenever the version number matches but the computed schema hash doesn't. Schema `version` bumped 2 → 3 to fix it.

## Installation

Drop this folder into `Interface/AddOns/TradeSkillMaster_AuctionDB`, replacing the stock module. Requires core TradeSkillMaster to be installed as usual.

---

# TradeSkillMaster_AuctionDB (улучшенная версия)

Улучшенный форк модуля AuctionDB из TradeSkillMaster. Вся заслуга за оригинальный аддон принадлежит команде TradeSkillMaster; этот форк добавляет локальный расчёт исторической цены и исправляет баг со стиранием данных.

## Что изменено

- **Модуль `PriceHistory`** — локально заполняет источник цены `DBHistorical` (раньше заполнялся только официальным TSM Desktop App) на основе скользящего среднего рыночной цены по дням для каждого предмета, записывается в новое поле `TSM.db.realm.priceHistoryDaily`. Период усреднения настраивается (1 / 3 / 7 / 30 / 90 дней, новый выпадающий список «Период усреднения исторической цены» в общих настройках модуля, по умолчанию 7 дней) через новое поле схемы `historicalPricePeriodDays`.
- **Исправлен баг схемы версий, незаметно стиравший все данные сканирования.** Новые ключи realm-области были помечены `lastModifiedVersion`, совпадающим с *текущим* номером `version` схемы, а не повышенным — `TSMAPI.Settings` стирает всю базу при загрузке, если номер версии совпадает, но вычисленный хеш схемы — нет. Номер `version` схемы поднят с 2 до 3 для исправления.

## Установка

Поместите эту папку в `Interface/AddOns/TradeSkillMaster_AuctionDB`, заменив штатный модуль. Требует установленного базового TradeSkillMaster, как обычно.
