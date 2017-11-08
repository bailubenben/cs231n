**x[obj]**

|Indexing Method   |obj's component                       |relationship with original array|rules|
|------------------|--------------------------------------|--------------|-----|
|*Basic slicing*     |slice object, an integer, or a tuple of slice objects and integers, interspersing with Ellipsis and newaxis.<br></br><br> In order to remain backward compatible with a common usage in Numeric, basic slicing is also initiated if the selection object is any non-ndarray sequence (such as a list) containing slice objects, the Ellipsis object, or the newaxis object, but not for integer arrays or other embedded sequences.</br>| **views** of the original array|<br>1.An integer, i, returns the same values as i:i+1 except the dimensionality of the returned object is reduced by 1</br><br>2.You may use slicing to set values in the array, but (unlike lists) you can never grow the array. The size of the value to be set in x[obj] = value must be (broadcastable) to the same shape as x[obj]</br>
|*Advanced Indexing*|a non-tuple sequence object, an ndarray (of data type integer or bool), or a tuple with at least one sequence object or ndarray (of data type integer or bool)|**copy** of the data|<br>1.rows[:, np.newaxis] + columns</br><br>2.np.ix_(rows, columns)</br>
|*Field Access*|If the ndarray object is a structured array the fields of the array can be accessed by indexing the array with strings, dictionary-like.|Indexing x['field-name'] returns a new view to the array|


NB:There are six sequence types: strings, Unicode strings, lists, tuples, buffers, and xrange objects.


