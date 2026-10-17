# Reasoning Before Execution

Write the rule behind each case before you commit your predictions. Replace
every placeholder line below with one to three sentences that name the rule
producing that case's value, type, length, and dimensions. One rule is enough.
After you run and find a miss, add a short correction entry under that case in a
later commit.

## P01
R uses type coercion to convert all elements of c(TRUE, 2L, 3.5) to the type double since it has higher in the coercion ladder, producing [1,2,3.5]. The result is a vector with length 3 and no dimensions.

## P02
This coerces all elements of c(1L, "2", TRUE) to character because character is higher in the coercion ladder than integer and logical. The result is ["1","2","TRUE"], with length 3 and no dimensions.

## P03
This recycles the shorter vector c(1L, 2L) to match the length of c(10L, 20L, 30L, 40L) during element-wise addition, producing [11,22,31,42]. The result has length 4 and no dimensions.

## P04
Positive indices select elements by position, in the order specified. Selecting positions 3 and 1 returns the named values third=9 and first=8, preserving their names. Since the selected values are integers, the result has type integer, length 2, and no dimensions.

## P05
Replace this line with the rule that decides this case.
The reason is that the -2L is saying that the second element is not included in the combined vector. Since the selected values are integers, the result has type integer, length 2, and no dimensions.

## P06
The is.na(x) | x > 10L condition selects elements that are either missing (NA) or greater than 10. The result is [NA, 12], with type integer, length 2, and no dimensions because logical indexing returns a vector containing the selected elements.

## P07
The factor() function converts the character values into a factor, storing 2 fields inside of it which is factor and levels. The result is factor["low","high","low"] with levels ["low","high","low"], with type string, length 3 since the factor has 3 elements. And also, no dimensions because it is a one-dimensional vector for the 2 fields.

## P08
The list() function stores elements of different types. The list contains two named fields, scores and label, so its type is a list, and the length is based on how many fields there are in the list which is 2, and dimensions are none.

## P09
Replace this line with the rule that decides this case.

## P10
Replace this line with the rule that decides this case.

## P11
Replace this line with the rule that decides this case.

## P12
Replace this line with the rule that decides this case.

## P13
Replace this line with the rule that decides this case.

## P14
Replace this line with the rule that decides this case.

## P15
Replace this line with the rule that decides this case.

## P16
Replace this line with the rule that decides this case.
