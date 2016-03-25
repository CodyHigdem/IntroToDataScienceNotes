#Subway Data 2

##The Data
So for some reason I can't see the csv file which makes this a pain. So my first query will just be to search everything in the database to see if it has anything of good use. 

`q_weather_table = """
    SELECT *
    FROM weather_data
    S"""
    print pandasql.sqldf(q_weather_table.lower(), locals())
    print '**************DONE***********'`

This backfires a little as the browser isn't able to display all of the columns. 

so I modify the query to just have 'rain' since I'm guessing there is a rain yes (1) or no (0) column. 

`q_weather_table = """
    SELECT *
    FROM weather_data 
    """`

And it does return rain 0 or 1. So perfect. 

###The real Query

   `weather_data = pandas.read_csv(filename)
    q_weather_table = """
    SELECT rain 
    FROM weather_data 
    """
    print pandasql.sqldf(q_weather_table.lower(), locals())
    print '**************DONE***********'
    q = """
    SELECT count(*) 
    FROM weather_data 
    WHERE rain=1;
    """
    

    
    #Execute your SQL command against the pandas frame
    rainy_days = pandasql.sqldf(q.lower(), locals())

    return rainy_days`

and it returns:
`    rain
0      0
1      0
2      0
3      1
4      0
5      0
6      0
7      0
8      0
9      0
10     0
11     0
12     0
13     0
14     1
15     1
16     1
17     1
18     1
19     1
20     1
21     0
22     1
23     0
24     0
25     0
26     0
27     0
28     0
29     1
**************DONE***********
   count(*)
0        10
Good job! Your code worked perfectly.


   count(*)
0        10`

## 2.2

   This function should run a SQL query on a dataframe of
    weather data.  The SQL query should return two columns and
    two rows - whether it was foggy or not (0 or 1) and the max
    maxtempi for that fog value (i.e., the maximum max temperature
    for both foggy and non-foggy days).  The dataframe will be 
    titled 'weather_data'. You'll need to provide the SQL query.


So the trick here is to return two columns and two rows. The first is if fog is 0 or 1. Then the max temperture (maxtempi) for the fog value of 0 and 1. 

So scrolling throug the sql docs GROUP BY may be the best: The GROUP BY statement is used in conjunction with the aggregate functions to group the result-set by one or more columns.


So let's give it a try. 

`import pandas
import pandasql


def max_temp_aggregate_by_fog(filename):
    '''
    This function should run a SQL query on a dataframe of
    weather data.  The SQL query should return two columns and
    two rows - whether it was foggy or not (0 or 1) and the max
    maxtempi for that fog value (i.e., the maximum max temperature
    for both foggy and non-foggy days).  The dataframe will be 
    titled 'weather_data'. You'll need to provide the SQL query.
    
    You might also find that interpreting numbers as integers or floats may not
    work initially.  In order to get around this issue, it may be useful to cast
    these numbers as integers.  This can be done by writing cast(column as integer).
    So for example, if we wanted to cast the maxtempi column as an integer, we would actually
    write something like where cast(maxtempi as integer) = 76, as opposed to simply 
    where maxtempi = 76.
    
    You can see the weather data that we are passing in below:
    https://www.dropbox.com/s/7sf0yqc9ykpq3w8/weather_underground.csv
    '''
    weather_data = pandas.read_csv(filename)

    q = """
    SELECT fog, max(cast (maxtempi as integer))
    FROM weather_data
    GROUP BY fog
    """
    
    #Execute your SQL command against the pandas frame
    foggy_days = pandasql.sqldf(q.lower(), locals())
    return foggy_days`


## Problem 2.3

    This function should run a SQL query on a dataframe of
    weather data.  The SQL query should return one column and
    one row - the average meantempi on days that are a Saturday
    or Sunday (i.e., the the average mean temperature on weekends).
    The dataframe will be titled 'weather_data' and you can access
    the date in the dataframe via the 'date' column.
    
    You'll need to provide  the SQL query.

    You might also find that interpreting numbers as integers or floats may not
    work initially.  In order to get around this issue, it may be useful to cast
    these numbers as integers.  This can be done by writing cast(column as integer).
    So for example, if we wanted to cast the maxtempi column as an integer, we would actually
    write something like where cast(maxtempi as integer) = 76, as opposed to simply 
    where maxtempi = 76.
    
    Also, you can convert dates to days of the week via the 'strftime' keyword in SQL.
    For example, cast (strftime('%w', date) as integer) will return 0 if the date
    is a Sunday or 6 if the date is a Saturday.


    We need to return 1 column and 1 row. The AVERAGE temperature (meantempi) on days that are saturday and sunday. 
    So first let's just get the average. Which should be used by AVG.

    So we're no longer groupong but we're selecting these data where it's a saturday or a sunday. In the instructions we get the hint: 
        Also, you can convert dates to days of the week via the 'strftime' keyword in SQL.
        For example, cast (strftime('%w', date) as integer) will return 0 if the date
        is a Sunday or 6 if the date is a Saturday.
    so cast(strftime('w%', 0)) AND cast(strftime('w%', 6)) will get us the averages of all Sundays and Averages of all Saturdays

    In SQL we can use cast an strftime. The trick is in which order? If you cast inside it's an error, so it looks like cast needs to be on the outside. 

