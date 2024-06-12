#python #data-engineering #data-science 

# tkinter
Python comes with tkinter by default.
```python
import tkinter as tk
```

Then we need to create the widget
```python
firstwindow = tk.Label(root, text="Hello World!")
```

Then pack it ("shove it onto the screen") and display it in the main loop:
```python
firstwindow.pack()

root.tk.mainloop()
```

# Grid system in Python

Instead of packing it, we can use grid, a built-in python method to assign grid coordinates to our labels:

```python
firstwindow.grid(row = 0, column= 0)

secondwindow.grid(row = 1, column= 0)
```

If resized, they stay in the same position.

Played around with it:
```python
import tkinter as tk

root = tk.Tk()

firstwindow = tk.Label(root, text="Hi!")
secondwindow = tk.Label(root, text = "My name is")
thirdwindow = tk.Label(root, text="Hi!")
fourthwindow = tk.Label(root, text = "My name is")

firstwindow.grid(row = 0, column= 0)
secondwindow.grid(row = 1, column= 0)
thirdwindow.grid(row = 2, column= 0)
fourthwindow.grid(row = 3, column= 0)

root.tk.mainloop()
```

Which can be simplified as below:
```python
import tkinter as tk

root = tk.Tk()

firstwindow = tk.Label(root, text="Hi!").grid(row = 0, column= 0)
secondwindow = tk.Label(root, text = "My name is").grid(row = 1, column= 0)
thirdwindow = tk.Label(root, text="Hi!").grid(row = 2, column= 0)
fourthwindow = tk.Label(root, text = "My name is").grid(row = 3, column= 0)


root.tk.mainloop()
```

# Creating Buttons
Buttons are easy to make, using the `Button()` method:
```python
import tkinter as tk

root = tk.Tk()

mybutton = tk.Button(root, text="Click me")
mybutton.pack()
root.tk.mainloop()
```

We can disable the button with the `state` kwarg:
```python
mybutton = tk.Button(root, text="Click me", state="disabled")
```

And add padding with `padx` and `pady` kwargs:
```python
mybutton = tk.Button(root, text="Click me", padx=50, pady= 50)
```

### Buttons with visual output
To have the button action something we can use a function:
```python
def my_click():
    labelwindow = tk.Label(root, text="I clicked the button")
    labelwindow.pack()

mybutton = tk.Button(root, text="Click me", padx=50, pady= 50, command=my_click)
```

### Changing Colour of Buttons
To change the colour of the text (foreground) we can use the `fg=` kwarg:
```python
mybutton = tk.Button(root, text="Click me", padx=50, pady= 50, command=my_click, fg="blue")
```

And background:
```python
mybutton = tk.Button(root, text="Click me", padx=50, pady= 50, command=my_click, fg="blue", bg="red")
```


# Input Fields

To have a basic entry we use the `Entry()` tkinter method
```python
my_entry = tk.Entry()
my_entry.pack()
```

The width can also be changed:
```python
my_entry = tk.Entry(root, width=50)
my_entry.pack()
```

Like in the button, the `fg` and `bg` can also be changed.
The `borderwidth` can also be changed to be raised:
```python
my_entry = tk.Entry(root, width=50, borderwidth=15, fg="blue", bg="black")
```

To get entry we can link up the button and text with the get method:

```python
import tkinter as tk

root = tk.Tk()
my_entry = tk.Entry(root, width=50, borderwidth=8)
my_entry.pack()

def my_click():
    labelwindow = tk.Label(root, text=my_entry.get())
    labelwindow.pack()

mybutton = tk.Button(root, text="Enter your name", padx=50, pady= 50, command=my_click, fg="blue", bg="red")

mybutton.pack()

root.tk.mainloop()
```

Can also use a f-string inside to have a concatenated string:
```python
def my_click():w
    labelwindow = tk.Label(root, text=f"Hello {my_entry.get()}")=
    labelwindow.pack()
```

Or even a variable
```python
def my_click():

    my_text = f"Hello {my_entry.get()}"
    labelwindow = tk.Label(root, text=my_text)
    labelwindow.pack()
```