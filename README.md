###Модель для Распознавания Рукописных Букв Английского Алфавита
Этот проект представляет модель нейронной сети, разработанную для распознавания рукописных букв английского алфавита с использованием библиотеки Keras и датасета, содержащего рукописные изображения букв. Модель построена исключительно на полносвязанных слоях (Dense layers) и обучается на выборке букв, закодированных в виде изображений 28x28 пикселей.

Описание Датасета
Датасет состоит из изображений букв от 'A' до 'Z', где каждый образец представлен в виде одномерного массива длиной 784 (28x28 пикселей). Метки (labels) указывают, к какой букве относится изображение (0 - 'A', 1 - 'B', ... 25 - 'Z').

Источник: A-Z Handwritten Data

Подготовка и Обучение Модели
Зависимости
Убедитесь, что установлены следующие библиотеки:

numpy
matplotlib
scikit-learn
keras
Структура Модели
Модель состоит из двух слоев:

Входной слой — полносвязный слой (Dense) из 512 нейронов с функцией активации ReLU.
Выходной слой — полносвязный слой из 26 нейронов с функцией активации softmax для предсказания одной из 26 букв алфавита.
Компиляция и Обучение Модели
Модель компилируется с использованием:

Оптимизатор: RMSprop
Функция потерь: categorical_crossentropy
Метрика: accuracy
Модель обучается на 5 эпохах с размером батча 128. Датасет разбивается на тренировочную и тестовую выборку в соотношении 80:20.

python
Копировать код
history = model.fit(x_train, y_train, validation_data=(x_test, y_test), epochs=5, batch_size=128)
Оценка Результатов
После обучения модель тестируется на отложенной тестовой выборке. Выводятся следующие метрики:

Точность на тестовой выборке
Потери на тестовой выборке
Пример Предсказания
Пример использования модели для предсказания буквы на изображении из тестовой выборки:

python
Копировать код
# Предсказываем выбранную картинку
prediction = model.predict(x)
pred = np.argmax(prediction)
print(f'Распознана Буква: {word_dict[pred]}')
Результаты и Графики
Графики обучения показывают динамику изменения потерь и точности на каждой эпохе:

График потерь показывает, как изменяется ошибка (потери) на тренировочной и тестовой выборке.
График точности демонстрирует изменение точности предсказаний на тренировочной и тестовой выборке по эпохам.
Выводы
График потерь показывает, сходится ли модель — если значения потерь для обучающей и тестовой выборки постепенно снижаются, это сигнализирует о качественном обучении.
График точности на тестовой и обучающей выборке показывает, как хорошо модель обобщает данные. Если разница в точности на обучающей и тестовой выборке велика, модель может быть переобучена.
Как запустить
Скачайте датасет и сохраните его в текущую рабочую директорию.
Запустите скрипт в любом Python-совместимом IDE (например, Jupyter Notebook).
Проанализируйте результаты и графики после завершения обучения.
Задачи для Улучшения
Добавить более глубокую архитектуру, используя свёрточные слои (CNN), чтобы улучшить качество распознавания.
Исследовать влияние изменения гиперпараметров (например, размер батча, скорость обучения) на точность модели.
Добавить регуляризацию для уменьшения возможного переобучения.
