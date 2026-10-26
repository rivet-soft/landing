# Rivet — лендинг

Статическая страница для [Rivet](https://github.com/rivet-soft/rivet), быстрого нативного HTTP‑клиента для API.
Одна страница, без сборки и зависимостей: `index.html` и картинки в `assets/`.

## Как устроено

- **Кнопки «Скачать»** при загрузке страницы спрашивают у GitHub API последний релиз
  (`/repos/rivet-soft/rivet/releases/latest`) и подставляют файл под систему посетителя:
  `.dmg` для macOS, `.zip` для Windows, `.tar.gz` для Linux. Если появятся `.msi`, `.exe`, `.AppImage` или `.deb`,
  они выберутся автоматически (порядок — в `RANK` внутри `index.html`).
  Ответ API кешируется в `localStorage` на 10 минут. Если API недоступен, ссылки ведут на
  `https://github.com/rivet-soft/rivet/releases/latest`, так что после нового релиза ничего править не нужно.
- **Демо‑запрос** в первом экране — интерактивная модель окна Rivet: метод и окружение переключаются,
  `⌘↵` / `Ctrl+Enter` отправляет запрос, в Production опасные методы просят подтверждение.
- **`⌘K` / `Ctrl+K`** открывает палитру команд по странице, `/` — тоже.
- **Сниппеты кода** во вкладке «Код» сгенерированы самим Rivet (`rivet mcp` → `generate_code`) и лежат
  в `<script id="code-samples">`.
- Скриншоты сняты с релизной сборки Rivet на демо‑проекте Shop API (`examples/shop-api.yaml`)
  и лежат в `assets/shots/*.webp`.

## Локальный просмотр

```bash
python3 -m http.server 8000
# открыть http://localhost:8000
```

## Публикация

Страница работает на любом статическом хостинге. Для GitHub Pages: Settings → Pages →
Deploy from a branch → `main` / `(root)`. Файл `.nojekyll` уже лежит в корне.
