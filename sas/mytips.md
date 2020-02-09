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
