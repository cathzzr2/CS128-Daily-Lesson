# CS128-Daily-Lesson

## 5.1 Exceptions

- Remember to **include stdexcept**, otherwise there will be a run-time error detected by library
- **throw** an exception when an unexpected error happens, for example,
  > if (area < 0) { throw std::runtime_error("invalid area"); }
- to indicate that we are willing to **catch** these exceptions, we can use try-catch block, and catch block is usually followed by an excemtion handler 
  > try {double area = area_calc(-10, 10); }
  > catch (const runtime_error& e) { // handle exception }
- The type of exception we **throw** must match the one we acknowledge to **handle**
- Fundamental question: Do I have sufficient info to decide how to respond to the error? 

- If no, re-throw the exception 
  > catch (const runtime_error& e) { throw; }
- If yes, handle it
  > catch (const runtime_error& e) { area = 0; }
  
- Exceptions are designed to handle non-local errors. Never use it to handle local errors. 


## 5.2 Exceptions Part 2

- Different kinds of execeptions defined in stdexcept
  > std::runtime_error(std::string) (range_error, overflow_error, underflow_error)
  
  > std::logic_error(std::string) (length_error, domain_error, out_of_range, invalid_argument)
  - e.g., throw **std::invalid_argument** error should match catch **std::logic_error** or **std::invalid_argument**
  
- Preconditions and Postconditions

  - **Precondition**: must be true prior to the execution 
  - if violated, the effect of the code will be undefined
  
  - **Postcondition**: must be true after the execution 
  - a valid precondition usually leads to a valid postcondition


## 5.3 Testing and Debugging

- Differences

  - Teststng: detecting errors
  - Debugging: diagonosing and correcting the root causes of detected errors 
  
- What to do 

  - Write sel-documentting code
  - Comment to explain non-intuitive code
  - Use meaningful names
  - Break code into small functions
  - Avoid complicated code sequences
  - Use library facilities
  
- What no to do (when the program doesn't work)

  - randomly look at the program
  - change it to just "look" better 

- Careful considerations (beginnings & ends)

  - initialize every variable
  - every value is reasonable & sensible
  - the functions gets the right arguments
  - the function returns the right value
  - handle the first element correctly
  - handle the last element correctly
  - handle the empty case correctly
  - open the files correctly
  - the program reads the input 
  - the program prints the output 

- **Informal testing & debugging**

  - add debug output statements to see what is printed out
  - fix the plce with bad output

- Asserts

  > include cassert
  - when the result is false, the program will print an error with filename and line number 
  
  - Code Example #1: Ensure reasonable output
  > constexp int kLargestReasonable = 1000;
  > int num_of_elements = -1;
  > assert (kLargstReasonable >= number_of_elements);
  > assert (num_of_elements > 0);
  - Standard Output Example
  "a.out: driver.cc:12: int main(): Assertion 'num_of_elements > 0' failed"
  
  - Code Example #2: Ensure post-conditions are met
  > ...
  > assert (result >= 0.0);
  > return result;
  
- Asserts vs. Exceptions\

  - assetions can help detect the errors, except
  - trying to open an file that DNE
  - incorrect/invalid arguments passed to our functions
  
- **Formal tests**

  - Unit tests
    
    - written by programmers, for programmers
    - test the system at the lowest level
    - isolate from the more complete systems
  
  - Component tests
  
    - 
