
import numpy as np
import matplotlib.pyplot as plt

try:
    print("Enter a mathematical equation in terms of x (e.g., x**2, np.sin(x), np.exp(x), or a constant like 5):")
    equation = input("y = ")
    x = np.linspace(-10, 10, 500)

    try:
        y = eval(equation, {"np": np, "x": x}) 
    except Exception as inner_e:
        print(f"Invalid equation: {inner_e}")
        
    if np.isscalar(y):
        y = np.full_like(x, y)  

    plt.figure(figsize=(8, 6))
    plt.plot(x, y, label=f"y = {equation}")
    plt.axhline(0, color='black', linewidth=0.7, linestyle='--')
    plt.axvline(0, color='black', linewidth=0.5, linestyle='--')
    plt.title("Graph of the Equation")
    plt.xlabel("x")
    plt.ylabel("y")
    plt.legend()
    plt.grid(True, linestyle='--', alpha=0.7)
    plt.show()

except Exception as e:
    print(f"An error occurred: {e}")


