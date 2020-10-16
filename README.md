# CodeDepends ADAM

```r
library(CodeDepends)
tt = readScript(txt = "
library(dplyr)
ADSL <- data.frame(1:10); 
ADSL$var=1; 
ADAE = ADSL; 
funs = function(x) {NULL}; 
ADSL = funs(2);   
funs = function(x) {2};
ADAE$var=funs(ADSL); 
fff = function(y) y")

info <- getInputs(tt)

index = getVariableDepends("ADSL", info = info, asIndex = TRUE, checkLibraries = TRUE)

lapply(info[index], function(x) `@`(x, "code"))

index = getVariableDepends(c("ADSL","ADAE"), info = info, asIndex = TRUE, checkLibraries = TRUE)

lapply(info[index], function(x) `@`(x, "code"))
```r
