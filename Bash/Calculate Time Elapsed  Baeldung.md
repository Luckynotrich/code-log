## 1\. Overview[](https://www.baeldung.com/linux/bash-calculate-time-elapsed#overview)

**We define elapsed time for a block of code as how long that block takes to execute.** In this tutorial, we’re going to explore how to measure elapsed time in Linux.

## 2\. Using the _date_ Command[](https://www.baeldung.com/linux/bash-calculate-time-elapsed#using-the-date-command)

As we know, the [_sleep_](https://man7.org/linux/man-pages/man3/sleep.3.html) command waits for a specified number of seconds. We’ll use it as our sample block code because it lets us define how long our code block will take to run in a somewhat precise manner.

Let’s now calculate the time elapsed using _[date](https://www.baeldung.com/linux/date-command)_.

Let’s create an _elapsed\_time.sh_ script:

```bash
start=$(date +%s) sleep 5 sleep 7 end=$(date +%s) echo "Elapsed Time: $(($end-$start)) seconds"
```

We use _$()_ to initialize _start_ and _end_ variables. _$()_ is for command substitution. So, it runs the commands inside and captures the result in the corresponding variable.


Note that we **used _$(())_ for computing the result of arithmetic operations**.

Let’s now run our script:

```bash
$ ./elapsed_time.sh Elapsed Time: 12 seconds
```

## 3\. Using Internal Variable _$SECONDS_[](https://www.baeldung.com/linux/bash-calculate-time-elapsed#using-internal-variable-seconds)

We can use the Bash shell’s internal variable _$SECONDS_ to calculate the elapsed time. When referenced, **_$SECONDS_ outputs the number of seconds elapsed since the current shell was invoked**. Let’s then make another version of our _elapsed\_time.sh_ script:

```bash
SECONDS=0 sleep 5 sleep 7 echo "Elapsed Time (using \$SECONDS): $SECONDS seconds"
```

**We set the value of the _SECONDS_ variable to zero** before the code block starts. **Note that using a non-integer value will set it to zero.**

Once our example code block finishes, _$SECONDS_ contains the execution time for that code block. Note that in this case, there’s no need for arithmetic operations.

[![freestar](https://a.pub.network/core/imgs/fslogo-green.svg)](https://ads.freestar.com/?utm_campaign=branding&utm_medium=banner&utm_source=baeldung.com&utm_content=baeldung_leaderboard_mid_2)

[![freestar](https://a.pub.network/core/imgs/fslogo-green.svg)](https://ads.freestar.com/?utm_campaign=branding&utm_medium=banner&utm_source=baeldung.com&utm_content=baeldung_leaderboard_mid_2)

Let’s run our script again and check the result:

```bash
$ ./script.sh Elapsed Time (using $SECONDS): 12 seconds
```

## 4\. Using Bash Shell’s _TIMEFORMAT_[](https://www.baeldung.com/linux/bash-calculate-time-elapsed#using-bash-shells-timeformat)

We can also use the Bash shell’s [_TIMEFORMAT_](https://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash.html#index-TIMEFORMAT) combined with the _[time](https://www.baeldung.com/linux/time-command)_ command to calculate the exact time spent on a block of commands with milliseconds precision. Let’s create another version of our calculation script:

```bash
TIMEFORMAT='It took %R seconds.' time { sleep 5 sleep 7 }
```

We should wrap our commands in _time{}_ after we define the _TIMEFORMAT_ string. The _TIMEFORMAT_ is a string format that will be printed after the execution of the block code inside the _time{}_ wrapper finishes. The **_%R_ specifies to print the elapsed time in seconds with milliseconds precision**.

Let’s test our script:

```bash
$ ./elapsed_time.sh It took 12.008 seconds.
```

In _TIMEFORMAT_, we can **use a digit before _R_ to specify the number of fractional digits** to print after the decimal point. Therefore, a value of zero (_%0R_) causes no decimal point to be printed in the elapsed time output:

[![freestar](https://a.pub.network/core/imgs/fslogo-green.svg)](https://ads.freestar.com/?utm_campaign=branding&utm_medium=lazyLoad&utm_source=baeldung.com&utm_content=baeldung_leaderboard_mid_3)

```bash
TIMEFORMAT='It took %0R seconds.' time { sleep 5 sleep 7 }
```

Let’s run our script again:

```bash
$ ./elapsed_time.sh It took 12 seconds.
```

**The default value for the optional digit specifying the precision is 3**. Note that if we specify any number greater than 3, it’ll be replaced with 3.

It worth noting that with the _time_ command, we can also calculate the CPU time spent in user mode or system mode.

## 5\. Elapsed Time in Nanoseconds[](https://www.baeldung.com/linux/bash-calculate-time-elapsed#elapsed-time-in-nanoseconds)

All these methods calculate the elapsed time in seconds or milliseconds. If we want the elapsed time in nanoseconds, we can use **t****he _date_ command’s** **_%N_ option**:

```bash
start=$(date +%s%N) sleep 5 sleep 7 end=$(date +%s%N) echo "Elapsed time: $(($end-$start)) ns"
```

Let’s check the result:

```bash
$ ./elapsed_time.sh Elapsed time: 12023674735 ns
```

**Note that if we want to have the time in milliseconds again, we should divide the nanosecond output by 1 million**:

```bash
start=$(date +%s%N) sleep 5 sleep 7 end=$(date +%s%N) echo "Elapsed time: $(($(($end-$start))/1000000)) ms"
```

Now, let’s run this new version:

```bash
$ ./elapsed_time.sh Elapsed time: 12022 ms
```

## 6\. Conclusion[](https://www.baeldung.com/linux/bash-calculate-time-elapsed#conclusion)

In this article, we measured the elapsed time for a series of commands.

[![freestar](https://a.pub.network/core/imgs/fslogo-green.svg)](https://ads.freestar.com/?utm_campaign=branding&utm_medium=banner&utm_source=baeldung.com&utm_content=baeldung_incontent_1)

First, we calculated the elapsed time using the _date_ command. Then, we used the _$SECONDS_ variable, which is the Bash shell’s internal variable that holds the elapsed time since the current shell started.

After that, we used the _TIMEFORMAT_ built-in variable along with the _%R_ option for calculating the elapsed time with millisecond precision.

Finally, we introduced the _date_ command’s _%N_ option to calculate the elapsed time down to nanoseconds.