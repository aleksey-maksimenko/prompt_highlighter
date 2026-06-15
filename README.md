# Prompt Hub PoC

Технический прототип редактора промптов для проекта Prompt Hub.

Проверка концепции собственного Prompt-редактора с подсветкой синтаксиса и live-preview.

Проект реализован как отдельный изолированный стенд и не включает backend, авторизацию, хранение данных или каталог промптов.

---

## Технологии

* React
* TypeScript
* Vite
* CSS
* Собственный Parser
* Собственная Token System

---

## Архитектура

```text
Prompt Text
    ↓
Parser
    ↓
Tokens
    ↓
React Renderer
    ↓
Preview
```

---

## Структура проекта

```text
src
├── components
│   ├── PromptEditor
│   ├── PromptPreview
│   └── Toolbar
│
├── pages
│   └── PlaygroundPage.tsx
│
├── parser
│   ├── parsePrompt.ts
│   ├── parseInline.ts
│   ├── tokenTypes.ts
│   └── rules
│
├── utils
│   └── applyToolbarAction.ts
│
├── App.tsx
├── main.tsx
└── index.css
```

---

## Поддерживаемый синтаксис

### Заголовки

```text
## Заголовок
```

### Разделители

```text
---
```

### Decorator

```text
+++Reasoning
```

### Переменные

```text
{{user}}
```

### XML

```text
<user>
</user>
```

### Inline Code

```text
`json`
```

### Code Block

````text
```json
{
  "status": "ok"
}
```
````

### CAPS

```text
НИКОГДА
ВСЕГДА
IMPORTANT
```

### MetaGlyph

```text
∈
∩
∪
¬
→
⊕
```

### Жирный текст

```text
**важный текст**
```

### Курсив

```text
*важный текст*
```

---

## Toolbar

Поддерживает:

* Заголовок
* Жирный текст
* Курсив
* Переменная
* XML-тег
* Inline Code
* Decorator

Если текст выделен, используется оборачивание.
Если текст не выделен, вставляется шаблон.

---

## Текущее состояние

Реализовано:

* Live Preview
* Собственный Parser
* Token Rendering
* Подсветка синтаксиса
* Toolbar
