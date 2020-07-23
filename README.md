# Efficiency and Value of Refactoring Code 

## Overview
The goals of this project were to answer two key components.  One, does the refactoring improve computer processing time; and two, whether refactoring existing script make coding faster and/or more efficient.  

## Results
The original script was written with a nested loop.  In this case, for each of the 12 ticker symbols, 3,012 rows were evaluated multiple times to test conditions.  That equate to 36,144 passes through the dataset (12 x 3012).

    Outer loop:	For i = 0 to 11 identify a ticker symbol to check

      Inner loop:	For j = rowStart to rowEnd	evaluate each row to: 

                    1-sum the ticker’s total volume
                    2-identify ticker’s starting price
                    3-identify ticker’s ending price
                    4-calculated ticker’s annual return

      Close inner loop

    Close outer loop
 			
After each evaluation, data would be assigned to a variable and entered onto a worksheet.  The nested loop script took .5664063 seconds run the analysis for 2017 and .53125 seconds for 2018. (link to png files)

In comparison, the refactored code reviews each row of data only once, taking 3,012 passes through the dataset.   The use of arrays allows this methodology.  An array is essentially a single variable that can hold multiple elements.  You could think of the array like a grocery list – it’s one piece of paper but contains many items.  Where a variable would only store one (1) value, an array can store many values while utilizing the storage capacity of one (1) variable.  Reducing storage used makes the process faster.  

In refactoring the nested loop code, an index, as well as the arrays to store the data, is declared.

    Declare index for array:
                    Dim tickerIndex As Integer 
                    tickerIndex = 0 
                      determines which ticker symbol is being checked (declared previously in the script)

    Declare arrays: Dim tickerVolumes(12) As Long
                    Dim tickerStartingPrices(12) As Single
                    Dim tickerEndingPrices(12) As Single

    Loop:	For i = 2 To RowCount	evaluate all rows to

            1-sum the ticker’s total volume
            2-identify ticker’s starting price
            3-identify ticker’s ending price
            4-calculated ticker’s annual return
          
    Close loop

The evaluated data are then placed onto a summary worksheet.  

The processing time using arrays was shortened to .0859375 seconds for 2017 (link) and .078125 seconds for 2018 (link).

## Conclusion

As seen in the comparison, the use of arrays would be clearly preferred.  There is almost a half second speed increase for both 2017 and 2018.  For small datasets, such as our challenge, a nested loop design can  work well without a significant time-performance issue.  However, once the code starts running on much larger datasets (because more storage is required), the effects of processing time will become noticeably longer and inefficient.  

The concept of refactoring code is advantageous.  The user takes the existing script and rearranges the logic to suit a particular purpose.  In stead of re-creating work, one can easily edit it creating a revised script that is more effective and in less time.

One drawback of refactoring is the challenge of altering some of the logic imbedded in the original code.  Not all the pieces of the code you want to use can fit in the same sequence in the revised version.   There will be a need to make additional logic adjustments in sequence and reasoning will need to be made.  It is not as simple as reordering lines of code.  

Nonetheless, even with potential difficulties faced with refactoring, it is still an effective and efficient way to write code for common procedures.
  
