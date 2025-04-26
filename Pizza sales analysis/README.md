# 🍕 Аналитика продаж пиццы | Pizza Sales Analytics

## 🇷🇺 Русская версия

Проект представляет собой полный цикл анализа продаж пиццерии с использованием "Python", "SQL" и "Power BI".  
Включает подготовку данных, расчёт метрик, SQL-запросы и создание интерактивного дашборда.

---

### 📦 Структура проекта

| Файл                             | Описание                                              |
|----------------------------------|-------------------------------------------------------|
| `Pizza Sales Analysis.ipynb`     | Python-ноутбук с очисткой данных и визуализацией      |
| `Pizza sales SQL queries.docx`   | SQL-запросы для расчёта метрик и аналитики            |
| `pizza restaurant sales.pbix`    | Power BI-дэшборд с фильтрами и KPI-графиками          |

---

### 📊 Используемые данные

4 объединённых CSV-файла:

- `orders.csv` — ID и дата заказов  
- `order_details.csv` — состав заказов  
- `pizzas.csv` — пиццы, категории, размеры, цены
- `pizza_types.csv`- название, категории, ингредиенты

---

### 🧮 Ключевые SQL-запросы (KPI)

- Общая выручка  
- Общее количество заказов  
- Общее количество проданных пицц
- Средняя стоимость заказа
- Средний чек  
- Среднее количество пицц на заказ 
- Топ-10 пицц по выручке 
- Топ-10 пицц по продажам  
- Продажи по дням недели, месяцам, часам  
- Доли продаж по категориям и размерам

📄 Смотри: `Pizza sales SQL queries.docx`

---

### 📊 Power BI-визуализации

- KPI-карточки  
- Тренд заказов по месяцам  
- Продажи по часам и дням недели  
- Топ пицц  
- Доли продаж по категориям и размерам  
- Срезы: название, количество, дата, категория, размер

---

### 🧪 Python-анализ

- Объединение и очистка данных  
- Выделение признаков (день, время)  
- Визуализация (bar, pie, line)  
- Подсчёт выручки, количества, распределений

---

### 💡 Основные инсайты

- Самая прибыльная пицца: "Classic Deluxe"  
- Больше всего заказов — "в обед и вечером"  
- Самый популярный размер: "Large"  
- Пиковые дни: "пятница и суббота"

---

### 🛠 Используемые технологии

- Python (pandas, matplotlib, seaborn)  
- MySQL  
- Power BI Desktop

---

## 🇬🇧 English Version

This project presents a full-cycle sales analysis for a fictional pizza restaurant using **Python**, **SQL**, and **Power BI**.  
It includes data cleaning, KPI calculation, query-based insights, and interactive dashboarding.

---

### 📦 Project Components

| File                            | Description                                          |
|----------------------------------|------------------------------------------------------|
| `Pizza Sales Analysis.ipynb`     | Python notebook with preprocessing and EDA           |
| `Pizza sales SQL queries.docx`   | SQL queries for metrics and business logic           |
| `pizza restaurant sales.pbix`    | Power BI dashboard with filters and KPIs             |

---

### 📊 Dataset

Merged from 3 CSV files:

- `orders.csv` — order dates and IDs  
- `order_details.csv` — pizza items in each order  
- `pizzas.csv` — pizza details: names, categories, sizes, prices
- `pizza_types.csv`- name, categories, ingredients
---

### 🧮 Key SQL KPIs

- Total revenue  
- Total orders
- Total number of pizzas sold  
- Average order value 
- Average bill 
- Average pizzas per order 
- Top 10 pizzas by revenue 
- Top 10 pizzas by sales  
- Sales by hour, weekday, month  
- % of sales by category and size

📄 See: `Pizza sales SQL queries.docx`

---

### 📊 Power BI Visuals

- KPI cards (revenue, orders, AOV, quantity)  
- Monthly order trend  
- Sales by hour and weekday  
- Top-selling pizzas  
- % of sales by category and size  
- Slicers by name, quantity, date, category and size

---

### 🧪 Python EDA

- Merging and cleaning raw data  
- Feature engineering (hour, day)  
- Visualizations (bar, pie, line)  
- Revenue, quantity, distribution metrics

---

### 💡 Key Insights

- Most profitable pizza: "Classic Deluxe"  
- Peak hours: "lunch and evening"  
- Most popular size: "Large"  
- Peak days: "Friday and Saturday"

---

### 🛠 Tools

- Python (pandas, matplotlib, seaborn)  
- MySQL  
- Power BI Desktop

---

## ✍️ Author

Salima Kuvandykova

---
📌 *This project was created for portfolio purposes to demonstrate skills in data analysis, SQL, and business intelligence.*

