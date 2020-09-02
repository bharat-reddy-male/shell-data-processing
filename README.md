# Shell-Data-Processing : Word Count

## Getting data from a website using curl

Select any website of your wish and copy the URL and paste it in the command below as follows:

`curl "URL for Website" -O "file name to be saved"`

An example is below:

`curl "http://shakespeare.mit.edu/Poetry/elegy.html" -O "data.
txt"`

If the URL uses HTTPS, first run the command mentioned below to establish a secure connection:

`[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12`

## Cleaning up the data

1: Open a bash window in the current working directory and run the command mentioned below to clear most of the [HTML tags](https://www.w3schools.com/TAGS/default.ASP)

`sed -E 's/<[^>]*>/''/g' data.txt > result.txt`

Here the data.txt is the input file name and the result.txt is the output file name with most of the HTML tags removed.

2: Now clear the empty spaces using the "[tr](https://www.geeksforgeeks.org/tr-command-in-unix-linux-with-examples/)" command in linux. 

`tr ' ' '\12' < result.txt`

Here we cannot keep the replacement string as empty since the operation will return an error if we do hence we use and ASCII replacement for newline \12.


3: Now we sort the remaining words in alphabetical order using the [sort](https://www.geeksforgeeks.org/sort-command-linuxunix-examples/) command

`tr ' ' '\12' < returnedfile | sort`

4: Now we start counting the unique values using the [uniq](https://www.geeksforgeeks.org/uniq-command-in-linux-with-examples/) command.

`tr ' ' '\12' < returnedfile | sort | uniq -c`

5: Now sort the output in numerical order using the sort command's "-nr" flag.

`tr ' ' '\12' < returnedfile | sort | uniq -c | sort -nr`

6: Now the words are numerically sorted and we have to save this into a file so redirect the output of the above command to a file.

`tr ' ' '\12' < returnedfile | sort | uniq -c | sort -nr > result.txt`

The file will now contain the word count for the website chosen.


Links for commands were taken from [Geeks for Geeks](https://www.geeksforgeeks.org/)
