# csi2532_playground
Lab 04
1. Les professeurs peuvent enseigner le même cours sur plusieurs semestres et seule la plus récente doit être enregistrée.
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

3. Chaque professeur enseigne exactement un cours (ni plus, ni moins).
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
5. Les professeurs peuvent enseigner le même cours sur plusieurs semestres et chaque doit être enregistrée.
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
    primary key (ssn, courseid, semesterid),
    foreign key (ssn) references professors,
    foreign key (courseid) references courses
);
```
6. Supposons maintenant que certains cours puissent etre enseignes conjointement par une equipe de professeurs, mais il est possible qu'aucun professeur dans une equipe ne puisse enseigner le cours. Modelisez cette situation en introduisant des ensembles d'entites et des ensembles de relations supplementaires si necessaire.
```sql
CREATE TABLE professors(
    ssn integer, 
    primary key (ssn)
);

CREATE TABLE courses(
    courseid varchar(100), 
    primary key (courseid)
);

CREATE TABLE groups(
    groupid varchar(100),
    primary key (groupid)
);

CREATE TABLE member_of(
    ssn integer, 
    groupid varchar(100),
    primary key (ssn, groupid),
    foreign key (ssn) references professors,
    foreign key (groupid) references groups
);


CREATE TABLE teaches(
    groupid varchar(100),
    courseid varchar(100),
    semesterid varchar(100), 
    primary key (groupid, courseid, semesterid),
    foreign key (groupid) references groups,
    foreign key (courseid) references courses
);
```






