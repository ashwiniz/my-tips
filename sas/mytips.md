# sas tips
---

- clear sas result viewer output 
```
ODS HTML CLOSE;
ODS HTML;
```
reference: https://kb.iu.edu/d/bbpr

- LOG CLEAR
```
CTRL + E
```

- keep and obs in set statement
```
data x;
set y (obs = 10 keep = enrolid);
run;
```
- Group by sum 
- example: identifying whether andro = 1 if that enrolid had acne = 1 and alo = 1 at any point
```
data abhi_tmp2;
	set abhi_tmp1;
	by enrolid;
	if first.enrolid then sum_acne = 0;
		sum_acne + acne;
	if first.enrolid then sum_alo = 0;
		sum_alo + alo;
	if sum_acne * sum_alo > 0 then andro = 1;
	if andro = 1 then output;
run;
```
- merge datasets
```
proc sort data = x;
by id ;
run;
proc sort data = y;
by = id;
run;

data tmp;
merge x y;
by id;
run;
```
- Measure of association macro- returns relrisk/riskdiff
```
%macro assoc(ref,exposed);
PROC FREQ DATA=hw3.merge_mcc1_age order=formatted;
tables bene_race_cd2*anyhosp/relrisk riskdiff cmh;
where bene_race_cd2 in (&ref,&exposed);
run;
%mend;
%assoc(1,2);
%assoc(1,5);
%assoc(1,3);
```
-Create global variables for paths to datasets and code that can be used throughout session*/
```
%let DataPath=C:\Users\JANA\Desktop\Professional\Teaching\EPID404 - JH\2018\Assignments\Datasets\Medicare claims;
%let CodePath=C:\Users\JANA\Desktop\Professional\Teaching\EPID404 - JH\2018\Assignments\HW3;
libname claims "&DataPath";
```

- runs code saved in another file for example some macro
```
%include "&CodePath\MedClaimsFormats_HW3update.sas";
```

- case statement in sas

```
CASE
    WHEN condition1 THEN result1
    WHEN condition2 THEN result2
    WHEN conditionN THEN resultN
    ELSE result
END; 
```
