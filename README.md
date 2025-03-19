This project is a multi-threaded password cracker that attempts to brute-force SHA-256 hashed passwords using a wordlist. It supports large external wordlists, multi-threading for faster cracking, and a graphical user interface (GUI) for ease of use.

Features

Uses SHA-256 hashing algorithm

Multi-threading for improved speed

Supports large external wordlists

GUI interface for ease of use

Can handle a variety of password character types

Requirements

Before running the project, ensure you have the following installed:

Python 3.x

Required Python libraries:

pip install hashlib tkinter concurrent.futures


How It Works

The user enters a SHA-256 hash into the GUI.

The program reads through a wordlist and hashes each word.

If a match is found, the password is displayed.

Multi-threading speeds up the process for large wordlists.

Installation and Usage

1. Clone the Repository

git clone https://github.com/yourusername/password-cracker.git
cd password-cracker

2. Run the Program

python password_cracker.py

3. Provide Input

Enter the SHA-256 hash of the password you want to crack.

Select a wordlist file (e.g., rockyou.txt).

Click "Start" to begin cracking.

Example Usage

If your hash is:

5e884898da28047151d0e56f8dc6292773603d0d6aabbdd6118b756f00442f9

And 'password' is in your wordlist, the program will return:

Password found: password

Wordlists

You can download large wordlists such as:

RockYou.txt (20GB of passwords)

Have I Been Pwned Password List

SecLists (GitHub repository with multiple wordlists)
