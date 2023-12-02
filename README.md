# class-time-table
This Python Tkinter program creates a stylish class timetable GUI, enabling users to organize and input class schedules efficiently. It features bold titles, labels, and entry widgets, offering a visually appealing and functional interface for managing class schedules, with a focus on days and times.
import tkinter as tk
from tkinter import ttk

class ClassTimetable(tk.Tk):
    def __init__(self):
        super().__init__()

        self.title("Class Timetable")
        self.geometry("700x400")

        self.days = ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"]
        self.times = ["8:00 AM", "8:45 AM", "9:30 AM", "10:15 AM", "11:00 AM",
                      "11:45 AM", "12:30 PM", "1:00 PM"]

        self.create_styles()
        self.create_timetable()

    def create_styles(self):
        style = ttk.Style()
        
        # Style for the title label
        style.configure("Title.TLabel", font=("Helvetica", 18, "bold"), foreground="blue", borderwidth=2, relief="solid", background="#eee")

        # Style for other labels, entries, and header
        style.configure("Header.TLabel", font=("Helvetica", 12, "bold"), background="#333", foreground="white")
        style.configure("Day.TLabel", font=("Helvetica", 12))
        style.configure("Time.TLabel", font=("Helvetica", 12))
        style.configure("Entry.TEntry", font=("Helvetica", 12))
        
        # Style for widgets within the timetable frame
        style.configure("Widget.TLabel", font=("Helvetica", 12), background="lightblue")
        style.configure("Widget.TEntry", font=("Helvetica", 12))

    def create_timetable(self):
        title_label = ttk.Label(self, text="Class Timetable", style="Title.TLabel")
        title_label.pack(pady=10)  # Add some padding to the top
        

        timetable_frame = ttk.Frame(self)
        timetable_frame.pack(expand=True, fill="both")

        # Create time block labels in the header
        ttk.Label(timetable_frame, text="Day / Time", width=15, style="Header.TLabel").grid(row=0, column=0, padx=5, pady=5)
        for i, time in enumerate(self.times):
            label = ttk.Label(timetable_frame, text=time, width=10, style="Widget.TLabel")
            label.grid(row=0, column=i + 1, padx=5, pady=5)

        # Create day labels and entry widgets with the new widget style
        for i, day in enumerate(self.days):
            label = ttk.Label(timetable_frame, text=day, width=15, style="Widget.TLabel")
            label.grid(row=i + 1, column=0, padx=5, pady=5)

            for j, time in enumerate(self.times):
                entry = ttk.Entry(timetable_frame, width=10, style="Widget.TEntry")
                entry.grid(row=i + 1, column=j + 1, padx=5, pady=5)

if __name__ == "__main__":
    app = ClassTimetable()
    app.mainloop()
