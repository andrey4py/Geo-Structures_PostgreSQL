# Geo-Structures PostgreSQL (PostGis)
Researching geospatial index structures (R-Tree, Quad-tree, BRIN) in PostgreSQL via PostGIS — comparing GiST, SP-GiST and BRIN indexes for radius and KNN queries on a ticket booking service dataset.

# PostgreSQL Geo Structures Research / Исследование геоструктур в PostgreSQL

## English

### Overview
Research project exploring the application of geospatial indexing structures in PostgreSQL using the PostGIS extension. The study was conducted as part of an information systems architecture course and is based on a ticket booking service project.

### Problem
The ticket booking service required an efficient mechanism for finding venues by user geolocation — "show events near me" and "top N nearest venues". Standard PostgreSQL B-tree indexes are not suitable for multidimensional spatial data, so specialized geospatial indexes were investigated.

### Stack
- PostgreSQL 16 + PostGIS 3.4 (via Docker)
- DBeaver (SQL client)

### What was researched
- Core geospatial data structures and their theoretical foundations: R-Tree, Quad-tree, K-d tree, Grid/Geohash
- PostGIS data types (`geometry` vs `geography`) and coordinate reference systems (SRID)
- Available index types in PostgreSQL for spatial data: GiST, SP-GiST, BRIN
- Two practical query scenarios: radius search and nearest neighbor search (KNN)
- Impact of data type choices on index usage and query performance

### Key Findings
The study showed that out of the three types of indexes tested, only GiST (R-Tree) supports both geosearch scenarios — radius search and KNN nearest neighbor search. SP-GiST (quadtree) is only suitable for radius search and doesn’t support KNN, while BRIN turned out to be completely useless for geospatial queries. The optimal setup for geosearch is using a GEOGRAPHY type column with a GiST index — it allows proper use of the index for both scenarios and returns distances in meters without any extra conversion.

### Structure
- Report .pdf
- Testing SQL code
- readme.md

---

## Русский

### Описание
Исследовательский проект по применению геопространственных индексов в PostgreSQL с использованием расширения PostGIS. Работа выполнена в рамках курса по архитектуре информационных систем на основе проекта сервиса бронирования билетов.

### Задача
Сервис бронирования билетов требовал эффективного механизма поиска площадок по геолокации пользователя — "мероприятия рядом со мной" и "N ближайших площадок". Стандартные B-tree индексы PostgreSQL не подходят для многомерных пространственных данных, поэтому были исследованы специализированные геопространственные индексы.

### Стек
- PostgreSQL 16 + PostGIS 3.4 (через Docker)
- DBeaver (SQL-клиент)

### Что исследовалось
- Основные геопространственные структуры данных и их теоретические основы: R-Tree, квадродерево, K-d дерево, Grid/Geohash
- Типы данных PostGIS (`geometry` vs `geography`) и системы координат (SRID)
- Доступные типы индексов PostgreSQL для пространственных данных: GiST, SP-GiST, BRIN
- Два практических сценария запросов: поиск в радиусе и поиск ближайших соседей (KNN)
- Влияние выбора типа данных на использование индекса и производительность запросов

### Основные выводы
Исследование показало, что из трёх протестированных типов индексов только GiST (R-Tree) поддерживает оба сценария геопоиска — поиск в радиусе и KNN-поиск ближайших объектов. SP-GiST (квадродерево) применим только для поиска в радиусе и не поддерживает KNN, BRIN оказался полностью непригоден для геопространственных запросов. Оптимальной конфигурацией для задачи геопоиска является сочетание столбца типа GEOGRAPHY с индексом GiST — оно обеспечивает корректное использование индекса для обоих сценариев и возвращает расстояния в метрах без дополнительной конвертации.

### Структура
- Отчет .pdf
- sql code тестирования
- readme.md
