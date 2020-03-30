Fork of the respository bassoy/ttv that hosts tensor algorithms which were recently adapted in the Boost::UBlas library.

The core of the tensor algorithms are matrix times vector routines. 

This fork studies the implemented matrix times vector routines and aims to enhance the performance by parallelization of independent operations.

As a matrix times vector operation can be calculated with a set of independent inner products, 
the openMP library is used to calculate the inner products in parallel threads. 

The matrices in this study are stored in the row-major and the column-major format.

The performance is measured in FLOPS per second (FLOP: floating point operation).

As references, the performance of the sequential routine and the corresponding openBLAS routines are used.

The figures show that the prallel and openBLAS routines outperform the sequential routines,
and for matrices of dimensions from 2^2 x 2^2 to 2^11 x 2^11 the openBLAS routines perform better than the proposed parallel routines.
However, starting from matrices of dimension 2^12 x 2^12 the proposed parallel procedures catch up to the openBLAS routines and even gain an upper hand in case of the major-row format matrices.  

![mtv_col_blas](https://github.com/hrhee/ttv/blob/master/misc/mtv_col_blas.png)

![mtv_row_blas](https://github.com/hrhee/ttv/blob/master/misc/mtv_row_blas.png)
