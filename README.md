## Ex-24 Create an empolyee onboarding application using,SpringBoot and SQL
## Aim:
To create an employee onboarding application using SpringBoot and SQL.

## Algorithm:
### Step 1:- 
Open Spring Initialzr.

### Step 2:-
Save the zip file.

### Step 3:-
Open an IDE like IntelliJ,Oracle etc.

### Step 4:-
Open the folder in the IDE.

### Step 5:-
Create Components.

### Step 6:-
Connect the database with the SpringBoot.

## Program:
Employee.java
```java
package com.Employee.employee.emp;

import jakarta.persistence.*;
import org.junit.platform.commons.annotation.Testable;
import org.springframework.boot.autoconfigure.domain.EntityScan;

import java.time.LocalDate;
import java.time.Period;

@Entity
@Table
public class Employee {
    @Id
    @SequenceGenerator(
            name = "employee_sequence",
            sequenceName = "employee_sequence",
            allocationSize = 1
    )
    @GeneratedValue(
            strategy = GenerationType.SEQUENCE,
            generator = "employee_sequence"
    )
    private Long empId;
    private String empName;
    @Transient
    private Integer empAge;
    private LocalDate empDob;
    private String empEmail;

    public Employee() {
    }

    public Employee(Long empId, String empName, LocalDate empDob, String empEmail) {
        this.empId = empId;
        this.empName = empName;
        this.empDob = empDob;
        this.empEmail = empEmail;
    }

    public Long getempId() {
        return empId;
    }

    public void setempId(Long empId) {
        empId = empId;
    }

    public String getempName() {
        return empName;
    }

    public void setempName(String empName) {
        empName = empName;
    }

    public Integer getempAge() {
        return Period.between(empDob,LocalDate.now()).getYears();
    }

    public void setempAge(Integer empAge) {
        empAge = empAge;
    }

    public LocalDate getempDob() {
        return empDob;
    }

    public void setempDob(LocalDate empDob) {
        empDob = empDob;
    }

    public String getempEmail() {
        return empEmail;
    }

    public void setempEmail(String empEmail) {
        empEmail = empEmail;
    }

    @Override
    public String toString() {
        return "Employee{" +
                "empId=" + empId +
                ", empName='" + empName + '\'' +
                ", empAge=" + empAge +
                ", empDob=" + empDob +
                ", empEmail='" + empEmail + '\'' +
                '}';
    }
}
```
applications.properties
```java
spring.datasource.url=jdbc:postgresql://localhost:5432/hosman_db
spring.datasource.username=postgres
spring.datasource.password=sk@123
spring.jpa.hibernate.ddl-auto=create-drop
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect
spring.jpa.properties.hibernate.format_sql=true
```
App.js
```java
import React from "react"
import './App.css';
import { BrowserRouter as Router, Route, Routes, Link } from "react-router-dom";
import EmployeeRegistrationComponent from './components/EmployeeRegistrationComponent/EmployeeRegistrationComponent';
import HeaderComponent from "./components/HeaderComponent/HeaderComponent";
import EmployeeDirectoryComponent from "./components/EmployeeDirectoryComponent/EmployeeDirectoryComponent";
import EmployeeDeletionComponent from "./components/EmployeeDeletionComponent/EmployeeDeletionComponent";

function App() {
  return (
    <Router>
            <div className="container">
              <HeaderComponent/>
              
            <nav className="nav-menu">
                <Link to="/" >Home</Link>
                <Link to="/admin/add" >Add Employee</Link>
                <Link to="/admin/delete" >Delete Employee</Link>
            </nav>
           <Routes>
                 <Route exact path='/' element={<EmployeeDirectoryComponent/>}></Route>
                 <Route path='/admin/add' element={<EmployeeRegistrationComponent/>}></Route>
                 <Route path='/admin/delete' element={<EmployeeDeletionComponent/>}></Route>
          </Routes>
          </div>
       </Router>
  );
}

export default App;
```
## Output:
![emp](https://github.com/SarankumarJ/Employee-Onboarding-Application/assets/94778101/5d2523bc-a320-4455-9c10-127a4c81efa3)



## Result:
Thus we have successfully created an employee onboarding application using SpringBoot and SQL.
