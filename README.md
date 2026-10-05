# Coordinate & Bearing Calculator / Калькулятор координат та азимутів

## English
A browser-based tool for preparing coordinate/bearing tables from Excel. The input file may use any column headers: column 1 is the point name, column 2 is Easting/X, and column 3 is Northing/Y.

### Required points
- **SP** and a continuous sequence **TP1...TPn** are required.
- **LM** and **BM** are optional.
- If both LM and BM exist, the calculation sequence starts `LM → BM → SP`. If only one exists, it connects directly to SP. If neither exists, the sequence starts at SP.
- Area is always calculated only from `SP → TP1 → ... → TPn → SP`; LM/BM never affect area.

### Workflow
1. Upload an `.xlsx` file.
2. Select WGS 1984 UTM Zone 36N or 37N.
3. Select magnetic declination (8° or 9°).
4. Review the generated table and map preview.
5. Click **Generate Excel** to download the result.

The map preview converts the selected UTM coordinates to WGS84 for display on OpenStreetMap tiles. Bearing, distance, and area calculations continue to use the original UTM coordinates. Excel processing is performed locally in the browser.

---

## Українська
Браузерний інструмент для підготовки таблиць координат, азимутів і відстаней з Excel. Назви колонок можуть бути будь-якими: 1-ша колонка — назва точки, 2-га — Easting/X, 3-тя — Northing/Y.

### Обов'язкові точки
- **SP** та безперервна послідовність **TP1...TPn** є обов'язковими.
- **LM** і **BM** — необов'язкові.
- Якщо є LM і BM, послідовність починається `LM → BM → SP`. Якщо є лише одна з них, вона напряму з'єднується з SP. Якщо немає обох — розрахунок починається з SP.
- Площа завжди рахується тільки по контуру `SP → TP1 → ... → TPn → SP`; LM/BM на площу не впливають.

### Послідовність роботи
1. Завантажте `.xlsx`.
2. Оберіть WGS 1984 UTM Zone 36N або 37N.
3. Оберіть магнітне схилення (8° або 9°).
4. Перевірте готову таблицю та візуалізацію на карті.
5. Натисніть **Згенерувати Excel**.

Для карти координати з обраної UTM-зони тимчасово перетворюються у WGS84 та відображаються на підкладці OpenStreetMap. Азимути, відстані та площа продовжують рахуватися за вихідними UTM-координатами. Обробка Excel виконується локально у браузері.


## v10 / Версія v10

**EN:** The calculated site area remains visible in the web preview for geometry checking, but it is no longer included in the exported Excel workbook. The Excel output contains only the coordinate/bearing/distance table.

**UA:** Розрахована площа ділянки залишається у веб-перегляді для перевірки геометрії, але більше не додається до експортованого Excel. Готовий Excel містить лише таблицю координат, азимутів і відстаней.


## Map interaction / Робота з картою
The map preview supports mouse/touch panning, mouse-wheel and +/- zoom, pinch zoom on touch devices, and a Fit to polygon button. Area is not displayed in the preview or exported Excel.

Попередній перегляд карти підтримує переміщення мишею/дотиком, масштабування колесом та кнопками +/−, pinch zoom на сенсорних пристроях і кнопку «Показати весь полігон». Площа не відображається у Preview та не експортується в Excel.
