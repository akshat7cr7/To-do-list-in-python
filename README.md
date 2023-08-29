# To-do-list-in-python
import tkinter as tk
from tkinter import messagebox

class ToDoListApp:
    def __init__(self, root):
        self.root = root
        self.root.title("To-Do List Application")

        self.tasks = []
        self.task_entry = tk.Entry(root)
        self.task_entry.pack(pady=10)

        add_button = tk.Button(root, text="Add Task", command=self.add_task)
        add_button.pack()

        remove_button = tk.Button(root, text="Remove Task", command=self.remove_task)
        remove_button.pack()

        list_button = tk.Button(root, text="List Tasks", command=self.list_tasks)
        list_button.pack()

    def add_task(self):
        task = self.task_entry.get()
        if task:
            self.tasks.append(task)
            self.task_entry.delete(0, tk.END)
            messagebox.showinfo("Task Added", "Task added successfully!")
        else:
            messagebox.showwarning("Empty Task", "Please enter a task.")

    def remove_task(self):
        task = self.task_entry.get()
        if task in self.tasks:
            self.tasks.remove(task)
            self.task_entry.delete(0, tk.END)
            messagebox.showinfo("Task Removed", "Task removed successfully!")
        else:
            messagebox.showwarning("Task Not Found", "Task not found!")

    def list_tasks(self):
        if not self.tasks:
            messagebox.showinfo("No Tasks", "No tasks found.")
        else:
            tasks_text = "\n".join([f"{i + 1}. {task}" for i, task in enumerate(self.tasks)])
            messagebox.showinfo("Tasks", tasks_text)

def main():
    root = tk.Tk()
    app = ToDoListApp(root)
    root.mainloop()

if __name__ == "__main__":
    main()

