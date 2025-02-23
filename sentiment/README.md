# API Documentation 

## Описание
Этот эндпоинт предназначен для анализа тональности текста. Он принимает текстовый запрос и возвращает тональность (`positive`, `neutral`, `negative`) с вероятностями для каждого класса.

### Эндпоинт
- **URL:** `https://sentiment.technokratos.com/analyze-sentiment`
- **Метод:** `POST`
- **Модель ответа:** `AnalyzeSentimentResponse`

---

## Структура запроса

### Тело запроса: `AnalyzeSentimentRequestBody`

| Поле      | Тип  | Описание             |
|-----------|------|----------------------|
| `message` | `str`| Текст для анализа.   |

---

## Структура ответа

### Тело ответа: `AnalyzeSentimentResponse`

| Поле      | Тип     | Описание                                           |
|-----------|---------|----------------------------------------------------|
| `sentiment`| `str`  | Определённая тональность текста (`positive`, `neutral`, `negative`). |
| `weights` | `Weights` | Вероятности для каждого класса.                   |

#### Модель `Weights`

| Поле       | Тип   | Описание                            |
|------------|-------|-------------------------------------|
| `neutral`  | `float`| Вероятность нейтральной тональности.|
| `positive` | `float`| Вероятность положительной тональности.|
| `negative` | `float`| Вероятность отрицательной тональности.|

---

## Пример использования

### Запрос

Пример отправки текста для анализа тональности:

```json
POST https://sentiment.technokratos.com/analyze-sentiment
{
  "message": "Этот проект просто невероятный!"
}
```

### Ответ
```json
{
  "sentiment": "positive",
  "weights": {
    "neutral": 0.01,
    "positive": 0.98,
    "negative": 0.01
  }
}
```