### Tabble:-1 - Calendar
```
Calendar = ADDCOLUMNS(
    CALENDARAUTO(),
"Month",FORMAT([Date],"MMM"),
"Month Index",MONTH([date]),
"Month_Year",FORMAT([Date],"mmm-yyyy"),
"Day", FORMAT([Date],"DDD"),
"Formate_date",FORMAT([Date],"DD-MMM-YYYY")
)
```
### Table:-2 - Estimate Commission Rate
```
Estimate Commission Rate = GENERATESERIES(0, 100, 1)
```
### Table:-3- Estimate Patient Amount
```
 Estimate Patient Amount = GENERATESERIES(1000, 99999999, 1)
```
### Table:-4 - Parameter
```
Parameter = GENERATESERIES(100, 9999999, 1)
```
### Table:-4 - Department
```
Department = SUMMARIZE(Staff,Staff[department_id])
```
