# bmi_calculator
A simple Python Tkinter application to calculate Body Mass Index (BMI) and show weight category.
import tkinter as tk

def calculate_bmi():
    try:
        weight = float(weight_entry.get())
        height = float(height_entry.get()) / 100  # cm → meters
        bmi = weight / (height ** 2)
        result_label.config(text=f"BMI: {bmi:.2f}")
        
        if bmi < 18.5:
            comment_label.config(text="Category: Underweight", fg="blue")
        elif 18.5 <= bmi < 24.9:
            comment_label.config(text="Category: Normal", fg="green")
        elif 25 <= bmi < 29.9:
            comment_label.config(text="Category: Overweight", fg="orange")
        else:
            comment_label.config(text="Category: Obese", fg="red")
    except:
        result_label.config(text="Please enter valid numbers!")
        comment_label.config(text="")

# Main window
window = tk.Tk()
window.title("BMI Calculator")
window.geometry("300x250")

# Weight input
tk.Label(window, text="Weight (kg):").pack()
weight_entry = tk.Entry(window)
weight_entry.pack(pady=5)

# Height input
tk.Label(window, text="Height (cm):").pack()
height_entry = tk.Entry(window)
height_entry.pack(pady=5)

# Calculate button
calculate_button = tk.Button(window, text="Calculate", command=calculate_bmi)
calculate_button.pack(pady=10)

# Result label
result_label = tk.Label(window, text="", font=("Arial", 12))
result_label.pack()

# Comment label
comment_label = tk.Label(window, text="", font=("Arial", 12, "bold"))
comment_label.pack()

# Run the window
window.mainloop()

