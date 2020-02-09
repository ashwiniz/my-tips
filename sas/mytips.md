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
