#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <sys/wait.h>

int main() {
    int x = 10;
    pid_t pid = fork();

    if (pid < 0) 
    {
        perror("fork failed");
        exit(EXIT_FAILURE);
    } 
    else if (pid == 0) 
    {
        // Child process
        x += 5;
        printf("Child Process: x = %d\n", x);
        _exit(0);
    } 
    else 
    {
        // Parent process
        wait(NULL); // Wait for child to finish
        printf("Parent Process: x = %d\n", x);
    }

    return 0;
}
