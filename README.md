# Домашнее задание к занятию 11.1. «Базы данных, их типы» - Evgeny Myznikov

### Задание 1. СУБД
1.1. Бюджетирование проектов с дальнейшим формированием финансовых аналитических отчётов и прогнозирования рисков.

Реляционные: Oracle, MySQL, Microsoft SQL Server, PostgreSQL.

1.2. Под каждый девелоперский проект создаётся отдельный лендинг, и все данные по лидам стекаются в CRM к маркетологам и менеджерам по продажам. Какой тип СУБД лучше использовать для лендингов и для CRM?

MySQL, PostgreSQL или Microsoft SQL. Первые две бесплатные, у второй есть бесплатная версия (с ограничениями). Для небольшой команды подойдет любое решение, т.к. нагрузка скорее всего будет не очень значительная. Если планируется масштабирование, то PostgreSQL и Microsoft SQL.

1.3. Отдел контроля качества решил создать базу по корпоративным нормам и правилам, обучающему материалу и так далее, сформированную согласно структуре компании. СУБД должна иметь простую и понятную структуру. 

Для хранения объектов в одной сущности, но с разной структурой; хранение структур на основе JSON подойдут документные: Couchbase, MongoDB, Amazon DocumentDB

1.4. Департамент логистики нуждается в решении задач по быстрому формированию маршрутов доставки материалов по объектам и распределению курьеров по маршрутам с доставкой документов. СУБД должна уметь быстро работать со связями.

Графовые: Neo4j, Amazon Neptune, InfiniteGraph, TigerGraph

### Задание 2. Транзакции

2.1. Пользователь пополняет баланс счёта телефона, распишите пошагово, какие действия должны произойти для того, чтобы транзакция завершилась успешно. Ориентируйтесь на шесть действий.

Онлайн-транзакции. Подразумевается, что клиент делает запрос на транзакцию «прямо здесь и сейчас», в режиме реального времени. Таким образом, сразу после подачи запроса банк получает сигнал о необходимости провести операцию. Сюда относятся переводы с карты на карту, снятие денег через банкомат, оплата покупок через мини-терминал, получение денежных средств онлайн и т.д.
Суть любой операции — это «общение» двух банков. Начинается все с того, что клиент заходит в мобильное приложение своего банка - отправляет запрос на пополнение счета телефона на определенную сумму - запрос попадает в банк клиента, где он обрабатывается(наличие необходимых средств и тд) - клиент получает ответ о списании средств со счета - перевод средств в банк оператора - банк оператора возвращает ответ в банк клиента о зачислении средств на счет клиента в банке оператора - банк оператора направляет информацию оператору и клиенту о пополнении счета.

### Задание 3. SQL vs NoSQL

3.1. Напишите пять преимуществ SQL-систем по отношению к NoSQL.

SQL - лучший выбор, когда:
Доступна предопределенная структура и заданные схемы
Все данные в наборе данных должны быть строго согласованы
Анализ поведенческих и настраиваемых сеансов
Разработка пользовательских панелей мониторинга
Выполнение операций объединения и сложных запросов
Необходимо выполнить многорядные транзакции

### Задание 4. Кластеры

Горизонтальное масштабирование (scale horizontally или scale out), которое базируется на добавлении дополнительных вычислительных узлов, то есть предоставляет возможность добавлять в систему дополнительные компьютеры и распределять работу между ними. Сотни и даже тысячи маломощных компьютеров, объединенных в кластер, могут обеспечивать вычислительную мощность суперкомпьютеров.

###### Hadoop:
Hadoop — это набор программ с открытым исходным кодом, предназначенный для обработки Big Data. В его состав входят несколько компонент, каждый из которых выполняет определенную задачу, связанную с аналитикой Big Data.
В состав Hadoop входят: Distributed File-System, MapReduce, Hadoop Common, Hadoop YARN

Ключевые особенности Hadoop:
Можно быстро сохранять и обрабатывать большие объемы разнообразных данных. Объемы данных, генерируемые Интернетом вещей и социальными сетями, постоянно растут. Это делает Hadoop ключевым инструментом для работы с подобными источниками данных большого объема.
Distributed File-System обеспечивает Hadoop высокой вычислительной мощностью, необходимой для быстрых вычислений.
Hadoop обрабатывает сбои оборудования, перенаправляя задания на другие узлы и автоматически поддерживая несколько копий данных.
Можно хранить разнообразные структурированные или неструктурированные данные без предварительной обработки (включая изображения и видео).
Фреймворк работает на обычных серверах, которые более эффективны с точки зрения затрат, чем специальные выделенные хранилища.
При увеличении объема обрабатываемых данных можно добавлять узлы, что позволяет системе масштабироваться. С точки зрения администрирования это делается очень просто.

###### MongoDB:
MongoDB — это гибкая и масштабируемая документноориентированная NoSQL СУБД, которая поддерживает различные модели данных и хранит данные в наборах ключ-значение. Она была разработана как решение для работы с большими объемами распределенных данных, которые не могут эффективно обрабатываться в реляционных моделях, содержащих строки и таблицы. Как и Hadoop, MongoDB бесплатная и с открытым исходным кодом.

Ключевые особенности MongoDB:
Богатый язык запросов, поддерживающий текстовый поиск, агрегирование и CRUD-операции.
По сравнению с реляционными базами данных требует меньше операций ввода/вывода из-за встраиваемых моделей данных (embedded data model). Для ускорения выполнения запросов есть поддержка индексов.
Отказоустойчивость обеспечивается через репликацию наборов данных. Репликация обеспечивает хранение данных на нескольких серверах, что создает избыточность и высокую доступность.
Поддержка механизма шардинга для горизонтального масштабирования. Позволяет с меньшими затратами обрабатывать увеличивающийся объем данных (по сравнению с вертикальными способами масштабирования).
Поддержка нескольких движков хранения, что позволяет выбирать оптимальный в зависимости от типа рабочей нагрузки.

MongoDB лучше подходит для решения задач, связанных с данными. Аргументы в пользу использования MongoDB сводятся к следующим:
При использовании реляционных баз данных потребуется использовать несколько таблиц. Mongo позволяет представить данные в виде одного объекта, что особенно удобно для неизменяемых данных.
Язык запросов, используемый MongoDB, поддерживает динамические запросы.
Схема в MongoDB неявная, т.е. не нужно заранее ее проектировать. Это упрощает представление наследования и полиморфизма в базе данных.
Легко реализовать горизонтальное масштабирование.