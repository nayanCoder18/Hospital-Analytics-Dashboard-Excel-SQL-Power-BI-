```
Admitted_status = 
"Total " &
CALCULATE(
    COUNTROWS(patient_info),
    patient_info[patient_status] = "Admitted"
) &
" Patient Admitted."
```
```
// 2
Admitted_status = 
"Total " &
CALCULATE(
    COUNTROWS(patient_info),
    patient_info[patient_status] = "Admitted"
) &
" Patient Admitted."
```
:smile:
