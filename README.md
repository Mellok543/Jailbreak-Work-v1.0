# JailBreak

Плагин JailBreak для CounterStrikeSharp.

В проекте есть:
- КТ-тест
- магазин за монеты
- покупка VIP через магазин
- ежедневные награды
- ежедневные задания
- игры на монеты
- лотерея
- меню с навигацией через бинды
- команды командира и LR
- админ-панель экономики, лотереи и LR

## Команды игроков

Основные команды:

- `!ct` / `css_ct` - пройти КТ-тест
- `!ctqueue` / `css_ctqueue` - показать статус очереди на КТ
- `!shop` / `css_shop` - открыть магазин
- `!balance` / `css_balance` - показать баланс монет
- `!topbalance` / `css_topbalance` - показать топ по балансу
- `!pay` / `css_pay` - открыть меню перевода монет
- `!games` / `css_games` - открыть меню игр
- `!lottery` / `css_lottery` - показать статус лотереи
- `!buyticket [кол-во]` / `css_buyticket [кол-во]` - купить один или несколько билетов лотереи

Ежедневные награды и задания:

- `!daily` / `css_daily` - забрать ежедневную награду
- `!dailyinfo` / `css_dailyinfo` - показать награды по дням серии
- `!quests` / `css_quests` - показать ежедневные задания

Меню и бинды:

- `!menubinds` / `css_menubinds` - показать подсказку по биндам меню
- `css_menu_up` - перемещение вверх по меню
- `css_menu_down` - перемещение вниз по меню
- `css_menu_select` - выбрать текущий пункт
- `css_menu_close` - закрыть меню

Команды JailBreak:

- `!w` / `css_w` - стать командиром и открыть меню командира
- `!uw` / `css_uw` - снять с себя командира
- `!lr` / `css_lr` - открыть LR-меню
- `!inmatecount` / `css_inmatecount` - посчитать зеков, которые далеко от командира

## Админ-команды

Доступ к админ-командам и админ-разделу магазина выдаётся по `SteamID64` через `AdminCommands.AllowedSteamIds`.

Экономика:

- `!givecoins <игрок> <кол-во>` / `css_givecoins <игрок> <кол-во>` - выдать монеты игроку
- `!takecoins <игрок> <кол-во>` / `css_takecoins <игрок> <кол-во>` - снять монеты у игрока
- `!setcoins <игрок> <кол-во>` / `css_setcoins <игрок> <кол-во>` - установить баланс игрока
- `!checkcoins <игрок>` / `css_checkcoins <игрок>` - посмотреть баланс игрока
- `!resetdaily <игрок>` / `css_resetdaily <игрок>` - сбросить ежедневную награду игрока
- `!resetquests <игрок>` / `css_resetquests <игрок>` - сбросить ежедневные задания игрока

LR и игры:

- `!lrend` / `css_lrend` - принудительно завершить текущий LR
- `!lrunfreeze` / `css_lrunfreeze` - сбросить эффекты и разморозить участников текущего LR
- `!resetgameoffers` / `css_resetgameoffers` - сбросить активные приглашения в игры на монеты

## Рекомендуемые бинды меню

Пример:

```cfg
bind "uparrow" "css_menu_up"
bind "downarrow" "css_menu_down"
bind "enter" "css_menu_select"
bind "backspace" "css_menu_close"
```

Альтернативный вариант:

```cfg
bind "z" "css_menu_up"
bind "x" "css_menu_down"
bind "c" "css_menu_select"
bind "v" "css_menu_close"
```

## Настройки магазина

Основные настройки в `shop_config.json`:

- `Items.VipEnabled` - включить покупку VIP
- `Items.VipItemName` - название VIP-товара
- `Items.VipCost` - цена VIP
- `Items.VipGroup` - VIP-группа для `css_vip_adduser`
- `Items.VipDuration` - срок действия VIP, например `7d`, `30d` или `0`
- `DailyReward.Enabled` - включить ежедневную награду
- `DailyReward.BaseAmount` - базовая награда
- `DailyReward.StreakBonusPerDay` - бонус за каждый день серии
- `DailyReward.MaxBonusStreakDays` - максимум дней серии для бонуса
- `Quests.Enabled` - включить ежедневные задания
- `Quests.KillsTarget` - цель по убийствам
- `Quests.KillsReward` - награда за убийства
- `Quests.SurviveRoundsTarget` - цель по выживанию в раундах
- `Quests.SurviveRoundsReward` - награда за выживание
- `Quests.PlayMinutesTarget` - цель по времени на сервере
- `Quests.PlayMinutesReward` - награда за время на сервере
- `Lottery.Enabled` - включить лотерею
- `Lottery.TicketCost` - цена билета
- `Lottery.MaxTicketsPerPlayer` - максимум билетов на игрока за карту
- `Lottery.AnnouncePurchases` - объявлять покупки билетов в чат
- `Lottery.HouseCommissionPercent` - комиссия сервера с банка
- `Lottery.AnnouncementIntervalMinutes` - интервал автоанонса банка в минутах, `0` отключает
- `AdminCommands.AllowedSteamIds` - SteamID64 с доступом к админ-командам и админ-панели

Пример:

```json
{
  "AdminCommands": {
    "AllowedSteamIds": [76561198000000000]
  }
}
```

## VIP через магазин

Выдача VIP выполняется через команду:

```text
css_vip_adduser <steamid or accountid> <vipgroup> <time or 0 permanently>
```

Пример настройки:

```json
{
  "Items": {
    "VipEnabled": true,
    "VipItemName": "VIP на 30 дней",
    "VipCost": 5000,
    "VipGroup": "gold",
    "VipDuration": "30"
  }
}
```
