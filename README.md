# Coordinate & Bearing Calculator / Калькулятор координат та азимутів

## English

### Description
Coordinate & Bearing Calculator is a bilingual (Ukrainian/English) browser-based tool for converting a simple Excel coordinate list into a ready bearing and distance table. It is designed to run as a static website, including on GitHub Pages. All calculations are performed locally in the user's browser; the uploaded coordinate file is not sent to a server.

The application calculates:
- true/grid bearing between consecutive points;
- magnetic bearing using the selected magnetic declination (8° or 9°);
- planar distance between points in metres;
- polygon area for the sequence `SP → TP1 → TP2 → ... → TPn → SP`;
- a ready-to-download bilingual Excel output table.

### Input Excel structure
The application does **not** depend on column header names. Only the position of the first three columns matters:

1. **Column 1** — point name;
2. **Column 2** — Easting / X coordinate;
3. **Column 3** — Northing / Y coordinate.

The first row is treated as the header row and may contain any column names.

Required point names are `LM`, `BM`, `SP`, and `TP1...TPn`. TP points must be numbered consecutively without gaps. The number of TP points is detected automatically.

Example:

| Any header | Any header | Any header |
|---|---:|---:|
| LM | 123456 | 5432100 |
| BM | 123500 | 5432150 |
| SP | 123600 | 5432200 |
| TP1 | 123700 | 5432250 |
| TP2 | 123650 | 5432300 |

### Workflow
1. Open the web application.
2. Select **UA** or **EN** for the interface language.
3. Upload an `.xlsx` or `.xls` file containing the coordinates.
4. Select the coordinate system: **WGS 1984 UTM Zone 36N** or **WGS 1984 UTM Zone 37N**.
5. Select the magnetic declination: **8°** or **9°**.
6. Check the preview and calculated total area.
7. Click **Generate Excel**.
8. The application creates `bearing_calculation.xlsx` with the sequence `LM → BM → SP → TP1 → ... → TPn → SP`.

### Calculation rules
- True bearing is calculated clockwise from grid north using UTM X/Y coordinates.
- Magnetic bearing = true/grid bearing − selected magnetic declination, normalized to `0–359°`.
- Distance is calculated as planar UTM distance in metres.
- Area is calculated from `SP` and all TP points and is returned in square metres.

### GitHub Pages
Upload `index.html` and `README.md` to the root of a GitHub repository. In **Settings → Pages**, choose **Deploy from a branch**, select `main`, choose `/ (root)`, and save. GitHub will publish the application as a static website.

---

## Українська

### Опис
Coordinate & Bearing Calculator — це двомовний (українська/англійська) браузерний додаток, який перетворює простий Excel-файл з координатами у готову таблицю азимутів і відстаней. Додаток може працювати як статичний сайт, зокрема через GitHub Pages. Усі розрахунки виконуються локально у браузері користувача; завантажений файл з координатами не передається на сервер.

Додаток автоматично розраховує:
- істинний/grid азимут між послідовними точками;
- магнітний азимут з урахуванням вибраного магнітного схилення (8° або 9°);
- відстань між точками у метрах;
- площу полігону за послідовністю `SP → TP1 → TP2 → ... → TPn → SP`;
- готову двомовну Excel-таблицю для завантаження.

### Структура вхідного Excel
Додаток **не прив'язаний до назв колонок**. Важливим є лише порядок перших трьох колонок:

1. **1-ша колонка** — назва точки;
2. **2-га колонка** — координата Easting / X;
3. **3-тя колонка** — координата Northing / Y.

Перший рядок вважається рядком заголовків. Назви колонок можуть бути будь-якими.

Обов'язкові назви точок: `LM`, `BM`, `SP` та `TP1...TPn`. TP мають бути пронумеровані послідовно, без пропусків. Кількість TP визначається автоматично.

Приклад:

| Будь-яка назва | Будь-яка назва | Будь-яка назва |
|---|---:|---:|
| LM | 123456 | 5432100 |
| BM | 123500 | 5432150 |
| SP | 123600 | 5432200 |
| TP1 | 123700 | 5432250 |
| TP2 | 123650 | 5432300 |

