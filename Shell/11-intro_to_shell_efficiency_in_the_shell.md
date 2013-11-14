## Timing Scripts and Working with Background Jobs ##

### Time settings

date = view & modify time (on your computer)
View:
      date “+%H” --> If it's 9 am, then it will show 09
      date “+%H:%M:%Ss” = (hours, minutes, seconds)
      %Y = years

      Modify:
      Month | Day | Hours | Minutes | Year

      sudo date 031423421997 = March 14th 1997, 23:42

### Executing programs at other times

use 'at' to execute programs in the future
Step 1, write in the terminal: at <timeOfExecution> ENTER ex --> at 16:45 or at 13:43 7/23/11 (to be more precise) or after a certain delay:
      at now +5 minutes (hours, days, weeks, months, years)
Step 2: <ENTER COMMAND> ENTER
      repeat step 2 as many times you need
Step 3: CTRL D to close input
atq = show a list of jobs waiting to be executed
atrm = delete a job n°<x>
ex (delete job #42) --> atrm 42
sleep = pause between commands
      with ';' you can chain commands, ex: touch file; rm file
you can make a pause between commands (minutes, hours, days) ex --> touch file; sleep 10; rm file <-- 10 seconds
crontab = execute a command regularly
      -e = modify the crontab
      -l = view current crontab
      -r = delete you crontab
In crontab the syntax is
<Minutes> <Hours> <Day of month> <Day of week (0-6,
0 = Sunday)> <COMMAND>
ex, create the file movies.txt every day at 15:47: 47 15 * * * touch /home/bob/movies.txt
* * * * * --> every minute
at 5:30 in the morning, from the 1st to 15th each month:
30 5 1-15 * *
at midnight on Mondays, Wednesdays and Thursdays:
0 0 * * 1,3,4
every two hours:
0 */2 * * *
every 10 minutes Monday to Friday:
*/10 * * * 1-5


### Execute programs in the background

Add a '&' at the end of a command
      ex --> cp bigMovieFile.mp4 &

nohup: ignores the HUP signal when closing the console (process will still run if the terminal is closed)
      ex --> nohup cp bigMovieFile.mp4

jobs = know what is running in the background

fg = put a background process to foreground
      ex: fg (process 1), f%2 (process 2) f%3, ...

& (see "man bash”,
section "SHELL GRAMMAR")
bg (bash builtin)
nohup

### screen


