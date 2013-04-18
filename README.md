Research into calibration of financial models
=============================================


Things to read/learn about before the starting on the project
-------------------------------------------------------------

* The R programming language and environment. Start with:
  http://cran.r-project.org/doc/manuals/R-intro.html

* Papers on calibration of the Heston model to market prices. Search
  with Google with "Heston Model Calibration" will lead to some good
  papers
  
* A little bit about QuantLib

Approach to work
----------------

* Define an appropriate interface to QuantLib pricing routines:

  * Assume for time being derivatives wrt parameters are not available
  * Will need to define overall derivative contract specification
    which does not change
  * Then the quantities which allow multiple observations of the
    market. Traditionally these will be the maturities and strikes of
    the options 
  * Multiple maturities/strikes should be supplied into a single
    function call for efficiency
  * The output should be price for each maturity/strike combination
  
  It is up to us to define the level at the interface works, with
  options being:
  
  * Via input/output text files 
  * Loading QuantLib as a shared library into R, the using it either
    via a C-interface, Rcpp (RQuantLib) or SWIG
  * Interprocess call (SOAP, or something similar)
  
* Implement optimisation of the model parameters wrt the market
  observations of prices using standard R least-squares algorithm

    * First, compare the results to the algorithm as implemented in
      QuantLib!





