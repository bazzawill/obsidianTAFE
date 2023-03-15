### Get all fields
```powershell
| get-member #gets all fields
```

### Narrow by field
```powershell
| ?  -#alias for Where-Object
```


### Equality
``` powershell

-eq, -ieq, -ceq - #equals
-ne, -ine, -cne - #not equals
-gt, -igt, -cgt - #greater than
-ge, -ige, -cge - #greater than or equal
-lt, -ilt, -clt - #less than
-le, -ile, -cle - #less than or equal
```

### Matching
```Powershell

-like, -ilike, -clike - string matches wildcard pattern
-notlike, -inotlike, -cnotlike - string doesn't match wildcard pattern
-match, -imatch, -cmatch - string matches regex pattern
-notmatch, -inotmatch, -cnotmatch - string doesn't match regex pattern
```

### Replacement
```powershell

-replace, -ireplace, -creplace - #replaces strings matching a regex pattern
```

### Containment
```Powershell

-contains, -icontains, -ccontains - #collection contains a value
-notcontains, -inotcontains, -cnotcontains - #collection doesn't contain a value
-in - #value is in a collection
-notin - #value isn't in a collection
Type

-is - #both objects are the same type
-isnot - #the objects aren't the same type
```

### output into clipboard
```powershell
(Get-WmiObject -Class win32_OperatingSystem).serialnumber|Set-Clipboard
```

### XML to object
```powershell
[xml]$GpoXml=get-GPOReport -Name "Default Domain Policy" -ReportType xml
```

### Download file
```powershell
function Get-URL ($url){
    Invoke-WebRequest $url -OutFile $url.split("/")[-1]
}
```
or use `curl.exe -O`
