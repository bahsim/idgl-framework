# Запись о генерации

## Определение

**Запись о генерации** представляет собой отдельную, высокоуровневую стратегию или подход к решению **Генеративной задачи**. Она служит контейнером, который можно изменять и уточнять до тех пор, пока стратегия не будет усовершенствована или отброшена.

Фреймворк IDGL определяет два цикла обратной связи, которые определяют, как обрабатываются записи:

1.  **Внутреннее уточнение (`Уточнение --> Генерация ИИ`):** Когда проверка выявляет незначительные расхождения, пользователь входит в цикл уточнения. Это включает в себя внесение корректировок в артефакт для *текущей стратегии*. Эти изменения происходят **внутри существующей `Записи о генерации`**, обновляя ее состояние.

2.  **Стратегическое повторное формирование запроса (`Валидация --> Формирование намерения`):** Когда артефакт в корне не соответствует цели, пользователь отказывается от текущей стратегии и возвращается на этап `Формирование намерения`. Это действие **создает новую `Запись о генерации`** для размещения нового стратегического подхода.

## Структура записи

Каждая запись содержит развивающееся состояние одного стратегического подхода:

1.  **Руководящая стратегия:** Основное намерение, определяющее этот подход.
2.  **Активный артефакт:** Окончательная версия артефакта для этой стратегии, идентичная последнему артефакту в истории уточнений.
3.  **История уточнений:** Подробный журнал внутренних циклов уточнений. Каждая запись представляет собой полный снимок, содержащий:
    *   **Намерение уточнения:** Конкретный запрос, использованный для изменения артефакта.
    *   **Примечание о валидации:** Результат валидации для этой конкретной версии артефакта.
4.  **Итоговое резюме валидации:** Заключительная оценка этого подхода после завершения цикла уточнений.

## Пример сценария: Разделение модификации и повторного запроса

**Генеративная задача:** "Создать визуально привлекательную и производительную галерею изображений."

*   **Запись о генерации 1 (Стратегия: Ленивая загрузка)**
    *   **Руководящая стратегия:** "Создать галерею с использованием простого подхода ленивой загрузки."
    *   **История уточнений (внутри Записи 1):**
        *   **Цикл 1:**
            *   **Намерение уточнения:** "Добавить анимацию появления по мере загрузки изображений."
            *   **Примечание о валидации:** "Анимация работает."
        *   **Цикл 2:**
            *   **Намерение уточнения:** "Сделать заполнитель размытой версией оригинального изображения."
            *   **Примечание о валидации:** "Эффект размытия добавлен и проверен."
    *   **Активный артефакт:** Окончательный, полный код для галереи с ленивой загрузкой, включая все уточнения.
    *   **Итоговое резюме валидации:** "Этот подход слишком прост и не может эффективно обрабатывать тысячи изображений. Нужна новая стратегия."

*   **Запись о генерации 2 (Стратегия: Виртуализация - Новая запись создана через повторный запрос)**
    *   **Руководящая стратегия:** (Сформирована после отказа от Записи 1) "Создать новую галерею с нуля, используя высокопроизводительную библиотеку виртуализации."
    *   **Внутренний цикл уточнений (Изменение Записи 2):**
        1.  Создан первоначальный артефакт.
        2.  Проверка выявила ошибку с полосой прокрутки. Внесено уточнение.
    *   **Активный артефакт:** Код для галереи на основе виртуализации с исправленной ошибкой.
    *   **Итоговое резюме валидации:** "Успех. Эта стратегия производительна и корректна." 