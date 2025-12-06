#  HR Analytics – Atlas Labs

## Описание проекта

Этот проект выполнен в Power BI в рамках практики и направлен на анализ сотрудников Atlas Labs.  
Исследуются ключевые HR-показатели: демография, удовлетворённость, производительность, текучесть.

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

## Этап 1. Подготовка данных

- Выполнена проверка и форматирование всех столбцов в Power Query  
- Приведены типы данных к корректным (текст, число, дата)  
- Удалены дубликаты и исправлены некорректные значения  
- Выполнена первичная проверка качества данных  

---

## Создание таблицы DimDate

- Таблица `DimDate` создана с помощью DAX-кода из файла `DimDate.txt`  
- Связана с таблицей `DimEmployee`  
- Связь сделана *неактивной*, т.к. у таблицы уже существует активная связь по другой колонке  

---

## Этап 2. Моделирование данных

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

## Этап 3. Создание мер (DAX)

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

# Этап 4. Создание визуализаций

### Страница 1 — Overview (Обзор)

- Карточки: TotalEmployees, ActiveEmployees, InactiveEmployees - Всего сотрудников, Активные сотрудники, Неактивные сотрудники
- Карточка: % Attrition Rate - Уровень текучести персонала
- График “Employee Hiring Trends” (TotalEmployeesDate by Date) - Тренды найма сотрудников
- Разделение сотрудников на Active / Inactive - Активные vs Неактивные

<img width="905" height="511" alt="image" src="https://github.com/user-attachments/assets/09f6423b-010a-484a-a2cb-7a6c5bcc44e6" />

---

### Страница 2 — *Demographics*

#### Возраст:
- Карточки: Youngest Employee / Oldest Employee - Самый молодой сотрудник/Самый возрастной сотрудник
- Колонка AgeBins (<20, 20–29, 30–39, 40–49, 50+) - Сотрудники по возрастным группам
- График "Employees by Age" - Сотрудники по возрасту
- График "Employees by Age and Gender" - Сотрудники по возрасту и полу

#### Прочая демография:
- График "Employees by Marital Status" - Сотрудники по семейному положению  
- AverageSalary (карточка) - Средняя зарплата 
- "Employees by Ethnicity and Average Salary" - Сотрудники по этническим группам и средней зарплате

<img width="902" height="506" alt="image" src="https://github.com/user-attachments/assets/05dbd32e-c303-4210-b093-21d24ce396b4" />

---

### Страница 3 — *Performance Tracker*

- Вычисляемый столбец: FullName  -  Фамилия Имя 
- Слайсер: Select employee - Выбор сотрудника
- Карточки: Last Review, Next Review  - Последнее ревю, Следующее ревю
- Графики удовлетворённости:
  - EnvironmentSatisfaction - Удовлетворённость рабочей средой 
  - JobSatisfaction - Удовлетворённость работой 
  - WorkLifeBalance -  Баланс работы и жизни 
  - RelationshipSatisfaction - Удовлетворённость отношениями в коллективе  
- Графики SelfRating и ManagerRating по годам - Самооценка и оценка руководителя

<img width="902" height="495" alt="image" src="https://github.com/user-attachments/assets/494f0b25-93c6-455d-8169-d1335f3751f1" />

---

### Страница 4 — *Attrition*

- Карточка % Attrition Rate - Общий уровень текучести 
- Графики:
  - % Attrition Rate by Department & JobRole - Текучесть по департаментам и должностям
  - "Attrition by Hire Date" (% Attrition Rate Date over time) - Текучесть по дате найма
  - "Attrition by Travel Frequency" - Текучесть в зависимости от командировок 
  - "Attrition by Overtime Requirement" - Текучесть в зависимости от переработок 
  - "Attrition by Tenure" - Текучесть по стажу работы

<img width="903" height="498" alt="image" src="https://github.com/user-attachments/assets/42c53767-9090-4679-944d-d3590255bcfd" />

---

## Итоги проекта

В результате работы над проектом были:

- Настроены активные и неактивные связи, включая пользовательские USERELATIONSHIP()  
- Разработаны ключевые HR-метрики и KPI  
- Реализованы интерактивные аналитические панели  
- Автоматизирована обработка данных в Power Query  
- Выполнен комплексный анализ: демография, текучесть, удовлетворенность, оценка эффективности, производительность  
