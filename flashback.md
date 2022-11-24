\section{Flashback}

# qdc2
## Orcl dg config steps:



```
```
Look! You can see my backticks.
```
```


```
function test() {
  console.log("notice the blank line before this function?");
}
```


```ruby
require 'redcarpet'
markdown = Redcarpet.new("Hello World!")
puts markdown.to_html
```


\begin{lstlisting}
$date_2
Sat Jun  1 14:31:01 CEST 2019
\end{lstlisting}

'''
Check CURRENT SCN of the Oracle Database
'''

First: Check CURRENT SCN of the Oracle Database

Following are the way to check current SCN in Oracle Database:

1. Fetch the current SCN number in \url{v$database} view.

'''
\url{Select CURRENT_SCN from v$database;}
'''

\url{SQL> Select CURRENT_SCN from v$database;}

\url{CURRENT_SCN}
-----------
3208426

2. Get from flashback package.

\url{select dbms_flashback.get_system_change_number from dual;}


\url{SQL> select dbms_flashback.get_system_change_number from dual;}

\url{GET_SYSTEM_CHANGE_NUMBER}
------------------------
3208440

3. Get the SCN from \url{timestamp_to_scn} function.

\url{select timestamp_to_scn(sysdate) from dual;}

 
\url{SQL> select timestamp_to_scn(sysdate) from dual;}

\url{TIMESTAMP_TO_SCN(SYSDATE)}
-------------------------
3208466

Example of \url{TIMESTAMP_TO_SCN & SCN_TO_TIMESTAMP} function

\url{select sysdate, timestamp_to_scn(sysdate) from dual;}

\url{SYSDATE TIMESTAMP_TO_SCN(SYSDATE)}
------------------- -------------------------
02-04-2019 15:25:05 3208525

\url{select scn_to_timestamp(3208525) from dual;}

\url{SCN_TO_TIMESTAMP(3208525)}
-----------------------------------------------
02-APR-19 03.25.03.000000000 PM

\url{select timestamp_to_scn(to_timestamp('02-04-2019 15:25:05','DD-MM-YYYY HH24:MI:SS')) "SCN" from dual;}

\url{SCN}
----------
3208525
