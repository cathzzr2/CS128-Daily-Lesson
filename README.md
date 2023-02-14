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



  