### Послідовність роботи
1. Відкрити вебдодаток.
2. Обрати **UA** або **EN** для мови інтерфейсу.
3. Завантажити `.xlsx` або `.xls` файл з координатами.
4. Обрати систему координат: **WGS 1984 UTM Zone 36N** або **WGS 1984 UTM Zone 37N**.
5. Обрати магнітне схилення: **8°** або **9°**.
6. Перевірити попередній перегляд таблиці та розраховану загальну площу.
7. Натиснути **Згенерувати Excel**.
8. Додаток створить `bearing_calculation.xlsx` з послідовністю `LM → BM → SP → TP1 → ... → TPn → SP`.

### Правила розрахунку
- Істинний азимут розраховується за UTM X/Y за годинниковою стрілкою від grid north.
- Магнітний азимут = істинний/grid азимут − вибране магнітне схилення з приведенням результату до `0–359°`.
- Відстань розраховується як планарна UTM-відстань у метрах.
- Площа розраховується за `SP` та всіма TP і повертається у квадратних метрах.

### Публікація на GitHub Pages
Завантажте `index.html` та `README.md` у корінь GitHub-репозиторію. У **Settings → Pages** виберіть **Deploy from a branch**, гілку `main`, папку `/ (root)` та збережіть налаштування. Після цього GitHub опублікує додаток як статичний вебсайт.

---

## Offline dependency / Автономна залежність

**EN:** Version 3 does not load the Excel-processing library from a public CDN. The required JavaScript ZIP module is stored locally in `libs/jszip.min.js`, and XLSX reading/writing is handled in the browser. This improves compatibility with corporate networks that block public CDNs. Keep the `libs` folder next to `index.html` when publishing the site.

**UA:** Версія 3 не завантажує бібліотеку для обробки Excel із зовнішнього CDN. Необхідний JavaScript ZIP-модуль зберігається локально у `libs/jszip.min.js`, а читання та створення XLSX виконується безпосередньо у браузері. Це покращує роботу в корпоративних мережах, де зовнішні CDN можуть бути заблоковані. Під час публікації обов'язково залишайте папку `libs` поруч з `index.html`.


## Browser compatibility / Сумісність браузерів

**English:** Version 4 uses explicit DOM element references instead of browser-created global variables. This improves compatibility with managed/corporate browsers and stricter browser security policies. The Excel ZIP library is stored locally in `libs/jszip.min.js`; no external CDN is required.

**Українська:** Версія 4 використовує явні посилання на HTML-елементи замість автоматичних глобальних змінних браузера. Це покращує сумісність із корпоративними/керованими браузерами та суворішими політиками безпеки. Excel ZIP-бібліотека зберігається локально в `libs/jszip.min.js`; зовнішній CDN не потрібен.


## Optional LM and BM / Необов’язкові LM та BM

**English:** `LM` and `BM` are optional. `SP` and a continuous sequence of `TP1...TPn` are required. If LM and/or BM are absent, the application shows a warning and continues. If both exist, the route starts `LM → BM → SP`. If only LM exists, it starts `LM → SP`. If only BM exists, it starts `BM → SP`. If neither exists, calculation starts `SP → TP1 → ... → TPn → SP`.

**Українська:** `LM` та `BM` є необов’язковими. Обов’язковими залишаються `SP` і безперервна послідовність `TP1...TPn`. Якщо LM та/або BM відсутні, додаток показує попередження, але продовжує роботу. Якщо є обидві точки, маршрут починається `LM → BM → SP`. Якщо є лише LM — `LM → SP`. Якщо є лише BM — `BM → SP`. Якщо немає обох — розрахунок починається `SP → TP1 → ... → TPn → SP`.


## Required control points / Обов’язкові контрольні точки

**English:** `LM`, `BM`, `SP`, and a continuous sequence of `TP1...TPn` are required. If `LM`, `BM`, `SP`, or any TP in the sequence is missing, the application displays an error and Excel generation is disabled. The calculation sequence is always `LM → BM → SP → TP1 → ... → TPn → SP`.

**Українська:** `LM`, `BM`, `SP` та безперервна послідовність `TP1...TPn` є обов’язковими. Якщо відсутні `LM`, `BM`, `SP` або будь-яка TP у послідовності, застосунок показує помилку та не дозволяє генерувати Excel. Послідовність розрахунку завжди: `LM → BM → SP → TP1 → ... → TPn → SP`.
