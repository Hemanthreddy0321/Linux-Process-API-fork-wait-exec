
Ex02-Linux Process API-fork(), wait(), exec()
# Ex02-OS-Linux-Process API - fork(), wait(), exec()
Operating systems Lab exercise


# AIM:
To write C Program that uses Linux Process API - fork(), wait(), exec()

# DESIGN STEPS:

### Step 1:

Navigate to any Linux environment installed on the system or installed inside a virtual environment like virtual box/vmware or online linux JSLinux (https://bellard.org/jslinux/vm.html?url=alpine-x86.cfg&mem=192) or docker.

### Step 2:

Write the C Program using Linux Process API - fork(), wait(), exec()

### Step 3:

Test the C Program for the desired output. 

# PROGRAM:

## C Program to print process ID and parent Process ID using Linux API system calls
```c
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main(void)
{	//variable to store calling function's process id
	pid_t process_id;
	//variable to store parent function's process id
	pid_t p_process_id;
	//getpid() - will return process id of calling function
	process_id = getpid();
	//getppid() - will return process id of parent function
	p_process_id = getppid();
	//printing the process ids

//printing the process ids
	printf("The process id: %d\n",process_id);
	printf("The process id of parent function: %d\n",p_process_id);
	return 0; }
```

## OUTPUT
![Screenshot 2024-04-03 213956](https://github.com/Hemanthreddy0321/Linux-Process-API-fork-wait-exec/assets/150005937/70d7cb52-ed4b-43a5-8c3a-879130caeb0f)



## C Program to create new process using Linux API system calls fork() and exit()
```c
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
#include<stdlib.h>
int main()
{ int pid; 
pid=fork(); 
if(pid == 0) 
{ printf("Iam child my pid is %d\n",getpid()); 
printf("My parent pid is:%d\n",getppid()); 
exit(0); } 
else{ 
printf("I am parent, my pid is %d\n",getpid()); 
sleep(100); 
exit(0);} 
}
```

## OUTPUT
![Screenshot 2024-04-03 214023](https://github.com/Hemanthreddy0321/Linux-Process-API-fork-wait-exec/assets/150005937/4480a9a6-6fbd-43dd-91f3-6ad01df7c6a1)



## C Program to execute Linux system commands using Linux API system calls exec() family
```c
#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <sys/wait.h>
#include <sys/types.h>
int main()
{       int status;
        printf("Running ps with execlp\n");
        execl("ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
printf("Running ps with execlp. Now with path specified\n");
        execl("/bin/ps", "ps", "ax", NULL);
        wait(&status);
        if (WIFEXITED(status))
                printf("child exited with status of %d\n", WEXITSTATUS(status));
        else
                puts("child did not exit successfully\n");
        printf("Done.\n");
        exit(0);}
```

## OUTPUT
![Screenshot 2024-04-03 214114](https://github.com/Hemanthreddy0321/Linux-Process-API-fork-wait-exec/assets/150005937/bf6bc604-bcec-4773-9f24-0b8b2d0873ad)
![Screenshot 2024-04-03 214208](https://github.com/Hemanthreddy0321/Linux-Process-API-fork-wait-exec/assets/150005937/8bd0ea86-e290-4611-9fbd-d30bdb7318a2)
![Screenshot 2024-04-03 214230](https://github.com/Hemanthreddy0321/Linux-Process-API-fork-wait-exec/assets/150005937/8cc38430-39bf-44f3-8d9e-11cf0372b87b)



# RESULT:
The programs are executed successfully.
