# Анализ АВ-теста новой системы рекомендации товаров

Команда внедрила в приложение умную систему рекомендации товаров – предполагается, что такая система поможет пользователям эффективнее работать с приложением и лучше находить необходимые товары.
Чтобы проверить эффективность системы рекомендаций, был проведен АБ-тест. В группе 1 оказались пользователи с новой системой рекомендаций, в группе 0 пользователи со старой версией приложения, где нет рекомендации товаров.

**Задача:** оценить, смогла ли новая система рекомендаций принести пользу бизнесу и пользователям приложения.

**Стек:** Python и библиотеки(pandas, seaborn, numpy, scipy.stats, requests, json, pingouin) + немного статистики и продуктовых метрик.

**Данные:**
- ab_users_data – история заказов пользователей, в этой таблице есть информация о том, какие заказы создавали и отменяли пользователи.
- ab_orders – подробная информация о составе заказа, тут для каждого заказа есть список id тех продуктов, которые были включены в заказ.
- ab_products – подробная информация о продуктах, их название и стоимость.

**Анализ:**
1. Предобработка данных. Датасет *ab_users_data* методом библиотеки Pandas explode() разбиваем список с покупками на отдельные строки. Собиранем финальный датасет, исключаем отмененные заказы.
2. Сравниваю конверсию отклоненённых закзов. Сатистический метод хи-квадрат не позволяет отклонить нулевую гипотезу о различиях переменных.
3. Нахожу средний чек. Провожу двувыборочный t-тест, который не позволяет отклонить нулевую гипотезу о различиях в выборках(т.е. среднии двух выборок/двух групп не имеют статистических различий).
4. Нахожу общую выручку. Выручка тестовый группы значительно больше.

**ВЫВОД:**
Анализ результатов АВ-тестировние показал: включать новую систему рекомендаций необходимо. средний чек и конверсия отмененных заказов не зависят от того, какая система рекомендации товаров применялась. Но выручка значительно выросла, за счёт того, что в тестовой группе больше пользователей дошло до шага совершения и оплаты заказа.
  
