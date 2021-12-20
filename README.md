# processing-text
An overview of processing text

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
## Using truncation, awk and sed

## Using regex
