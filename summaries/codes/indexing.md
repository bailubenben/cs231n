**x[obj]**

|Indexing Method   |obj's component                       |relationship with original array|rules|
|------------------|--------------------------------------|--------------|-----|
|*Basic slicing*     |slice object, an integer, or a tuple of slice objects and integers, interspersing with Ellipsis and newaxis| **views** of the original array|<br>1.An integer, i, returns the same values as i:i+1 except the dimensionality of the returned object is reduced by 1</br>
|*Advanced Indexing*|a non-tuple sequence object, an ndarray (of data type integer or bool), or a tuple with at least one sequence object or ndarray (of data type integer or bool)|**copy** of the data|
