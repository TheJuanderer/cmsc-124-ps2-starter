# Vector and Scalar Evaluation

Replace this paragraph after your checks pass. Trace one input, including the
missing value, through `clean_scores_vector()` and `clean_scores_scalar()`.
Compare the two evaluation models, identify where recycling would change the
answer, and explain which implementation you would keep in an R program.

`clean_scores_vector()`
The function copies the input with scores[], so the original and its names stay untouched. The logical index in return_vec[is.na(return_vec)] <- 0 overwrites every NA in one subassignment so basically you dont need to loop throughout return_vec. Next, pmin(2 * return_vec, 20) doubles every element and caps each at 20 in one expression it works even if the values are 0 since 0 * 20 is 0.


`clean_scores_scalar()`
This function builds a vector out with setNames(as.double(scores), names(scores)), which forces double type while keeping the names. Then a loop then handles one element per pass. It reads the value <- out[[i]], then it checks if the value is NA; if it is, replace an NA with 0. After that it applies pmin(2 * value, 20) to the value and finally, writes back with out[[i]] <- value. 
