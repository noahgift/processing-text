# processing-text
An overview of processing text


![IMG_07E48EAC62FD-1](https://user-images.githubusercontent.com/58792/146846349-c92329aa-4369-422c-a649-e572bc4ef492.jpeg)


## Using grep, cut, sort and unique

Exploratory data analysis with the CLI

### Using Grep

```bash

# Count the occurrences of phrase
grep -c bad
grep -c plastic

# How many negative reviews?
grep -c NEGATIVE amazon_reviews_appliances_5k_with_sentiment.txt

# How many positive reviews?
grep -c POSITIVE amazon_reviews_appliances_5k_with_sentiment.txt

```

### Using diff

```bash

#using diff shows the following
diff fruit1.txt fruit2.txt 

< strawberry
---
> peach
```

### Using uniq

```bash

#find unique words
uniq fruit1.txt 

cherry
pear
strawberry
apple

#count unique words
uniq -c fruit1.txt 

      1 cherry
      1 pear
      1 strawberry
      2 apple


```

### Using sort

```bash

# original order
cat fruit1.txt 

cherry
pear
strawberry
apple

# sorted order

sort fruit1.txt 

apple
apple
cherry
pear
strawberry

```

### Using cut

```bash

#Look at a few lines
head amazon_reviews_appliances_5k_with_sentiment.txt

#Now just grap the sentiment analysis
cat amazon_reviews_appliances_5k_with_sentiment.txt | rev | cut -d, -f1 | rev 

```
## Using truncation, transliteration awk and sed

### Truncate

```bash

#shuf is your friend for truncating for data science
# Randomly shuffles
shuf -n 10 amazon_reviews_appliances_5k_with_sentiment.txt | wc -l
shuf -n 10 amazon_reviews_appliances_5k_with_sentiment.txt > 10lines.txt

#run man shuf to see more

## You can also transliterate
echo "lower" | tr a-z A-Z

## You can combine truncate and transliterate together

shuf -n 1 amazon_reviews_appliances_5k_with_sentiment.txt | tr a-z A-Z

```

### Using sed (stream editor)

```bash

#Replace occurrences of MIXED with NEGATIVE
echo "MIXED" | sed 's/MIXED/NEGATIVE/'

shuf -n 200 amazon_reviews_appliances_5k_with_sentiment.txt | sed 's/MIXED/NEGATIVE/'

#how many negative/positive/mixed do we see with random sampling
shuf -n 200 amazon_reviews_appliances_5k_with_sentiment.txt | sed 's/MIXED/NEGATIVE/'| grep -c NEGATIVE
62
```
### Using AWK

A programming language built at Bell Labs in the 1970s.  Simple [examples here](https://www.gnu.org/software/gawk/manual/html_node/Very-Simple.html).

*condition { action }*

```bash

#only show entries with 10 or fewer fields
shuf -n 200 amazon_reviews_appliances_5k_with_sentiment.txt | sed 's/MIXED/NEGATIVE/'| awk 'NF < 10'

3568,US,32787845,R34E6LZXX7AZVG,B001DHKBP8,606598582,"Whirlpool Stove Knob Kit, 814362",Major Appliances,4,0,0,N,Y,Four Stars,great products,8/3/15,POSITIVE

```

## Using regex
