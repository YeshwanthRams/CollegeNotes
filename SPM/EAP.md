## Functional point analysis

FPA is technique used to measure software requirements bsaed on different functions , assigning points to each and summarizing them to estimate the total man-hours required for the project 

### Compnents of FPA 
FPA involves categorizing system interactions into five types : 

#### External Inputs (EI) 
- These are user inputs that are processed and stored within the system 
> add item shopping cart and ordering it
#### External Outputs (EO)
- These are data being sent out from the system to an external user of system
> sending order conformation email 
#### External Queries (EQ)
- This involves both input and output
> searching an item (input) and get search results back (output)
#### External Logic Files (EFL)
- The external data used by the system for reference or additional functionality
> Getting review of a product from third-party services
#### Internal Logic Files (IFL)
- A collection of interrelated data managed by the system
> The database storing all the items, user data , order history

![Alt text](FPAComponents.jpg)

### Benefits of Functional point analysis 

### FP Points Computation
- Calculate unadjusted functional points ( `UFP` )
    - know the weighing factors (Low, Average, High)
    - multiply component values with weights and finally add them all 
    - the result of that sum above is the UFP values
- Calculate comkplexity adjustment factor 
    - know the adjustment factor value
        - 0 : Not important
        - 1 : Incidental 
        - 2 : Moderate 
        - 3 : Average
        - 4 : Significant
        - 5 : Essential
    - multiply the adjustment factor value with len(general system characteristics) (usually 14)
    - $CAF = 0.65 + (0.01 \times \sum{F_i})$ => $F_i = 14 \times \text{adjustment factor value}$

Final Formula : $FP = UFP \times CAF$

### General System characteristics (GSC's)
following questions:
1. Does the system require reliable backup and recover.
2. Are data communications required?
3. Are there distributed processing functions?
4. Is performance critical?
5. Will the system run in an existing, heavily utilized operational environment?
6. Does the system require on-line data entry?
7. Does the on-line data entry require the input transaction to be built over multiple screens or operations?
8. Are the master files updated on-line?
9. Are the inputs, outputs, files, or inquiries complex?
10. Is the internal processing complex?
11. Is the code designed to be reusable?
12. Are conversion and installation included in the design?
13. Is the system designed for multiple installations in different organizations?
14. Is the application designed to facilitate change and ease of use by the user?
### Example

1. **Table of Weights for FPA Components**:

   | Component        | Low Complexity | Average Complexity | High Complexity |
   |------------------|----------------|--------------------|-----------------|
   | External Inputs  | 3              | 4                  | 6               |
   | External Outputs | 4              | 5                  | 7               |
   | External Inquiries| 3              | 4                  | 6               |
   | Internal Logic Files (ILF) | 7    | 10                 | 15              |
   | External Logic Files (ELF) | 5    | 7                  | 10              |

2. **Simplified Example for Calculation**:

   Let's assume we have the following counts for each component:
   - External Inputs: 2 of low complexity
   - External Outputs: 1 of average complexity
   - Inquiries: 2 of high complexity
   - Internal Logic Files: 1 of high complexity
   - External Logic Files: 1 of low complexity

   The calculation would be:
   - External Inputs: 2 × 3 = 6
   - External Outputs: 1 × 5 = 5
   - Inquiries: 2 × 6 = 12
   - Internal Logic Files: 1 × 15 = 15
   - External Logic Files: 1 × 5 = 5

   Total Unadjusted Function Points (UFP) = 6 + 5 + 12 + 15 + 5 = 43

Let's say that the 14 General System Characteristics (GSCs) each have an arbitrary value of 3 for simplicity. The sum of the GSCs would be 3 × 14 = 42.

Using the formula for the Complexity Adjustment Factor (CAF):
$ CAF = 0.65 + (0.01 \times \sum{E_i}) $
$ CAF = 0.65 + (0.01 \times 42) $
$ CAF = 0.65 + 0.42 $
$ CAF = 1.07 $

Now, calculate the final Function Points (FP) using the UFP from before:
$ FP = UFP \times CAF $
$ FP = 43 \times 1.07 $
$ FP = 46.01 $

So, the total Function Points, adjusted for complexity with this CAF, would be approximately 46.

## SLOC
**Source Lines Of Code** is a software metric used to measure the size of a software program by counting the number of lines in the program's source code.

SLOC is typically used to determine the amount of effort that will be required to develop a program, as well as programming productivity and effort once the software is produced

### Types of SLOC

