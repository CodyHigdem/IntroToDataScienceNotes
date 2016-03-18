#data wrangling

To import use `pandas.read_csv(path_to_csv)`

If we want to manipulate data we could do something like this

`import pandas

baseball_data = pandas.read_csv(path_to_csv)
baseball_data['nameFull'] = baseball_data['nameFirst'] + ' ' + baseball_data['nameLast']
baseball_data.to_csv(path_to_new_csv)`

