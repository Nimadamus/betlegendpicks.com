# Google Sheets Formula for Auto-Calculating Units

## Problem
When you grade games in column K (GRADE UNIT), the units in column E should automatically calculate based on whether the pick won, lost, or pushed.

## Solution

In your Google Sheets master sheet, **Column E (Units)** should have the following formula starting from row 2:

```excel
=IF(K2="", "", IF(K2="P", 0, IF(K2="W", IF(LEFT(C2,1)="+", D2*VALUE(MID(C2,2,10))/100, IF(LEFT(C2,1)="-", D2*100/VALUE(MID(C2,2,10)), D2)), IF(K2="L", -D2, ""))))
```

### How to Apply This Formula:

1. **Open your Google Sheet** (ID: 1izhxwiiazn99SRqcK8QpUE4pfvDRIFpgSyw5ZlMsvmY)

2. **Click on cell E2** (the first data row in the Units column)

3. **Paste the formula above**

4. **Press Enter**

5. **Copy the formula down** to all rows:
   - Click on cell E2 again
   - Click the small blue square in the bottom-right corner of the cell
   - Drag it down to cover all your data rows (or double-click it to auto-fill)

### What This Formula Does:

**Column References:**
- **C** = Odds (e.g., "+150" or "-110")
- **D** = Confidence/Units Risked (e.g., "1" or "2")
- **K** = GRADE UNIT (W/L/P)
- **E** = Units (calculated result)

**Logic:**
1. If K (GRADE UNIT) is **empty**: Display nothing
2. If K = **"P" (Push)**: Display 0 units
3. If K = **"W" (Win)**:
   - For **positive odds** (+150): Units = Confidence × (Odds/100)
     - Example: 1 unit at +150 = 1 × (150/100) = +1.50 units
   - For **negative odds** (-110): Units = Confidence × (100/Odds)
     - Example: 1 unit at -110 = 1 × (100/110) = +0.91 units
4. If K = **"L" (Loss)**: Units = -Confidence
   - Example: 1 unit risked = -1.00 units

### Example Results:

| Odds | Confidence | GRADE UNIT | Units (Result) |
|------|-----------|------------|----------------|
| +150 | 1         | W          | +1.50          |
| -110 | 1         | W          | +0.91          |
| +200 | 2         | W          | +4.00          |
| -150 | 1         | L          | -1.00          |
| +120 | 1         | P          | 0.00           |

### Alternative: Simpler Formula (if odds are always in American format)

If you want a slightly different calculation or if the above doesn't work perfectly with your odds format, try this simpler version:

```excel
=IF(K2="", "", IF(K2="P", 0, IF(K2="W", D2, IF(K2="L", -D2, ""))))
```

This version:
- Win = +Confidence
- Loss = -Confidence
- Push = 0

Then you can manually adjust for odds multipliers if needed.

### Troubleshooting:

If the formula doesn't work:
1. Make sure your **Odds column (C)** has values like "+150" or "-110" with the +/- symbol
2. Make sure your **Confidence column (D)** has numeric values only (1, 2, etc.)
3. Make sure your **GRADE UNIT column (K)** has only "W", "L", or "P"
4. Check that there are no extra spaces in any cells

### After Applying:

Once you apply this formula, whenever you:
1. Enter a pick with odds and confidence
2. Grade it by entering "W", "L", or "P" in column K

The Units column (E) will **automatically calculate** based on the result!
