# MPI_Ring_Blocking_NonBlocking
Write an MPI program and run it with n processes to form a ring-like message passing pattern among them.

That is, Process 0 sends a message to Process 1, Process 1 sends a message to Process 2, �., Process n-1 sends a message back to Process 0. In your program at the beginning Process 0 reads a floating point data (�f�) from a file named �data.txt�. Then the process updates f with f = f * 0.95 and sends the new f value to the next process. Generally each process p in the ring takes these two steps repeatedly (1) receiving a float data �f� from any process (ANY_SOURCE); (2) checking whether the received data is positve and less than a predefined threshold (0.01). If yes, it broadcasts "-1" to all the other processes (think of whether MPI collective broadcast can be used here.) and then it exits. Otherwise, if the received data f is positive, it updates the f value with f = f * 0.95 and then sends the new value to the next process ((p+1) mod n), else the process exits. Process 0 prints out the value of any data right after the data is received during the program execution. You need to make sure that all processes can exit without being deadlocked.
