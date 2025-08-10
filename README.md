#  Прогноз стоимости автомобиля

##  Описание проекта
Этот проект посвящён прогнозированию цены автомобилей на основе их характеристик.  
Используется датасет с данными о машинах в Молдове: год выпуска, пробег, объём двигателя, тип кузова, трансмиссия и др.

**Цель:** построить модель, которая сможет точно предсказывать цену автомобиля.

---

## � Данные
Источник данных: `moldova_cars_task.csv`

Признаки:
- `Year` — год выпуска
- `Distance` — пробег (км)
- `Engine_capacity(cm3)` — объём двигателя
- `Body_type` — тип кузова
- `Transmission` — тип трансмиссии
- `Fuel_type` — тип топлива
- `Price(euro)` — цена автомобиля (целевой признак)

---

## � Используемые технологии
- **Python**: `pandas`, `numpy`, `matplotlib`, `seaborn`
- **ML-библиотеки**: `scikit-learn`, `tensorflow`
- **Модели**:
  - Lasso Regression
  - Ridge Regression
  - Decision Tree Regressor
  - Bagging Regressor
  - Нейронная сеть (TensorFlow/Keras)

---

##  Этапы работы
1. **Загрузка и предварительный анализ данных**
   - Проверка типов данных
   - Поиск пропусков
   - Корреляционный анализ
2. **Предобработка**
   - Заполнение пропусков модой/средним
   - Масштабирование числовых признаков
   - One-hot encoding категориальных признаков
3. **Моделирование**
   - Подбор гиперпараметров через `GridSearchCV`
   - Обучение и сравнение моделей
4. **Оценка качества**
   - Метрики: RMSE, MAE, R²
   - Визуализация предсказаний

---

##  Результаты

| Модель                   | R²    | MAE (€) | MSE           |
|--------------------------|-------|---------|---------------|
| **Lasso Regression**     | 0.510 | 3638    | 47,768,189    |
| **Ridge Regression**     | 0.673 | 2270    | 31,893,408    |
| **Decision Tree**        | 0.742 | 2114    | 25,137,997    |
| **Bagging Regressor**    | 0.800 | 1913    | 19,541,724    |
| **Нейронная сеть (Keras)**| —     | 2339    | 21,731,094    |

---

##  Лучшие гиперпараметры

- **Lasso Regression** → `alpha=1`, `fit_intercept=True`
- **Ridge Regression** → `alpha=1`, `fit_intercept=True`
- **Bagging Regressor** → `n_estimators=12`, `max_features=2`, `max_samples=2`
- **Decision Tree** → `criterion='absolute_error'`, `min_samples_leaf=3`, `min_samples_split=3`, `max_features=2` *(подобрано экспериментально)*

---

##  Примеры визуализаций

**Матрица корреляций:**
![Correlation Matrix](images/correlation_matrix.png)

**Распределение цен:**
![Price Distribution](images/price_distribution.png)

**Сравнение предсказанных и фактических значений:**
![Predictions vs Actual](images/pred_vs_actual.png)

---

##  Как запустить проект
```bash
# Клонируем репозиторий
git clone https://github.com/maximus2012/car_price.git
cd project_name

# Устанавливаем зависимости
pip install -r requirements.txt

# Запускаем ноутбук
jupyter notebook "Цена_авто.ipynb"
