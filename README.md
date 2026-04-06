# Blog Customizer

Страница блога с открывающейся панелью кастомизации. Пользователь может менять шрифт, размер шрифта, цвет текста, цвет фона и ширину контента — изменения применяются через CSS-переменные после нажатия кнопки «Применить».

## Стек

- React 18 + TypeScript
- CSS Modules + SCSS
- Webpack
- Storybook

## Быстрый старт

```bash
git clone https://github.com/MrMikhaiI/blog-customizer.git
cd blog-customizer
npm install
npm start
```

Откроется браузер на `http://localhost:8080`.

## Команды

| Команда | Описание |
|---|---|
| `npm start` | Dev-сервер с hot reload |
| `npm run build` | Продакшн-сборка в `dist/` |
| `npm run storybook` | Storybook с UI-компонентами на `localhost:6006` |
| `npm run lint` | ESLint с автофиксом |
| `npm run stylelint` | Проверка SCSS |
| `npm run format` | Prettier |
| `npm run commit` | Commitizen для коммитов |

## Архитектура

```
App (index.tsx)
├── articleState — применённые настройки, передаются в <main> как CSS-переменные
├── setArticleState → onApply в ArticleParamsForm
│
└── ArticleParamsForm
    ├── isOpen — состояние открытия/закрытия сайдбара
    └── formState — черновик настроек до нажатия «Применить»
```

Закрытие сайдбара по клику вне панели реализовано через хук `useOutsideClickClose` из `src/ui/select/hooks`.

## Функциональность

- Клик на стрелку — открывает/закрывает сайдбар
- Клик вне сайдбара — закрывает его
- Изменения в форме не применяются сразу — только после «Применить»
- «Сбросить» — возвращает форму и статью к дефолтным настройкам
- Настройки применяются через CSS-переменные на уровне `<main>`

## Макет

[Figma](https://www.figma.com/design/LwuUJTVP5zN5xuhjazmq1A/Custom-dropdown?node-id=0-1)
