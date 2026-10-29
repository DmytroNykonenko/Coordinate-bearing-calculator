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

## v17 — Site name and map printing / Назва ділянки та друк карти

**English:** Enter an optional site/polygon name beside the coordinate system and magnetic declination. It appears on the map; if several polygons are present, the name is combined with each polygon number. Use **Print map** to open the browser's print dialog and choose a printer or **Save as PDF**. Print in landscape and enable background graphics if the satellite basemap does not appear. The map needs to finish loading before printing. Map tile access depends on your network.

**Українська:** Введіть необов'язкову назву ділянки поруч із системою координат і магнітним схиленням. Назва відображатиметься на карті; якщо полігонів кілька, до назви додається номер полігону. Натисніть **Друкувати карту**, щоб відкрити друк браузера, обрати принтер або **Зберегти як PDF**. Рекомендована альбомна орієнтація та ввімкнена опція друку фонової графіки. Перед друком дочекайтеся завантаження підкладки.
\n## v18 / Назва всередині полігону\nSite labels are positioned inside each polygon (centroid with concave-polygon fallback). / Назви ділянок розташовуються всередині відповідних полігонів.\n
## v19 — Print layout / Макет друку
The map print layout is optimized for one A4 landscape page at browser print scale 100%. The site cannot force browser printer settings, headers/footers, or printer color mode. If needed select A4, Landscape, disable headers/footers, and enable background graphics.

Макет друку оптимізовано для одного аркуша A4 в альбомній орієнтації при масштабі браузера 100%. Сайт не може примусово змінити налаштування принтера, колонтитули чи кольоровість. За потреби оберіть A4, Landscape, вимкніть колонтитули та увімкніть друк фонової графіки.