#### Physical SLOC 
> Physical SLOC calculates total number of lines a source code including inline comments , blank lines etc... 
> - it is easier to measure but very sentitive to coding conventions and code formatting

#### Logical SLOC 
> Logical SLOC only calculates executable code expressions (such as operators, functions, etc...)
> - while Logical SLOC is less effective to code formatting, it is hard to measure.

### Advantages 

- **Scope of automation** : Count the lines of code can be automated 
- **Intuitive Metric** : Line of Code serves as an intuitive metric for measuring the size of software due to the fact that it can be seen and the effect of it can be visualized.

### Disadvantages
- **Lack of Accountability** : Not useful to measure the productivity of a project using only result from the coding phase, which usually accounts for only 30% to 35% of the overall effort.

- **Developer’s Experience** : An experienced developer may implement certain functionality in fewer lines of code than another developer of relatively less experience does, though they use the same language.

- **Difference in Languages** : Different programming languages take different number of LOC to implement same funtionality

- **Advent of GUI Tools** : with GUI-based programming languages like visual basic developers write less code

## Basic COCOMO
The Basic COCOMO model calculates software development effort as a function of program size. The model uses the Source Lines of Code (SLOC) as a measure of program size and applies a mathematical formula to estimate the effort required. Here’s how you can calculate it:

1. **Determine the Size in SLOC**: First, you need to quantify the size of your software project in terms of Source Lines of Code. This step involves counting the number of lines of code that will be written for the project.

2. **Apply the Basic COCOMO Model Formula**: The Basic COCOMO model estimates the effort (in person-months) using the following formula:

   $ \text{Effort} = a \times (\text{KLOC})^b $

   In this formula:
   - $( \text{Effort} )$ is the software development effort in person-months.
   - $( a )$ and $( b )$ are empirically derived constants. For the Basic COCOMO model, $( a )$ typically equals 2.4, and $( b )$ equals 1.05.
   - $( \text{KLOC} )$ (Kilo Lines of Code) is the estimated number of thousands of lines of code.

   For example, if your project is estimated to be 10,000 lines of code (or 10 KLOC), you would calculate the effort as:

   $ \text{Effort} = 2.4 \times (10)^{1.05} $

3. **Calculate the Duration and Staffing**:
   The Basic COCOMO model also provides ways to estimate the project duration and the number of people required. The duration can be calculated using the formula:

   $ \text{Duration} = c \times (\text{Effort})^d $

   Where $( c )$ and $(  d )$ are constants (typically, $(  c = 2.5 )$ and $( d = 0.38 )$ for the Basic model). The number of people required (staffing) is simply the effort divided by the duration.

It’s important to note that the Basic COCOMO model is quite simplistic and is best used for rough, early-stage estimates of software projects. It does not account for various factors like team capability, technology novelty, and other project-specific attributes, which are considered in more advanced versions of the COCOMO model.

## UseCase Based Estimation
To provide an example of use-case based estimation, let's consider a hypothetical online shopping system. Here are the steps we would take:

1. **Identify Actors**:
   - Customers
   - Admin

2. **Identify Use Cases**:
   - Customers: Browse Items, Add to Cart, Checkout
   - Admin: Add Item, Remove Item, Process Orders

3. **Classify Actors and Use Cases**:
   - Actors: Simple (Customers), Average (Admin)
   - Use Cases: Simple (Browse Items), Average (Add to Cart, Add Item, Remove Item), Complex (Checkout, Process Orders)

4. **Assign Weights**:
   - Actor Weights: Simple = 1, Average = 2, Complex = 3
   - Use Case Weights: Simple = 5, Average = 10, Complex = 15

5. **Calculate Unadjusted Use Case Points (UUCP)**:
   - Actors: (1 Simple * 1) + (1 Average * 2) = 3
   - Use Cases: (1 Simple * 5) + (4 Average * 10) + (2 Complex * 15) = 115

6. **Determine Technical Complexity Factors (TCF)**:
   - Assume a TCF value based on technical aspects such as performance, security, etc. (e.g., 1.2)

7. **Determine Environmental Complexity Factors (ECF)**:
   - Assume an ECF value based on environmental aspects such as team experience (e.g., 0.8)

8. **Calculate Adjusted Use Case Points (AUCP)**:
   - AUCP = UUCP * TCF * ECF = 115 * 1.2 * 0.8 = 110.4

The values for TCF and ECF would normally be determined using a more detailed analysis based on specific factors and their associated weights.