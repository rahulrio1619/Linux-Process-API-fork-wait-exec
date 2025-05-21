# Linux-Process-API-fork-wait-exec-
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
```
Devolped by: RAHUL S 
Reg.No: 212224040259
```
## C Program to print process ID and parent Process ID using Linux API system calls

```
#include <stdio.h>
#include <sys/types.h>
#include <unistd.h>
int main(void)
{	
	pid_t process_id;
	pid_t p_process_id;
	process_id = getpid();
	p_process_id = getppid();
	printf("The process id: %d\n",process_id);
	printf("The process id of parent function: %d\n",p_process_id);
	return 0; }
```
## OUTPUT
![319525592-7ac28183-34f8-415f-9459-e427328e20eb](https://github.com/user-attachments/assets/912fa3ce-b640-415d-9224-fd8c3354c6ba)

## C Program to create new process using Linux API system calls fork() and exit()

```
#include <stdlib.h>
#include <sys/wait.h>
#include<stdio.h>
#include<unistd.h>
#include <sys/types.h>
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
![319525667-fe4ec4bc-8530-4242-b067-6ec1a767730e](https://github.com/user-attachments/assets/d0dab681-caf7-4ce9-9e03-0151862a58c7)

## C Program to execute Linux system commands using Linux API system calls exec() family
```
#include <stdlib.h>
#include <sys/wait.h>
#include<stdio.h>
#include<unistd.h>
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
![319525731-010f6c26-bc44-4beb-aa38-d5c3bba62426](https://github.com/user-attachments/assets/540b2672-5202-4f37-8f47-caf75556484d)
# RESULT:
The programs are executed successfully.
