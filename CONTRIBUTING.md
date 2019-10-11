# Contributing 
## Definitions
Contributions can be defined in the following forms:
    
-  **Module Development**
        
    -    Modules refer to collections of drivers, libraries, and other software that perform a function for the OS. While the goal of this project is to write as much of an OS in C or C++ as possible, some optimizations will improve performance vastly and these modules are welcome as separate components from the main project.
        
    - If you wish to write a module for a specific architecture, please wait for an API(usually in the base module for that same component) to be developed for interfacing with the driver. APIs will strive to abstract away the implementation-specific parts of OS development, allowing for a vast array of freedom in machine-specific implementations
    
   ***ALL ASSEMBLY MARCOS MUST HAVE COMMENTS DESCRIBING WHAT THEY DO*** 

    - This project is intended to help new developers get started with OS and low-level programming. As such, it is highly likely many newcomers will be unaccustomed to assembly language.
    
  - **Modules Documentation Requirements**
        
       -   All modules should have a readme file describing what the module does and what part of the OS it is intended to replace.
       - All modules should be very well documented and should clear describe what each function and member variable does. Long functions should be broken
  
- **Bug fixes**
    - A bug fix submission usually requires less scrutiny and documentation than a regular upload, however the amount of lenience is determined by the importance of the fix with regard to the stage the project is at( a physical memory address vunerability will have lower priority and higher standards than if implementing virtual memory solves the problem, and no memory manager has been implemented yet).
- **Vunerabilities**
     - Vunerabilities will be raised in issues. Sample issues coming soon. Response to vunerabilities is ranked on the progress of the OS and the severity of the threat it poses to the system.
