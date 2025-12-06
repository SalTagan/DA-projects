#  HR Analytics – Atlas Labs

## Описание проекта

Этот проект выполнен в Power BI в рамках практики DataCamp и направлен на анализ сотрудников Atlas Labs.  
Исследуются ключевые HR-показатели: демография, удовлетворённость, производительность, текучесть и карьерные траектории.

---

## Цели проекта
- Построить корректную модель данных для HR-аналитики  
- Разработать метрики текучести, удовлетворённости, performance review  
- Провести анализ факторов, влияющих на увольнения  
- Подготовить интерактивный дашборд для HR-отдела  
- Автоматизировать обновление данных через Power Query  

---

## Используемые технологии
- **Power BI Desktop**
- **Power Query**
- **DAX (Data Analysis Expressions)**
- **Data Modeling**

---

## Этапы работы над проектом


## 🧩 Этапы работы над проектом

---

## 🔧 Этап 1. Подготовка данных

- Выполнена проверка и форматирование всех столбцов в Power Query  
- Приведены типы данных к корректным (текст, число, дата) на основе метаданных  
- Удалены дубликаты и исправлены некорректные значения  
- Стандартизированы названия столбцов  
- Выполнена первичная проверка качества данных  
- Подготовлены таблицы для последующего моделирования

---

## 📅 Создание таблицы DimDate

- Таблица `DimDate` создана с помощью DAX-кода из файла `DimDate.txt`  
- Связана с таблицей `DimEmployee`  
- Связь сделана *неактивной*, т.к. у таблицы уже существует активная связь по другой колонке  

---

## 🔗 Этап 2. Моделирование данных

### Связи с DimEmployee:
- `DimEmployee` ↔ `DimEducationLevel`  

### Связи в FactPerformanceRating — уровни удовлетворённости:
- `EnvironmentSatisfaction` → `DimSatisfiedLevel` (**активная**)  
- `JobSatisfaction` → `DimSatisfiedLevel` (*неактивная, активируется через USERELATIONSHIP()*)  
- `RelationshipSatisfaction` → `DimSatisfiedLevel` (*неактивная*)  
- `WorkLifeBalance` → `DimSatisfiedLevel` (*неактивная*)  

### Связи в FactPerformanceRating — уровни performance rating:
- `SelfRating` → `DimRatingLevel` (**активная**)  
- `ManagerRating` → `DimRatingLevel` (*неактивная*)  

---

## 🧮 Этап 3. Создание мер (DAX)

### Основные KPI:
- **TotalEmployees** — количество сотрудников  
- **ActiveEmployees** — сотрудники с `Attrition = "No"`  
- **InactiveEmployees** — сотрудники с `Attrition = "Yes"`  
- **% Attrition Rate** — показатель текучести персонала  
- **AverageSalary** — средняя зарплата сотрудников  

### Меры с USERELATIONSHIP():
- `EnvironmentSatisfaction`  
- `JobSatisfaction`  
- `RelationshipSatisfaction`  
- `WorkLifeBalance`  

### Performance Review:
- **LastReviewDate** — дата последнего ревью  
- **NextReviewDate** — дата следующего ревью  
- **SelfRating** и **ManagerRating** — значения рейтингов по неактивным связям  

### Меры по дате:
- **TotalEmployeesDate** — с использованием USERELATIONSHIP  
- **InactiveEmployeesDate**  
- **% Attrition Rate Date**

---

# 📊 Этап 4. Создание визуализаций

### 📍 Страница 1 — *Overview*
- Карточки с TotalEmployees, ActiveEmployees, InactiveEmployees  
- Карточка % Attrition Rate  
- График "Employee Hiring Trends" (TotalEmployeesDate by Date)  
- Разделение по Attrition (Active/Inactive)  

<img width="905" height="511" alt="image" src="https://github.com/user-attachments/assets/09f6423b-010a-484a-a2cb-7a6c5bcc44e6" />

---

### 📍 Страница 2 — *Demographics*

#### Возраст:
- Карточки: Youngest Employee / Oldest Employee  
- Колонка AgeBins (<20, 20–29, 30–39, 40–49, 50+)  
- График "Employees by Age"  
- График "Employees by Age and Gender"

#### Прочая демография:
- График "Employees by Marital Status"  
- AverageSalary (карточка)  
- "Employees by Ethnicity and Average Salary"

<img width="902" height="506" alt="image" src="https://github.com/user-attachments/assets/05dbd32e-c303-4210-b093-21d24ce396b4" />

---

### Страница 3 — *Performance Tracker*

- Calculated Column: FullName (FirstName + LastName)  
- Слайсер: Select employee (single select + search)  
- Карточки: Last Review, Next Review  
- Графики удовлетворённости:
  - EnvironmentSatisfaction  
  - JobSatisfaction  
  - WorkLifeBalance  
  - RelationshipSatisfaction  
- Графики SelfRating и ManagerRating по годам

<img width="902" height="495" alt="image" src="https://github.com/user-attachments/assets/494f0b25-93c6-455d-8169-d1335f3751f1" />

---

### 📍 Страница 4 — *Attrition*

- Карточка % Attrition Rate  
- Графики:
  - % Attrition Rate by Department & JobRole  
  - "Attrition by Hire Date" (% Attrition Rate Date over time)  
  - "Attrition by Travel Frequency"  
  - "Attrition by Overtime Requirement"  
  - "Attrition by Tenure"

<img width="903" height="498" alt="image" src="https://github.com/user-attachments/assets/42c53767-9090-4679-944d-d3590255bcfd" />

---

## Итоги проекта

В результате работы над проектом были:

- Настроены активные и неактивные связи, включая пользовательские USERELATIONSHIP()  
- Разработаны ключевые HR-метрики и KPI  
- Реализованы интерактивные аналитические панели  
- Автоматизирована обработка данных в Power Query  
- Выполнен комплексный анализ: демография, текучесть, удовлетворенность, performance review, производительность  
