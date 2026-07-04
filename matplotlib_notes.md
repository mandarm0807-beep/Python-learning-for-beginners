# Matplotlib Notes

## 1. Importing the Library

```python
from matplotlib import pyplot as plt
```

This is the standard way to import matplotlib's plotting module.

---

## 2. Line Graphs (Basic Plot)

### Coordinates
```python
x_co_ordinates = [1, 2, 3, 4, 5, 6]
y_co_ordinates = [1, 2, 3, 4, 5, 6]
```

### Plotting
`plt.plot(x, y)` plots both x and y coordinates on the graph.

```python
plt.plot(x_co_ordinates, y_co_ordinates)
plt.show()  # displays the final graph
```

### Axis Labels & Title
```python
plt.xlabel("x co-ordinates")
plt.ylabel("y co-ordinates")
plt.title("simple graph")
```

### Legend
The **legend** helps label the different lines/data plotted on the graph.

```python
plt.legend(["runs", "balls"])
# or, using the label parameter on each plot call:
plt.plot(x_co_ordinates, y_co_ordinates, label="runs")
plt.plot(x_co_ordinates_1, y_co_ordinates_1, label="balls")
plt.legend()
```

### Styling a Plot (Color & Line Details)
```python
plt.plot(x_co_ordinates, y_co_ordinates, label="runs", color="b")  # blue
plt.plot(x_co_ordinates, y_co_ordinates, label="runs", color="r")  # red
```

### Built-in Styles
```python
print(plt.style.available)   # lists all available style names
plt.style.use("name of the style")   # apply a chosen style
```

### XKCD (Comic) Style
```python
plt.xkcd()   # renders the graph in a hand-drawn comic style
```

---

## 3. Pie Charts

### Basic Setup
```python
from matplotlib import pyplot as plt

slices = [20, 60]
labels = ["fans", "celebrity"]
colors = ["violet", "pink"]

plt.pie(slices, labels=labels, colors=colors)
plt.show()
plt.title("my piechart")
```

### Extra Pie Chart Options
| Feature | Purpose | Usage |
|---|---|---|
| `explode` | Pulls a slice out from the center (value = distance from center) | `explode = [0, 0.1]` → pass as `explode=explode` |
| `shadow` | Adds a shadow effect for visual depth | `shadow=True` |
| `startangle` | Rotates the starting angle of the chart | `startangle=90` |
| `autopct` | Displays percentage values on slices | `autopct="%1.1f%%"` |

All of these get passed as keyword arguments inside `plt.pie(...)`.

---

## 4. Stack Plots

### Data
```python
minutes = [1, 2, 3, 4, 5, 6, 7, 8, 9]
player_1 = [1, 2, 3, 3, 4, 4, 4, 4, 5]
player_2 = [1, 1, 1, 1, 2, 2, 2, 2, 3, 3, 3]
player_3 = [1, 1, 1, 2, 2, 2, 3, 3, 3]
```

### Plotting
```python
plt.stackplot(minutes, player_1, player_2, player_3)
plt.show()
```

### Labels & Legend
```python
labels = ["player_1", "player_2", "player_3"]   # pass as labels=labels in stackplot()
plt.legend(loc="upper left")   # positions the legend in the upper-left corner
```

### Colors
```python
colors = ["violet", "pink"]   # pass as colors=colors in stackplot()
```

---

## 5. Working with CSV Files

### Creating a CSV File (PyCharm workflow)
1. Right-click your project → **New** → **File** → name it `names.csv`
2. Open your file explorer/file manager and locate the folder
3. Right-click the file → **Open with** → **PyCharm**
4. Contents can now be copied/edited directly

### Reading a CSV File
```python
import csv

with open("names.csv", "r") as csvfile:
    reader = csv.reader(csvfile)
    for row in reader:
        print(row)
```

**Output:** All columns/rows in the CSV file get printed out, one row at a time.
