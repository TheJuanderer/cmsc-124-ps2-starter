# Vector and Scalar Evaluation

`clean_scores_vector()`
The function copies the input with scores[], so the original and its names stay untouched. The logical index in return_vec[is.na(return_vec)] <- 0 overwrites every NA in one subassignment so basically you dont need to loop throughout return_vec. Next, pmin(2 * return_vec, 20) doubles every element and caps each at 20 in one expression it works even if the values are 0 since 0 * 20 is 0.


`clean_scores_scalar()`
This function builds a vector out with setNames(as.double(scores), names(scores)), which forces double type while keeping the names. Then a loop then handles one element per pass. It reads the value <- out[[i]], then it checks if the value is NA; if it is, replace an NA with 0. After that it applies pmin(2 * value, 20) to the value and finally, writes back with out[[i]] <- value. 

## Which operations in the vector version act on all elements at once?
The operation ```return_vec[is.na(return_vec)] <- 0``` runs through the elements
instantly and replaces any NA value. 
The operation ```return_vec <- pmin(2 * return_vec, 20)```, runs the same but instead multiplying any non-NA value by 2, lowering it to 20 if greater than it. 

## Where does the scalar loop make evaluation order visible?
The scalar loop runs sequentially through the indexes of out. Ada is finished before Grace, Grace before Linus, Linus before Barbara. As shown in lines that access the index i of out. 
```
value <- out[[i]]
out[[i]] <- value
```

## Give one concrete input where careless recycling would change the answer.
An example would be when we have 4 students and they can achieve either of two grades, fail or pass
```
students <- c("A","B","C","D")
grades <- c("fail","pass")
```
If we just simply assign grades to students in a data frame matter
```
grade_list <- data.frame(student = students, grade = grades)
```
The grades will repeat from fail to pass and back:
```
Student A | Fail
Student B | Pass
Student C | Fail <- should have passed!
Student D | Pass

Vector students has length 4, but Vector grades has length 2, recycling Vector grades is the result.
```
So it could be that student C had the requirements to pass but actually failed because of recycling.

## Which implementation would you keep in an R program, and what tradeoff does that choice make?
Personally, I(Aparicio) would use the scalar implementation as it is easier to read and debug as it is similar to most programming language's implementation of a for loop. The tradeoff would be speed and increased code length.