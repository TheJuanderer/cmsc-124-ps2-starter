# Vector and Scalar Evaluation

`clean_scores_vector()`
The function copies the input with scores[], so the original and its names stay untouched. The logical index in return_vec[is.na(return_vec)] <- 0 overwrites every NA in one subassignment, with no loop. Next, pmin(2 * return_vec, 20) doubles every element and caps each at 20 in one expression.

`clean_scores_scalar()`
This function builds a vector out with setNames(as.double(scores), names(scores)), which forces double type while keeping the names. A loop then handles one element per pass: it reads value <- out[[i]], replaces an NA with 0, applies pmin(2 * value, 20), and writes back with out[[i]] <- value.

## Which operations in the vector version act on all elements at once?
The operation ```return_vec[is.na(return_vec)] <- 0``` runs through the elements
instantly and replaces any NA value. 
The operation ```return_vec <- pmin(2 * return_vec, 20)```, runs the same but instead multiplying any non-NA value by 2, lowering it to 20 if greater than it. 

## Where does the scalar loop make evaluation order visible?
The scalar loop runs sequentially through the indexes of out. Ada is finished before Grace, Grace before Linus, Linus before Barbara.
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

Students has length 4 but grades has length 2, so grades is recycled.
```

## Which implementation would you keep in an R program, and what tradeoff does that choice make?
Personally, I(Aparicio) would use the scalar implementation as it is easier to read and debug as it is similar to most programming language's implementation of a for loop. The tradeoff would be speed and increased code length.

Personally, I (Mendoza) would use the vector implementation. It is easy to understand without being complex: the code reads like the rule itself (replace NA with 0, double each score, cap at 20). It is also shorter, with fewer lines, since no loop or loop index is needed. The tradeoff is that the vector version creates a few full-length temporary vectors, so it uses a little more memory than the scalar loop, which handles one value at a time.