###INTRODUCTION

JSONVALUE is a friendly C++ class for parsing JSON string to C++ object, and creating a C++ representation of JSON string. Several advatages of this C++ JSON class are:

* strict and loose mode
* variant data type
* simple API
* depends on STL only.

Both ANSI and UNICODE strings are supported for parsing and stringification.

###USAGE

JSON C++ value, object and array can be created and added and retrieved using simple assignment operator (=) and object assignment operator ([]).

JSON string parsing support strict parsing as well as loose parsing via additional flags passed to ```Parse()``` function.

In loose parsing, user can opt to:

* allow unquote name
* allow white space control character
* allow single quote

In loose stringification, user can opt to:

* create unquote name
* create name with single quote
* pretty print output with TAB character or SPACE character
* output date as locale date

In strict mode:

* date is created in ISO date format: ```YYYY-MM-DD HH:MM:SS```
* all names and strings are double quoted


###EXAMPLES

Sample code to parse a JSON string:

Strict mode:
```c++
Parse(json_string);
```

Strict mode, with error messages: err is meaningful if Parse() returns false.

```c++
JSONERROR err;
Parse(json_string, 0, &err);
```

Loose mode: by default ```JSON_FLAG_LOOSE``` allow unquote name, white space control characters and single quote name. User can further restrict the level of looseness by passing different ```JSON_FLAG_xx``` values into ```Parse()``` function.

```c++
Parse(json_string, JSON_FLAG_LOOSE);
```
Loose mode, with error messages: err is meaningful if Parse() returns false.
```c++
JSONERROR err;
Parse(json_string, JSON_FLAG_LOOSE, &err);
```

Sample code to create JSON string:

```c++
JSONVALUE j;
j[_T("double")].Push(0.32);
j[_T("test")][_T("boolean")] = true;
string a;
j.ToString(a);
```

The default strict mode will generate the following JSON string:
```c++
{"double":[0.32],"test":{"boolean":true}}
```

User can further customize the output string by passing ```JSONFORMAT``` structure into ```ToString()``` function, which he can control the indent space (if ```JSON_FLAG_PRETTYPRINTSPACE``` is specified), floating point format and date format.

###NOTE
This code was originally developed for Ecava IGX WEB [SCADA](http://www.integraxor.com/), if you know what's SCADA then you may be interested to [download a copy](http://www.integraxor.com/download-igx.html) to see this peace of code performs in real life application.
