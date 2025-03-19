import hashlib
import threading
import tkinter as tk
from tkinter import filedialog, messagebox

# Function to load wordlist
def load_wordlist():
    file_path = filedialog.askopenfilename(title="Select Wordlist", filetypes=[("Text files", "*.txt")])
    return file_path

# Function to hash and compare words from wordlist
def crack_password(hash_to_crack, wordlist, status_label):
    try:
        with open(wordlist, "r", encoding="latin-1") as file:
            for index, word in enumerate(file):
                word = word.strip()
                hashed_word = hashlib.sha256(word.encode()).hexdigest()

                # Update status every 1000 attempts to keep GUI responsive
                if index % 1000 == 0:
                    status_label.config(text=f"Trying: {word}")
                    root.update_idletasks()

                if hashed_word == hash_to_crack:
                    messagebox.showinfo("Success", f"Password Found: {word}")
                    status_label.config(text="Password Cracked!")
                    return
        messagebox.showerror("Failed", "Password Not Found in Wordlist")
        status_label.config(text="Password Not Found")
    except FileNotFoundError:
        messagebox.showerror("Error", "Wordlist file not found")
    except Exception as e:
        messagebox.showerror("Error", f"An error occurred: {str(e)}")

# Function to start cracking in a new thread
def start_cracking():
    hash_input = hash_entry.get().strip()
    wordlist_path = load_wordlist()

    if not hash_input or not wordlist_path:
        messagebox.showerror("Error", "Please enter a hash and select a wordlist")
        return

    # Update UI before starting thread
    status_label.config(text="Cracking in progress...")
    
    # Start password cracking in a new thread
    thread = threading.Thread(target=crack_password, args=(hash_input, wordlist_path, status_label))
    thread.start()

# GUI Setup
root = tk.Tk()
root.title("SHA-256 Password Cracker")

# Input field for SHA-256 hash
tk.Label(root, text="Enter SHA-256 Hash:").pack()
hash_entry = tk.Entry(root, width=50)
hash_entry.pack()

# Button to start cracking process
crack_button = tk.Button(root, text="Start Cracking", command=start_cracking)
crack_button.pack()

# Status label to show progress
status_label = tk.Label(root, text="Waiting for input...")
status_label.pack()

# Run GUI
root.mainloop()
