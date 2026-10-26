# Программирование для ИИ

Домашние работы по курсу «Программирование для ИИ»: полный цикл работы с данными — от производительности NumPy до предобработки, регрессионных моделей, подбора гиперпараметров, подготовки датасета изображений и обработки текста.

![Python](https://img.shields.io/badge/Python-3-3776AB?logo=python&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?logo=pandas&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-F7931E?logo=scikitlearn&logoColor=white)
![XGBoost](https://img.shields.io/badge/XGBoost-189FDD)
![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?logo=opencv&logoColor=white)
![NLTK](https://img.shields.io/badge/NLTK-154F5B)
![gensim](https://img.shields.io/badge/gensim-Word2Vec-0B7285)

## Работы

| № | Ноутбук | Тема | Что сделано |
|---|---------|------|-------------|
| 1 | [`1_dz.ipynb`](1_dz.ipynb) | NumPy vs списки Python | Замер скорости суммы, среднего и умножения на массивах до 10⁸ элементов; фильтрация и визуализация ~434 тыс. точек из `data.csv` в заданном прямоугольнике |
| 2 | [`2_dz.ipynb`](2_dz.ipynb) | Предобработка и признаки | Очистка объявлений о продаже авто ([Kaggle: car sales](https://www.kaggle.com/datasets/ekibee/car-sales-information)), обработка пропусков, Label/One-Hot кодирование, новые признаки (в т.ч. оценка состояния машины) |
| 3 | [`3_dz.ipynb`](3_dz.ipynb) | Линейная регрессия | Предсказание цены автомобиля: корреляционный анализ, масштабирование, два эксперимента с набором признаков — **R² = 0.935** |
| 4 | [`4_dz.ipynb`](4_dz.ipynb) | Ансамбли | Random Forest и XGBoost с тремя конфигурациями гиперпараметров каждая — лучший **R² = 0.962** (XGBoost) |
| 5 | [`5_dz.ipynb`](5_dz.ipynb) | Подбор гиперпараметров | Сравнение GridSearchCV, RandomizedSearchCV и BayesSearchCV по качеству и времени (таблица ниже) |
| 6 | [`6_dz.ipynb`](6_dz.ipynb) | Датасет изображений | Маска объекта (цветовой фильтр + морфология) против GrabCut, генератор аугментаций и сборка датасета |
| 7 | [`7_dz.ipynb`](7_dz.ipynb) | Обработка текста | Очистка диалогов от разметки, восстановление структуры, нормализация, лемматизация (pymorphy3) и стемминг, Bag of Words, TF-IDF, биграммы, Word2Vec |

### Подбор гиперпараметров (работа 5)

Задача — регрессия цены автомобиля, метрики на отложенной выборке:

| Модель | Метод | MAE, ₽ | R² | Время, с |
|---|---|---:|---:|---:|
| Random Forest | GridSearchCV | 115 964 | 0.9605 | 89 |
| Random Forest | RandomizedSearchCV | 119 039 | 0.9593 | 129 |
| Random Forest | BayesSearchCV | 115 797 | 0.9604 | 65 |
| XGBoost | GridSearchCV | 116 037 | 0.9626 | 122 |
| XGBoost | RandomizedSearchCV | **113 848** | 0.9626 | 36 |
| XGBoost | BayesSearchCV | 115 092 | **0.9629** | 36 |

Вывод: XGBoost стабильно немного точнее Random Forest, а случайный и байесовский поиск дают то же качество, что и полный перебор, в 2–3 раза быстрее.

## Запуск

```bash
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook
```

Большие датасеты и промежуточные файлы в репозиторий не включены (см. `.gitignore`); исходные данные для работ 2–5 — по ссылке на Kaggle выше.

## Автор

Куценко Игорь — [@igr43](https://github.com/igr43)
