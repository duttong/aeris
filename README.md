<h2>NOAA Aeris N2O/CO Instrument Software</h2>

<p>The main program to run the Aeris instrument equipped with a multi-position Valco valve is <strong>aeris.py</strong>. Run <strong>aeris.py -h</strong> to see the various options for the program.</p>

<p>Run <strong>aeris.py</strong> without options to use the valve sequence programed in the config.py file. The <strong>aeris.py</strong> program will store the output of the Aeris instrument to a .csv file. To read the csv file into a pandas data frame.</p>
<pre><code>df = pd.read_csv(file, infer_datetime_format=True, parse_dates=True, index_col='datetime')</code></pre>
<p>To calculate statistics on the second half of each SSV position after a valve switch.</p>
<pre><code>
<p>1. df2 = df.groupby(['seq_count','ssv'], as_index=False).apply(lambda x: x.iloc[x.ssv.size//2:]).reset_index(level=0, drop=True)
<p>2. df2.groupby(['seq_count','ssv']).mean() or .std()
</code></pre>

<h3>Initial Setup</h3>
<p>1. Edit the <strong>config.py</strong> file with the Valco valve and Aeris serial port settings.
<p>2. Change the valve sequence and duration in <strong>config.py</strong>.
