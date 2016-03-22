#Subway Data 2

##The Data
So for some reason I can't see the csv file which makes this a pain. So my first query will just be to search everything in the database to see if it has anything of good use. 

`    q_weather_table = """
    SELECT *
    FROM weather_data 
    """
    print pandasql.sqldf(q_weather_table.lower(), locals())
    print '**************DONE***********'`

This backfires a little as the browser isn't able to display all of the columns. 

so I modify the query to just have 'rain' since I'm guessing there is a rain yes (1) or no (0) column. 

`q_weather_table = """
    SELECT *
    FROM weather_data 
    """`

And it does return rain 0 or 1. So perfect. 

##The real Query

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