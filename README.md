# geo_indexes_postgreSQL
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
Empirical testing showed that index type selection and data type consistency between the column definition and query conditions are both critical for achieving efficient spatial query execution. The research identified which combinations of index types and data types lead to index usage and which fall back to full table scans, with measurable differences in query performance.

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
Эмпирическое тестирование показало, что выбор типа индекса и согласованность типов данных между определением столбца и условиями запроса критически важны для эффективного выполнения пространственных запросов. В ходе исследования определены комбинации типов индексов и типов данных, при которых индекс используется, а при которых планировщик переходит на полный перебор таблицы — с измеримой разницей в производительности.

### Структура
- Отчет .pdf
- sql code тестирования
- readme.md
