#### Summarizing Data

Don't sort and sum (because resorting will break this).  Also, don't filter and sum (excel still counts hidden rows) , use sumif  

= left(B2,5) takes first five letters

keep original data, put reformatted data in new column (reformatting may be incorrect)

fixing zip codes, adding back leading zero:
=rept('0','5-len(A2))&""&A2
or use value(ZipCode) in Vlookup

Sumifs to sum over a column with several conditions

Partially fixed references to row, column headers

use iferror as wrap of getpivotdata function to catch values not found in pivot table

#### How to write a report
frequency: claim count / earned exposure
severity: incurred loss / claim count
pure premium: incurred loss / earned exposure OR frequency \* severity

Create pivot table.  Create columns to use as condition values in getpivotdata function.  white out repeated indices, code columns by color, green low red high, add borders, thin interior and thick outside border.

Black background, white text header, white background indices, centered indices, formatted values (percent, dollar, etc.)

Hide rows with no relevant data, making note below table.  white background around note.
