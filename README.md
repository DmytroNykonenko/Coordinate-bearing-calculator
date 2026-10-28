# Coordinate & Bearing Calculator v12 / Калькулятор координат та азимутів

## English
Browser-based bilingual coordinate calculator with an interactive OpenStreetMap preview. All input data are processed locally in the browser.

### Input Excel
- Column 1: point name; column 2: UTM Easting; column 3: UTM Northing. Column headers can be anything.
- Place **LM** and/or **BM** anywhere in the file if available; both are optional and shared by all polygons.
- Each **SP** begins a new polygon. Its following **TP1, TP2, ... TPn** rows belong to that polygon until the next SP. TP numbering restarts at TP1 for each polygon.
- Point names are normalized for Cyrillic/Latin lookalikes and whitespace.
- Each polygon must have consecutive TP numbers (at least TP1 and TP2); rows must be grouped by polygon.

### Usage
1. Open `index.html` or the GitHub Pages website.
2. Upload the Excel file and choose WGS 1984 UTM Zone 36N/37N and magnetic declination 8°/9°.
3. Review the bilingual bearing/distance table and independent colored polygons on the interactive map. Zoom, pan or fit all polygons.
4. Download one Excel workbook with a single sheet, section headers **Polygon 1**, **Polygon 2**, etc. No area is displayed or exported.

Shared LM→BM is calculated once (if both exist). For each polygon, BM→SP or LM→SP is calculated when the relevant reference point exists. No artificial links connect separate polygon boundaries.

**Note:** bearings are UTM grid bearings; the displayed “True bearing” column follows the previous calculator's grid-based convention, without meridian-convergence correction.

## Українська
Двомовний браузерний калькулятор координат із інтерактивною картою OpenStreetMap. Дані обробляються локально у браузері.

### Вхідний Excel
- Колонка 1 — назва точки, колонка 2 — UTM Easting, колонка 3 — UTM Northing. Заголовки можуть бути довільними.
- **LM** і **BM** необов'язкові та спільні для всіх полігонів.
- Кожен **SP** починає новий полігон. Наступні **TP1, TP2, ... TPn** належать йому до наступного SP. Нумерація TP починається заново в кожному полігоні.
- Назви точок нормалізуються (латиниця/кирилиця, пробіли).
- Для кожного полігону потрібна безперервна послідовність TP (щонайменше TP1 і TP2). Точки полігонів мають бути згруповані.

### Послідовність роботи
1. Відкрийте `index.html` або сайт GitHub Pages.
2. Завантажте Excel, оберіть WGS 1984 UTM Zone 36N/37N і магнітне схилення 8°/9°.
3. Перевірте таблицю азимутів/відстаней і окремі кольорові полігони на інтерактивній карті. Можна масштабувати, рухати та показувати всі полігони.
4. Завантажте один Excel із заголовками **Полігон 1**, **Полігон 2** тощо в одній таблиці. Площа ніде не виводиться.

Спільний перехід LM→BM обчислюється один раз (якщо є обидві точки). Для кожного полігону обчислюється BM→SP або LM→SP за наявності контрольної точки. Штучних переходів між контурами немає.

**Примітка:** азимути обчислюються за координатною сіткою UTM; колонка «Істинний азимут» зберігає попередню логіку калькулятора без поправки на зближення меридіанів.

### GitHub Pages
Upload `index.html`, `README.md`, and `libs/jszip.min.js` to the repository root (with the JS file inside `libs/`). Enable Settings → Pages → Deploy from a branch → main → /(root).


## v13 — Basemap switcher / Перемикач підкладки

**English:** The interactive map defaults to **Satellite Imagery (Esri World Imagery)**. Use the **Basemap** dropdown above the map to switch to **OpenStreetMap** without changing the polygons, point labels, current zoom, or pan position. Satellite and OSM tiles require internet access to their respective providers. Attribution is shown on the map. Bearings, distances and Excel export are unaffected.

**Українська:** За замовчуванням карта використовує **супутникові знімки Esri World Imagery**. У меню **Підкладка** над картою можна переключитися на **OpenStreetMap** без зміни полігонів, підписів, масштабу та положення карти. Для обох підкладок потрібен доступ до відповідних картографічних серверів. Атрибуція відображається на карті. Розрахунки та експорт Excel не змінюються.


## v14 — Image / OCR input (English)

In addition to XLSX, select **Image / OCR** and upload one or more PNG, JPG or WebP screenshots of a coordinate table. Click **Recognize**, inspect the editable review table, correct any mistaken digits or point labels, and click **Apply coordinates**. The existing preview, map and Excel export then use the verified coordinates. Each new `SP` begins a separate polygon. `LM` and `BM` are optional shared points.

OCR uses Tesseract.js and downloads the recognition engine/model from external services when first used; Internet access is required. Images are processed in the browser, not uploaded to our server. Accuracy is not guaranteed. Always compare coordinates with the original image. Missing rows can be added manually, and the raw OCR text can be edited/reparsed. A cropped table may omit SP; do not invent missing coordinates.

## v14 — Завантаження зображень / OCR (Українська)

Окрім XLSX, можна вибрати **Image / OCR** і завантажити одне або кілька зображень таблиці у форматі PNG, JPG або WebP. Натисніть **Розпізнати зображення**, перевірте та за потреби виправте назви точок і координати у редагованій таблиці, після чого натисніть **Підтвердити координати**. Після цього працюють звичайні Preview, карта й експорт Excel. Кожна нова `SP` починає окремий полігон. `LM` і `BM` — необов'язкові спільні точки.

Для OCR використовується Tesseract.js, який під час першого запуску завантажує бібліотеку та модель із зовнішніх ресурсів. Потрібне інтернет-з'єднання. Обробка зображень відбувається в браузері, без надсилання на наш сервер. OCR може помилятися — **обов'язково звіряйте координати з оригіналом**. Відсутні рядки можна додати вручну, а розпізнаний текст відредагувати й повторно розібрати. Якщо на фото немає SP, координати SP потрібно надати окремо.


## v15 — OCR improvements / Покращення OCR

English: The OCR input is enlarged and converted to high-contrast monochrome before recognition. The parser expects `From / To / Magnetic / True / Distance / Easting / Northing` and extracts only the `From` point and its UTM coordinates. Ambiguous lines are omitted, never guessed. Review all rows and manually add missing coordinates before applying.

Українська: Перед розпізнаванням зображення збільшується й переводиться у висококонтрастний чорно-білий вигляд. Парсер обробляє формат `Від / До / Магнітний / Істинний / Відстань / UTMX / UTMY`, беручи назву з колонки «Від». Неоднозначні рядки пропускаються, а не вгадуються. Обов'язково перевірте всі рядки й додайте пропущені координати вручну.
