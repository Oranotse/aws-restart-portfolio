# Python Scripting: Finding Prime Numbers 🐍

The detailed steps for this lab can be seen clearly in the folder titled **Lab Steps Screenshots**.

## What This Lab Is About

In this lab, I worked on writing a Python script to find and display all prime numbers between 1 and 250, then save those results to a file. According to AWS, both Python 2 and Python 3 are installed on the **Linux Host EC2 instance**, but it is recommended to use Python 3. The challenge was to create a script that could identify prime numbers efficiently and store the output in a `results.txt` file for future reference.

## Connecting to the Linux Host

I connected to the **EC2 instance** using SSH through **PuTTY**. After downloading the `labsuser.ppk` file from the lab details, I entered the instance's public IP address into PuTTY, loaded the private key, and connected as `ec2-user`. Once connected, I had command-line access to start working on the Python script.

## Writing the Python Script

I created `primenumbers.py` using **nano**. The script uses a loop to check each number from 1 to 250, skipping numbers below 2 since they are not prime. For each number, it assumes the number is prime (`is_prime = True`), then tests divisibility by all numbers from 2 up to itself using the modulo operator (`num % i == 0`). If divisible, it marks the number as not prime and breaks the loop. Prime numbers that pass this test get added to the `primes` list using `primes.append(num)`. The script then prints all the prime numbers to the terminal.

## Saving Results to a File

I used `open("results.txt", "w")` to create the output file, wrote the header `"Prime numbers between 1 and 250:\n"`, then looped through the `primes` list writing each number as a string with `file.write(str(p) + "\n")`. After closing the file with `file.close()`, the script printed a confirmation message that the results were saved.

## Testing the Script

I ran the script with `python3 primenumbers.py` and it successfully displayed all prime numbers in the terminal. I verified the output file by running `cat results.txt`, which showed all the prime numbers listed one per line, confirming the script worked correctly.

## What I Learned

This lab taught me how to write a Python script that solves a mathematical problem and saves output to a file instead of just printing to the terminal. I got practical experience connecting to an **EC2 instance** using SSH and **PuTTY**, which is essential when working with cloud servers. The prime number logic using loops and the modulo operator helped me understand how to break down problems systematically. Working directly on an EC2 instance through the command line also gave me hands-on experience with **nano**, which is important for creating and editing files on remote AWS servers. 🎉
