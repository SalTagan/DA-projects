HR Analytics – Atlas Labs

Описание проекта

Этот проект выполнен в Power BI в рамках практики DataCamp и направлен на анализ сотрудников Atlas Labs: демография, удовлетворённость, производительность, текучесть и поведение сотрудников.
Проект демонстрирует навыки работы с моделированием данных, DAX, Power Query и построением визуальной аналитики.

Основные цели проекта

Построить полноценную модель данных (звёздная схема)
Разработать ключевые метрики HR
Проанализировать текучесть сотрудников и факторы, влияющие на неё
Оценить удовлетворённость, performance review и карьерные показатели
Построить интерактивные дашборды для HR-отдела

Используемые технологии

Power BI Desktop
Power Query
DAX (Data Analysis Expressions)
Data Modeling

Этап 1. Подготовка данных
Проверка и форматирование столбцов
Проверены типы данных (текст, числа, даты) на основе метаданных
Приведены типы к корректным форматам

Создание таблицы DimDate
Добавлена с помощью DAX кода из файла DimDate.txt
Подключена к DimEmployee (неактивная связь, т. к. уже есть связь по другой колонке)

Настройка ключевых связей
DimEmployee ↔ DimEducationLevel
FactPerformanceRating:
EnvironmentSatisfaction → DimSatisfiedLevel (активная)
JobSatisfaction, RelationshipSatisfaction, WorkLifeBalance → (неактивные, активируются через USERELATIONSHIP)

FactPerformanceRating:
SelfRating → DimRatingLevel (активная)
ManagerRating → DimRatingLevel (неактивная)

Этап 2. Создание Measures
Основные метрики
TotalEmployees = COUNT(DimEmployee[EmployeeID])
ActiveEmployees = CALCULATE([TotalEmployees], DimEmployee[Attrition] = "No")
InactiveEmployees = CALCULATE([TotalEmployees], DimEmployee[Attrition] = "Yes")
Attrition Rate = DIVIDE([InactiveEmployees], [TotalEmployees])

Меры по датам (через USERELATIONSHIP)
TotalEmployeesDate = CALCULATE([TotalEmployees], USERELATIONSHIP(DimEmployee[HireDate], DimDate[Date]))
InactiveEmployeesDate = CALCULATE([InactiveEmployees], USERELATIONSHIP(DimEmployee[HireDate], DimDate[Date]))
% Attrition Rate Date = DIVIDE([InactiveEmployeesDate], [TotalEmployeesDate])

Финансовые меры
AverageSalary = AVERAGE(DimEmployee[MonthlyIncome])

Performance Review
LastReviewDate
NextReviewDate
JobSatisfaction
EnvironmentSatisfaction, RelationshipSatisfaction, WorkLifeBalance
SelfRating, ManagerRating

Этап 3. Визуализация
Страница 1: Employee Overview
Карточки: TotalEmployees, ActiveEmployees, InactiveEmployees, Attrition Rate
Stacked Column Chart: Hiring Trends (TotalEmployeesDate, Attrition split)
Clustered Bar Chart: Active Employees by Department
Matrix / Chart: Active Employees by Department & JobRole
<img width="905" height="511" alt="image" src="https://github.com/user-attachments/assets/09f6423b-010a-484a-a2cb-7a6c5bcc44e6" />


Страница 2: Demographics
Youngest employee / Oldest employee
AgeBins (создано в Power Query)
Employees by Age
Employees by Age and Gender
Employees by Marital Status
Employees by Ethnicity & Average Salary
Page-level filter: Active / Inactive
<img width="902" height="506" alt="image" src="https://github.com/user-attachments/assets/05dbd32e-c303-4210-b093-21d24ce396b4" />


Страница 3: Performance Tracker
Слайсер по FullName
Last Review / Next Review cards
Satisfaction Metrics by Year (Environment, Job, WorkLife, Relationship)
Performance Ratings by Year (SelfRating & ManagerRating)
<img width="902" height="495" alt="image" src="https://github.com/user-attachments/assets/494f0b25-93c6-455d-8169-d1335f3751f1" />


Страница 4: Attrition
Attrition Rate card
Attrition by Department & JobRole
Attrition by Hire Date (% Attrition Rate Date)
Attrition by Business Travel
Attrition by Overtime
Attrition by Tenure
<img width="903" height="498" alt="image" src="https://github.com/user-attachments/assets/42c53767-9090-4679-944d-d3590255bcfd" />


Выводы проекта (основные инсайты)
Текучесть сотрудников выше у сотрудников с низким уровнем зарплаты и высоким overtime.
Уровень JobSatisfaction и WorkLifeBalance являются ключевыми факторами удержания.
Наибольший риск ухода в отделах Sales и Laboratory.
Молодые сотрудники (20–29) обладают более высокой мобильностью.
Performance Review напрямую влияет на вероятность удержания сотрудника.

Итог

Проект демонстрирует полный цикл работы аналитика:
очистка данных
моделирование
DAX-расчёты (включая USERELATIONSHIP)
построение дашбордов
визуальный анализ HR данных
анализ текучести, отсутствий, performance review
