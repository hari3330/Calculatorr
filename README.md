# Calculatorr
import tkinter as tk
import os

def on_click(button_value):
    if button_value == "=":
        try:
            result = eval(entry.get())
            entry.delete(0, tk.END)
            entry.insert(tk.END, str(result))
        except Exception as e:
            entry.delete(0, tk.END)
            entry.insert(tk.END, "Error")
    elif button_value == "C":
        entry.delete(0, tk.END)
    else:
        entry.insert(tk.END, button_value)

# Create the main window
root = tk.Tk()
root.title("Calculator")
root.wm_geometry("350x420")

# script_directory = os.path.dirname(os.path.abspath(__file__))
#
# #Join the script directory with the icon filename
# icon_filename = "Calculatorr.ico"  # Replace with the actual icon filename
# icon_path = os.path.join(script_directory, icon_filename)


root.iconbitmap("Calculatorr.ico" )
root.resizable(False, False)

# Entry widget to display the calculations
entry = tk.Entry(root, font=("Helvetica", 20), justify="right")
entry.grid(row=0, column=0, columnspan=4, padx=10, pady=10)

# Define the buttons
buttons = [
    '7', '8', '9', '/',
    '4', '5', '6', '*',
    '1', '2', '3', '-',
    '0', '.', '=', '+',
    'C'
]

# Create and place the buttons on the grid
row, col = 1, 0
for button_value in buttons:
    button = tk.Button(root, text=button_value, font=("Helvetica", 15), width=5, height=2, command=lambda val=button_value: on_click(val))
    button.grid(row=row, column=col, padx=5, pady=5)
    col += 1
    if col > 3:
        col = 0
        row += 1

# Run the main event loop
root.mainloop()
