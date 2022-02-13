# csi2532_playground
Lab 04
1. Les professeurs peuvent enseigner le même cours sur plusieurs semestres et seule la plus récente doit être enregistrée.
<img width="498" alt="Capture" src="https://user-images.githubusercontent.com/75296154/153736504-f0981c93-2994-4168-892b-f2fb38a535b1.PNG">


```sql
CREATE TABLE Professeur(
 SSN integer, 
primary key (SSN)
);

CREATE TABLE courses(
 courseid varchar(100), 
primary key (courseid)
);

CREATE TABLE teaches(
 SSN integer,
 courseid varchar(100),
 semestreID varchar(100), 
primary key (SSN, courseid),
 foreign key (SSN) references Professeur,
 foreign key (courseid) references Cours
);
```

3. Chaque professeur enseigne exactement un cours (ni plus, ni moins).
<img width="498" alt="Capture" src="https://user-images.githubusercontent.com/75296154/153736504-f0981c93-2994-4168-892b-f2fb38a535b1.PNG">

```sql
CREATE TABLE Professeur(
 SSN integer, 
primary key (SSN)
);

CREATE TABLE Cours(
 courseid varchar(100), 
primary key (courseid)
);

CREATE TABLE teaches(
 SSN integer,
 courseid varchar(100),
 semesterid varchar(100), 
primary key (SSN, courseid),
 foreign key (SSN) references Professeur,
 foreign key (courseid) references Cours
);
```
5. Les professeurs peuvent enseigner le même cours sur plusieurs semestres et chaque doit être enregistrée.
<img width="498" alt="Capture" src="https://user-images.githubusercontent.com/75296154/153736504-f0981c93-2994-4168-892b-f2fb38a535b1.PNG">

```sql
CREATE TABLE Professeur(
    SSN integer, 
    primary key (SSN)
);

CREATE TABLE Cours(
    courseid varchar(100), 
    primary key (courseid)
);

CREATE TABLE teaches(
    SSN integer,
    courseid varchar(100),
    semestreID varchar(100), 
    primary key (SSN, courseid, semestreID),
    foreign key (SSN) references Professeur,
    foreign key (courseid) references Cours
);
```
6. Supposons maintenant que certains cours puissent etre enseignes conjointement par une equipe de professeurs, mais il est possible qu'aucun professeur dans une equipe ne puisse enseigner le cours. Modelisez cette situation en introduisant des ensembles d'entites et des ensembles de relations supplementaires si necessaire.
<img width="520" alt="Capture1" src="https://user-images.githubusercontent.com/75296154/153737129-521ad3e8-3915-46db-ab73-368c38625fd8.PNG">

```sql
CREATE TABLE Professeur(
    SSN integer, 
    primary key (SSN)
);

CREATE TABLE Cours(
    courseid varchar(100), 
    primary key (courseid)
);

CREATE TABLE equipe(
    groupid varchar(100),
    primary key (id)
);

CREATE TABLE membre(
    SSN integer, 
    id varchar(100),
    primary key (SSN, id),
    foreign key (SSN) references Professeur,
    foreign key (id) references equipe
);


CREATE TABLE teaches(
    id varchar(100),
    courseid varchar(100),
    semestreID varchar(100), 
    primary key (id, courseid, semestreID),
    foreign key (id) references equipe,
    foreign key (courseid) references cours
);
```






