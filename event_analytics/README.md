# Проект "Событийная аналитика"

В данном проекте необходимо разобраться, как ведут себя пользователи мобильного приложения стартапа, который продаёт продукты питания.

**Задачи исследования:**
- изучить воронку продаж
- определить путь пользователя до покупки
- определить, сколько пользователей доходит до покупки
- определить, на каких шагах застревают пользователи и в каких количествах.
- исследовать результаты A/A/B-эксперимента. 

**Суть эксперимента**

Дизайнеры приложения пришли с идеей замены шрифтов во всём приложении. Но менеджеры не хотят рисковать, так как подобные изменения могли бы привести к снижению выручки. Было принято решение провести A/A/B-тестирование. Пользователей поделили на 3 группы: 2 контрольные со старыми шрифтами и одну экспериментальную — с новыми.

По результатам теста необходимо **выяснить, повлияло ли изменение шрифта на поведение пользователей и, как следствие, на конверсию шагов воронки.**

**Структура проекта:**

1. Общая информация о данных
2. Подготовка данных
3. Изучение и проверка данных
4. Воронка событий
5. Изучение результатов эксперимента
6. Вывод.

**Используемые библиотеки:** pandas, scipy.stats, datetime, numpy, math, matplotlib.pyplot.

**Статус проекта:** проект окончен.

**Ход исследования:** Провели предобработку - привели названия столбцов к стандартному виду, проверили пропуски, удалили дубликаты, привели данные к нужному типу. Удалили период с неполными данными (1.17%). Убедились, что отсутствуют пользователи, попавшие в разные группы A/A/B-тестирования. Определили частоту событий в логах. Посчитали количество пользователей для каждого события и доли пользователей, перешедших на следующий шаг - составили воронку, исключили из неё Tutorial как необязательный для совершения покупки экран. Создали сводную таблицу с количеством уникальных пользователей в каждой группе по каждому событию, а также посчитаем долю пользователей, совершивших эти события. Проверили контрольные группы - разница в количестве пользователей двух контрольных групп составила 1.15% (число участников примерно равно). Написали функцию для проведения z-теста для каждой пары групп по каждому событию для проверки статистически значимой разницы долей групп. Включили в проверку метод Шидака для критического уровня, так как проводится множественный тест (4 проверки для 4 событий - всего 16 проверок). Тест показал, что доли контрольных групп не имеют статистически значимой разницы по всем событиям. Так же z-тест не показал  различий в сравнении экспериментальной группы с контрольными. Это говорит о том, что изменение шрифта никоим образом не повлияло на поведение пользователей и воронка событий не изменилась.Сформировали выводы.

**Ключевые выводы проекта:**

Пользователь проходит следующие шаги:

- главный экран
- каталог продуктов
- просмотр корзины
- успешная оплата.

Самым проблемным шагом воронки является переход с главного экрана в каталог - теряется 38% пользователей. Этот пункт следует изучить более подробно, возможно, пользователи сталкиваются с какой-то проблемой.

47.7% пользователей после главного экрана совершили покупку - это довольно высокий показатель.

Анализ результатов A/A/B-теста показал, что для каждой пары групп по каждому событию нет статистически значимой разницы в долях пользователей групп, совершивших событие. Это говорит о том, что изменение шрифта никоим образом не повлияло на поведение пользователей и воронка событий не изменилась. Эксперимент можно считать удачным, и шрифт можно спокойно заменять. Но и позитивных изменений в воронке замена шрифта не произвела - все показатели остались на прежнем уровне.