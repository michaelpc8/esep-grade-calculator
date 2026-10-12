# ESEP Grade Calculator

A Go library to calculate a student's final letter grade from three kinds of graded work: assignments, essays and exams.

## How final grade calculation works

1. Grades are added one at a time with a name, numeric score and a type.
2. The average of each grade type is calculated.
3. The final numeric grade is the sum of each average multiplied by its weight:

| Grade type  | Weight |
|-------------|--------|
| Assignments | 50%    |
| Exams       | 35%    |
| Essays      | 15%    |

4. The numeric grade is converted to a letter grade:

| Letter | Numeric grade |
|--------|---------------|
| A      | 90 and above  |
| B      | 80 and above  |
| C      | 70 and above  |
| D      | 60 and above  |
| F      | below 60      |

## Project Layout

```
esep-grade-calculator/
├── README.MD
└── grade-calculator/
    ├── go.mod                     # Go module definition (module name and Go version)
    ├── grade_calculator.go        # Library code: GradeCalculator, Grade, GradeType
    └── grade_calculator_test.go   # Unit tests using Go's built-in testing package
```

## Requirements 

- Golang 1.24+ : https://go.dev/dl/
- Check your version using `go version`
- No other dependencies. Only the Go standard library is used.

## Usage
```go
calc := NewGradeCalculator()

calc.AddGrade("open source assignment", 95, Assignment)
calc.AddGrade("exam 1", 88, Exam)
calc.AddGrade("essay on ai ethics", 91, Essay)

letter := calc.GetFinalGrade()
```

Run unit tests:
```
cd grade-calculator/
go test ./...
```

Run unit tests with code coverage:
```
cd grade-calculator/
go test -coverprofile=coverage.txt ./...
``` 