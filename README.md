# YouTube
Курсовой проект по дисциплине "Проектирование высоконагруженных систем" VK Education в МГТУ.

## 1. Тема и целевая аудитория
YouTube - видеохостинг, предоставляющий своим пользователям возможность просмотра, оценки, комментирования и загрузки видео.

### Ключевой функционал 
- Список рекомендованных видео
- Поиск видео
- Просмотр видео
- Загрузка видео
- Добавление комментариев к видео
- Оценка видео посредством лайков/дизлайков
- Подписка на автора контента

### Целевая аудитория
Видеохостинг имеет 2,7 миллиарда активных пользователей в месяц [1].
Данные о месячной аудитории по странам представлены в таблице.

| Страна    | Количество пользователей в месяц, млн |
| --------- | ------------------------------------- |
| Индия     | 476                                   |
| США       | 238                                   |
| Бразилия  | 147                                   |
| Индонезия | 139                                   |
| Россия    | 95,4 [2]                              |
| Мексика   | 84,2                                  |
| Япония    | 79,4                                  |
| Пакистан  | 66,1                                  |
| Германия  | 65,7                                  |
| Вьетнам   | 63                                    |

## 2. Расчет нагрузки
### Продуктовые метрики
- 122 млн. активных пользователей в день (DAU) [1]
- 2,7 млрд. активных пользователей в месяц (MAU)
- Среднее время просмотра - 19 минут в день [3]
- На сервисе размещено 4 млрд. видео. Их суммарная длительность: 12,5 мин / 60 мин * 4 млрд = 800 млн. часов
- Каждую минуту на YouTube загружается 360 часов видео
- Среднее видео длится 12,5 минут [4]
- Среднее видео набирает 5600 просмотров [5]
- 2 из 1000 пользователей оставляют комментарий к видео
- 4 из 1000 пользователей сотавляют оценку к видео

### RPS по типам запросов
Предположим, что пользователь посещает страницу рекомендаций 2 раза в день и 1 раз в день производит поиск видео.

Пусть видео отдаются пользователю блоками размером в 1 минуту.

Среднее количество видео, которое все пользователи загружают на видеохостинг в день: 360 часов * 60 * 24 / 12,5 минут = 2 488 320.

Предположим, что пользователь подписывается на новые каналы 5 раз в год.

| Тип запроса         | Количество запросов в день на пользователя | Средний RPS   | Пиковый RPS |
| ------------------- | ------------------------------------------ | ------------- | ----------- |
| Список рекомендаций | 2                                          | 2 824         | 7 060       |
| Поиск видео         | 1                                          | 1 412         | 3 530       |
| Просмотр видео      | 19                                         | 26 828        | 67 070      |
| Загрузка видео      | 0,02                                       | 28            | 70          |
| Комментарий         | 0,002                                      | 3             | 8           |
| Оценка видео        | 0,004                                      | 6             | 15          |
| Оформление подписки | 0,015                                      | 21            | 52          |
| Суммарно за день    | 22,041                                     | 31 122        | 77 805      |

### Технические метрики
- Один час видео на YouTube в среднем весит 4 Гб [6]
- Размер пользовательского хранилища составляет 1 Мб

### Объем сохраняемых данных
| Тип данных           | Средний размер единицы данных | Количество данных | Размер данных |
| -------------------- | ----------------------------- | ----------------- | ------------- |
| Профиль пользователя | 1 Мб/шт                       | 2,5 млрд. шт      | 2 384 Тб      |
| Видео                | 4 Гб/час                      | 800 млн. часов    | 3 051 Пб      |
| Комментарии          | 0,1 Кб/шт                     | 44 млрд. шт       | 4 Тб          |

### Сетевой трафик

| Тип запроса         | Трафик на одно действие | Пиковый RPS | Пиковый трафик, Гбит/с | Суммарный суточный трафик, Гбайт/сутки |
| ------------------- | ----------------------- | ----------- | ---------------------- | -------------------------------------- |
| Список рекомендаций | 2 Мб                    | 7 060       | 110                    | 476 550                                |
| Поиск видео         | 2 Мб                    | 3 530       | 55                     | 238 275                                |
| Просмотр видео      | 68 Мб                   | 67 070      | 35 630                 | 153 925 650                            |
| Загрузка видео      | 853 Мб                  | 70          | 466                    | 2 015 212                              |

## Источники
1. [Статистика использования YouTube по странам](https://www.globalmediainsight.com/blog/youtube-users-statistics/#YouTube_Users_by_Country)
2. [Статистика использования YouTube в России](https://www.statista.com/forecasts/1146977/youtube-users-in-russia)
3. [Статистика просмотра видео](https://www.broadbandsearch.net/blog/average-daily-time-on-social-media)
4. [Количество загружаемого контента](https://photutorial.com/how-many-videos-on-youtube/)
5. [Среднее количество просмотров](https://www.descript.com/blog/article/49-youtube-stats-2023-engagement-views-revenue-and-more)
6. [Вес видео](https://www.whistleout.com.au/MobilePhones/Guides/How-Much-Data-Does-YouTube-Use)