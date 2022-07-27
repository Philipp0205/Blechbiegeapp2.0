# Java -version wrong 
ou're probably have java.exe copied over to one of system paths (AFAIK that's Java installer default behavior). 

Check path of java.exe exe with 
`for %I in (java.exe) do @echo %~$PATH:I`  (cmd )

