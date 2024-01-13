# Lab 1 Report
## the cd command
![image](https://github.com/theryanfo/cse15l-lab-reports/assets/156359755/562cf8b5-088c-44ca-87f0-b354df432274)

1. path to directory as argument: Working directory - /home; we choose the messages directory which is located within the home directory; it is not an error.
2. path to file as argument: Working directory - /home/lecture1; we recieve an error since Hello.java is a file, not a directory. We cannot use a file as an argument for the cd command.
3. no argument: Working directory - /home/lecture1; The cd command with no arguments returns our working directory to the home directory; it is not an error.

## the ls command
![image](https://github.com/theryanfo/cse15l-lab-reports/assets/156359755/6ae93d71-6c83-4757-bbd7-1e77b9696d52)

1. no argument: Working directory - /home/lecture1; the command lists the contents of the working directory, giving the names of the 3 files and the name of the directory inside the working directory; it is not an error.
2. path to directory as argument: Working directory - /home/lecture1; the command lists the contents of the messages directory, which includes the 4 files shown above; it is not an error.
3. path to file as argument: Working directory - /home/lecture1; since the Hello.java file exists, the command lists Hello.java; it is not an error.

## the cat command
![image](https://github.com/theryanfo/cse15l-lab-reports/assets/156359755/1e573646-4fe7-4315-8dce-ffbff31cce02)

1. path to directory as argument: Working directory - /home/lecture1; we recieve an error because the cat command cannot read a directory.
2. path to file as argument: Working directory - /home/lecture1; to read the jp-ja.txt file within messages, we use messages/jp-ja.txt as the argument; it is not an error.
3. no argument:  Working directory - /home/lecture1; if cat is run with no arguments, the program reads from standard input; technically not an error.
