# csi2532_playground
Lab 04

<img width="498" alt="Capture" src="https://user-images.githubusercontent.com/75296154/153736504-f0981c93-2994-4168-892b-f2fb38a535b1.PNG">


```sql
CREATE TABLE professors(
 ssn integer, 
primary key (ssn)
);

CREATE TABLE courses(
 courseid varchar(100), 
primary key (courseid)
);

CREATE TABLE teaches(
 ssn integer,
 courseid varchar(100),
 semesterid varchar(100), 
primary key (ssn, courseid),
 foreign key (ssn) references professors,
 foreign key (courseid) references courses
);
```
