---
title: "DataCamp course: R practices"
author: "Mehrnoosh"
date: "6/30/2021"
output: 
  html_document: 
    keep_md: yes
---




## Practice 1: Creat a matrix

```r
# Creat star_wars_matrix
box_office <- c(460.998, 314.4, 290.475, 247.900, 309.306, 165.8)
region <- c("US", "non-US")
titles <- c("A New Hope", "The Empire Strikes Back", "Return of the Jedi")
               
star_wars_matrix <- matrix(box_office, nrow = 3, byrow = TRUE,
                           dimnames = list(titles, region))

# Creat star_wars_matrix2 as a matrix with data for the prequels trilogy
star_wars_matrix2 <- matrix(c(474.5, 552.5, 310.7, 338.7, 380.3, 468.5),
                            nrow = 3, byrow = TRUE, 
                            dimnames = list(c("The Phantom Menace", "Attack of the Clones", "Revenge of the Sith"), region))
```

## Practice 2: Adding rows/columns to a matrix

```r
# Combine both Star Wars trilogies in one matrix (i.e. add rows)
all_wars_matrix <- rbind(star_wars_matrix, star_wars_matrix2)

# The worldwide box office figures
worldwide_vector <- rowSums(all_wars_matrix)

# Bind the new variable worldwide_vector as a column to star_wars_matrix
all_wars_matrix <- cbind (all_wars_matrix, worldwide_vector)

# Total revenue for US and non-US
total_revenue_vector <- colSums(all_wars_matrix)

# Bind total_revenue_vector as a row to all_wars_matrix
all_wars_matrix <- rbind (all_wars_matrix, total_revenue_vector)

# Print out all_wars_matrix
all_wars_matrix
```

```
##                               US non-US worldwide_vector
## A New Hope               460.998  314.4          775.398
## The Empire Strikes Back  290.475  247.9          538.375
## Return of the Jedi       309.306  165.8          475.106
## The Phantom Menace       474.500  552.5         1027.000
## Attack of the Clones     310.700  338.7          649.400
## Revenge of the Sith      380.300  468.5          848.800
## total_revenue_vector    2226.279 2087.8         4314.079
```

## Practice 3: Selecting matrix elements

```r
# my_matrix[1,2] selects the element at the first row and second column.
# my_matrix[1:3,2:4] results in a matrix with the data on the rows 1, 2, 3 and columns 2, 3, 4.
# my_matrix[,1] selects all elements of the first column.
# my_matrix[1,] selects all elements of the first row.

# Select the non-US revenue for all movies
non_us_all <- all_wars_matrix[1:6, 2]

# Average non-US revenue
mean(non_us_all)
```

```
## [1] 347.9667
```

```r
# Select the non-US revenue for first two movies
non_us_some <- non_us_all [1:2]
  
# Average non-US revenue for first two movies
mean(non_us_some)
```

```
## [1] 281.15
```
