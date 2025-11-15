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
Admitted_status = 
"Total " &
CALCULATE(
    COUNTROWS(patient_info),
    patient_info[patient_status] = "Admitted"
) &
" Patient Admitted."
```
```
Calender_icon = "https://i.ibb.co/jvLKN8CT/calendar.png"
```
```
Check_icon = "https://i.ibb.co/DP0Zcc2V/checklist.png"
```
```
Discharged_patient = 

CALCULATE(
    COUNTROWS(patient_info),
    patient_info[patient_status] = "Discharged"
) 
```
```
Discharged_per = DIVIDE([Discharged_patient],[Patient_count])
```
```
Doctor_commission_amt = [Total_bill_amount] * [Doctor_commission_rate]
```
```
Doctor_commission_rate = 0.1
```
```
Doctor_fees = CALCULATE(SUM(Bills[Value]),Bills[Charges_type] = "Doctor")
```
```
Estiamte_commission = 
var patient_amount = MAX('3- Estimate Patient Amount'[Estimate Patient Amount])
var commission_rate = MAX('2- Estimate Commission Rate'[Estimate Commission Rate])
 var commisson_per = DIVIDE(commission_rate,100)

RETURN patient_amount * commisson_per
```
```
Patient_count = DISTINCTCOUNT(patient_info[patient_id])
```
```
Patient_Phone_numebr = SELECTEDVALUE(patient_info[patient_phone],"Not available")
```
```
satisfaction_rating star rating = 
VAR __MAX_NUMBER_OF_STARS = 5
VAR __MIN_RATED_VALUE = 0
VAR __MAX_RATED_VALUE = 5
VAR __BASE_VALUE = SUM('patient_info'[satisfaction_rating])
VAR __NORMALIZED_BASE_VALUE =
	MIN(
		MAX(
			DIVIDE(
				__BASE_VALUE - __MIN_RATED_VALUE,
				__MAX_RATED_VALUE - __MIN_RATED_VALUE
			),
			0
		),
		1
	)
VAR __STAR_RATING = ROUND(__NORMALIZED_BASE_VALUE * __MAX_NUMBER_OF_STARS, 0)
RETURN
	IF(
		NOT ISBLANK(__BASE_VALUE),
		REPT(UNICHAR(9733), __STAR_RATING)
			& REPT(UNICHAR(9734), __MAX_NUMBER_OF_STARS - __STAR_RATING)
	)
```
```
surgery_Status_icon = 
IF(
    SELECTEDVALUE(
        patient_info[surgery_status])="Completed",[Check_icon],[Calender_icon])
```
```
Target = 100
```
```
Total_bill_amount = 
var discount =CALCULATE(SUM(Bills[Value]),Bills[Charges_type] = "discount")
VAR total_amount= SUM(Bills[Value])
RETURN total_amount - discount
```
```
Total_med_sale_qty = SUM(medicine_patient[qty])
```
```
Total_stock_QTY = SUM(Medical_stock_info[stock_qty])
```