`import pandas
import pandasql

def avg_weekend_temperature(filename):
    '''
    This function should run a SQL query on a dataframe of
    weather data.  The SQL query should return one column and
    one row - the average meantempi on days that are a Saturday
    or Sunday (i.e., the the average mean temperature on weekends).
    The dataframe will be titled 'weather_data' and you can access
    the date in the dataframe via the 'date' column.
    
    You'll need to provide  the SQL query.
    
    You might also find that interpreting numbers as integers or floats may not
    work initially.  In order to get around this issue, it may be useful to cast
    these numbers as integers.  This can be done by writing cast(column as integer).
    So for example, if we wanted to cast the maxtempi column as an integer, we would actually
    write something like where cast(maxtempi as integer) = 76, as opposed to simply 
    where maxtempi = 76.
    
    Also, you can convert dates to days of the week via the 'strftime' keyword in SQL.
    For example, cast (strftime('%w', date) as integer) will return 0 if the date
    is a Sunday or 6 if the date is a Saturday.
    
    You can see the weather data that we are passing in below:
    https://www.dropbox.com/s/7sf0yqc9ykpq3w8/weather_underground.csv
    '''
    weather_data = pandas.read_csv(filename)

    q = """
    SELECT AVG(cast(meantempi as integer))
    FROM weather_data
    WHERE cast (strftime('%w', date) as integer) = 0
          OR cast (strftime('%w', date) as integer) = 6

    """
    
    #Execute your SQL command against the pandas frame
    mean_temp_weekends = pandasql.sqldf(q.lower(), locals())
    return mean_temp_weekends`

## 2.4

    This function should run a SQL query on a dataframe of
    weather data. More specifically you want to find the average
    minimum temperature (mintempi column of the weather dataframe) on 
    rainy days where the minimum temperature is greater than 55 degrees.

    This is a very straight forward attempt. 
    1. get average lowest temperature (minitemp)
    2. when it's raining (rainy = 1)
    3. and if the low temp is greater than 55 (mintemp > 55)

        `q = """
    SELECT AVG(cast(mintempi as integer))
    FROM weather_data
    WHERE rain=1 AND mintempi > 55
    """`


## 2.5
    
    This next task seems a bit of a jump but they give you a really good tutorial: https://docs.google.com/document/d/1S4Gk42ZPBKAUZh7IPbqyzq_vk18oCvcniVcA4byBXCE/pub

    So check that out and you can solve it.



`import csv

def fix_turnstile_data(filenames):
    '''
    Filenames is a list of MTA Subway turnstile text files. A link to an example
    MTA Subway turnstile text file can be seen at the URL below:
    http://web.mta.info/developers/data/nyct/turnstile/turnstile_110507.txt
    
    As you can see, there are numerous data points included in each row of the
    a MTA Subway turnstile text file. 

    You want to write a function that will update each row in the text
    file so there is only one entry per row. A few examples below:
    A002,R051,02-00-00,05-28-11,00:00:00,REGULAR,003178521,001100739
    A002,R051,02-00-00,05-28-11,04:00:00,REGULAR,003178541,001100746
    A002,R051,02-00-00,05-28-11,08:00:00,REGULAR,003178559,001100775
    
    Write the updates to a different text file in the format of "updated_" + filename.
    For example:
        1) if you read in a text file called "turnstile_110521.txt"
        2) you should write the updated data to "updated_turnstile_110521.txt"

    The order of the fields should be preserved. Remember to read through the 
    Instructor Notes below for more details on the task. 
    
    In addition, here is a CSV reader/writer introductory tutorial:
    http://goo.gl/HBbvyy
    
    You can see a sample of the turnstile text file that's passed into this function
    and the the corresponding updated file in the links below:
    
    Sample input file:
    https://www.dropbox.com/s/mpin5zv4hgrx244/turnstile_110528.txt
    Sample updated file:
    https://www.dropbox.com/s/074xbgio4c39b7h/solution_turnstile_110528.txt
    '''
    for name in filenames:
        # your code here`

## 2.6

    Write a function that takes the files in the list filenames, which all have the 
    columns 'C/A, UNIT, SCP, DATEn, TIMEn, DESCn, ENTRIESn, EXITSn', and consolidates
    them into one file located at output_file.  There should be ONE row with the column
    headers, located at the top of the file. The input files do not have column header
    rows of their own.

    


