import os
import datetime
import tkinter as tk
from tkinter import filedialog

def scan_folder(folder_path):
    files = os.listdir(folder_path)
    
    for file in files:
        file_path = os.path.join(folder_path, file)
        if os.path.isfile(file_path):
            date = datetime.datetime.fromtimestamp(os.path.getmtime(file_path)).strftime("%d-%m-%Y")
            file_type = os.path.splitext(file)[1][1:].lower()

            # Check if the date directory exists, and create it if it doesn't
            date_dir = os.path.join(folder_path, date)
            os.makedirs(date_dir, exist_ok=True)

            # Check if the file type directory exists, and create it if it doesn't
            file_type_dir = os.path.join(date_dir, file_type)
            os.makedirs(file_type_dir, exist_ok=True)

            if file_type in {"jpg", "jpeg", "png", "mp4", "avi", "mov"}:
                os.rename(file_path, os.path.join(file_type_dir, file))
            else:
                os.rename(file_path, os.path.join(file_type_dir, file))

def browse_folder():
    folder_path = filedialog.askdirectory()
    folder_path_entry.delete(0, tk.END)
    folder_path_entry.insert(0, folder_path)

def process_folder():
    folder_path = folder_path_entry.get()
    scan_folder(folder_path)

# Create the main window
root = tk.Tk()
root.title("File Organizer")

# Create and place widgets
folder_path_label = tk.Label(root, text="Enter the folder path:")
folder_path_label.pack(pady=10)

folder_path_entry = tk.Entry(root, width=50)
folder_path_entry.pack(pady=10)

browse_button = tk.Button(root, text="Browse", command=browse_folder)
browse_button.pack(pady=10)

process_button = tk.Button(root, text="Process Folder", command=process_folder)
process_button.pack(pady=20)

# Start the main loop
root.mainloop()
