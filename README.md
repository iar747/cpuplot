# cpuplot

## Command Line Profiler of CPU Usage and Load Average.

![](cpuplot%20xlarge%20screenshot.png)


## Synopsis
Displays bar graphs to the terminal depicting the Total CPU Usage Percentage and the Total 1 Minute Load Average Percentage.  It also shows name of the process with the highest CPU utilization.

If the system has been in sleep mode, it displays the "ASLEEP" text.

Default wait interval between system readings is 5secs. But a different one can be passed in the command line with the **-i** argument.

**Build for MacOS bash.  A linux version coming soon.**

**Developer: Ismael Antadillas**



## Usage: 
**cpuplot -i [seconds] -w [small medium large xlarge]**

Where:

**-i interval time in seconds between CPU readings.**

**-w width of the output, "small", "medium", "large", "xlarge"**

Example: `cpuplot -i 9 -w xlarge`

This command will set the time intervals to 9 seconds and the view will show the plot bars for total % of CPU usage and total % of load average.


## Calculations:
As described in the man page for the "ps" command:
"The CPU utilization of the process is a decaying average over up to a
minute of previous (real) time.  Because the time base over which this
is computed varies (some processes may be very young), it is possible
for the sum of all %cpu fields to exceed 100%."

Because of the above some values for the "Total CPU Usage" may be over 100%.
When this happens, the bar plot will be truncated to 100%.

The 1 minute Load Average Percentage, is calculated dividing the 1 minute
Load Average by the number of Cores in the system.
