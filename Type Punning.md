# Type Punning : 
This is an old technique to do  aliasing  in a safe way. 

Keep the src and dest type a single union and store src type in the union object and receive the target type from the dest object type from the pointer. 

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

struct emp {
	int empId;
	char name[7];
};

struct student {
	int studentId;
	char name[4];
};


union compartment 
{
	struct emp e; 
	struct student s; 
};

int main()
{
	struct emp e; 
	e.empId = 10; 
	strcpy( e.name, "Arijit");


	struct student s = *((struct student*) (&e));
	printf("%d:%s\n", s.studentId, s.name);


	union compartment c ; 
	c.e = e; 

	struct student s1 = c.s;
	printf("%d:%s\n", s1.studentId, s1.name);
	return 0;
}

```


