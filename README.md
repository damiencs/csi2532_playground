# csi2532_playground
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
