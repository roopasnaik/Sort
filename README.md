# Sort
import tkinter as tk
import random
import time

class SortingVisualizer:
    def __init__(self, root):
        self.root = root
        self.root.title("Sorting Algorithm Visualizer")
        self.frame = tk.Frame(self.root)
        self.frame.pack()

        self.label = tk.Label(self.frame, text="Enter numbers separated by space:")
        self.label.grid(row=0, column=0)

        self.input_entry = tk.Entry(self.frame)
        self.input_entry.grid(row=0, column=1)

        self.sort_button = tk.Button(self.frame, text="Sort", command=self.start_sorting)
        self.sort_button.grid(row=0, column=2)

        self.canvas = tk.Canvas(self.root, width=800, height=400)
        self.canvas.pack()

    def start_sorting(self):
        input_list = [int(x) for x in self.input_entry.get().split()]

        sorting_algorithm = self.selection_sort(input_list.copy()) # Change this to your desired sorting algorithm
        self.animate_sorting(sorting_algorithm)

    def animate_sorting(self, sorting_algorithm):
        for step, arr in enumerate(sorting_algorithm):
            self.draw_array(arr)
            self.root.update_idletasks()
            time.sleep(0.05) # Adjust the speed of animation here

    def draw_array(self, arr):
        self.canvas.delete("all")
        width = 800 / len(arr)
        height_scale = 400 / max(arr)
        for i, num in enumerate(arr):
            self.canvas.create_rectangle(i * width, 400, (i+1) * width, 400 - num * height_scale, fill="blue")

    def selection_sort(self, arr):
        n = len(arr)
        for i in range(n-1):
            min_idx = i
            for j in range(i+1, n):
                if arr[j] < arr[min_idx]:
                    min_idx = j
            arr[i], arr[min_idx] = arr[min_idx], arr[i]
            yield arr

    def insertion_sort(self, arr):
        for i in range(1, len(arr)):
            key = arr[i]
            j = i - 1
            while j >= 0 and arr[j] > key:
                arr[j + 1] = arr[j]
                j -= 1
            arr[j + 1] = key
            yield arr

    def merge_sort(self, arr):
        if len(arr) > 1:
            mid = len(arr) // 2
            L = arr[:mid]
            R = arr[mid:]

            yield from self.merge_sort(L)
            yield from self.merge_sort(R)

            i = j = k = 0

            while i < len(L) and j < len(R):
                if L[i] < R[j]:
                    arr[k] = L[i]
                    i += 1
                else:
                    arr[k] = R[j]
                    j += 1
                k += 1

            while i < len(L):
                arr[k] = L[i]
                i += 1
                k += 1

            while j < len(R):
                arr[k] = R[j]
                j += 1
                k += 1
            yield arr

    def quick_sort(self, arr):
        if len(arr) <= 1:
            return arr
        pivot = arr[len(arr) // 2]
        left = [x for x in arr if x < pivot]
        middle = [x for x in arr if x == pivot]
        right = [x for x in arr if x > pivot]
        return self.quick_sort(left) + middle + self.quick_sort(right)


root = tk.Tk()
app = SortingVisualizer(root)
root.mainloop()
import tkinter as tk
import random
import time

class SortingVisualizer:
    def __init__(self, root):
        self.root = root
        self.root.title("Sorting Algorithm Visualizer")
        self.frame = tk.Frame(self.root)
        self.frame.pack()

        self.label = tk.Label(self.frame, text="Enter numbers separated by space:")
        self.label.grid(row=0, column=0)

        self.input_entry = tk.Entry(self.frame)
        self.input_entry.grid(row=0, column=1)

        self.sort_button = tk.Button(self.frame, text="Sort", command=self.start_sorting)
        self.sort_button.grid(row=0, column=2)

        self.canvas = tk.Canvas(self.root, width=800, height=400)
        self.canvas.pack()

    def start_sorting(self):
        input_list = [int(x) for x in self.input_entry.get().split()]

        sorting_algorithm = self.selection_sort(input_list.copy()) # Change this to your desired sorting algorithm
        self.animate_sorting(sorting_algorithm)

    def animate_sorting(self, sorting_algorithm):
        for step, arr in enumerate(sorting_algorithm):
            self.draw_array(arr)
            self.root.update_idletasks()
            time.sleep(0.05) # Adjust the speed of animation here

    def draw_array(self, arr):
        self.canvas.delete("all")
        width = 800 / len(arr)
        height_scale = 400 / max(arr)
        for i, num in enumerate(arr):
            self.canvas.create_rectangle(i * width, 400, (i+1) * width, 400 - num * height_scale, fill="blue")

    def selection_sort(self, arr):
        n = len(arr)
        for i in range(n-1):
            min_idx = i
            for j in range(i+1, n):
                if arr[j] < arr[min_idx]:
                    min_idx = j
            arr[i], arr[min_idx] = arr[min_idx], arr[i]
            yield arr

    def insertion_sort(self, arr):
        for i in range(1, len(arr)):
            key = arr[i]
            j = i - 1
            while j >= 0 and arr[j] > key:
                arr[j + 1] = arr[j]
                j -= 1
            arr[j + 1] = key
            yield arr

    def merge_sort(self, arr):
        if len(arr) > 1:
            mid = len(arr) // 2
            L = arr[:mid]
            R = arr[mid:]

            yield from self.merge_sort(L)
            yield from self.merge_sort(R)

            i = j = k = 0

            while i < len(L) and j < len(R):
                if L[i] < R[j]:
                    arr[k] = L[i]
                    i += 1
                else:
                    arr[k] = R[j]
                    j += 1
                k += 1

            while i < len(L):
                arr[k] = L[i]
                i += 1
                k += 1

            while j < len(R):
                arr[k] = R[j]
                j += 1
                k += 1
            yield arr

    def quick_sort(self, arr):
        if len(arr) <= 1:
            return arr
        pivot = arr[len(arr) // 2]
        left = [x for x in arr if x < pivot]
        middle = [x for x in arr if x == pivot]
        right = [x for x in arr if x > pivot]
        return self.quick_sort(left) + middle + self.quick_sort(right)


root = tk.Tk()
app = SortingVisualizer(root)
root.mainloop()
import tkinter as tk
import random
import time

class SortingVisualizer:
    def __init__(self, root):
        self.root = root
        self.root.title("Sorting Algorithm Visualizer")
        self.frame = tk.Frame(self.root)
        self.frame.pack()

        self.label = tk.Label(self.frame, text="Enter numbers separated by space:")
        self.label.grid(row=0, column=0)

        self.input_entry = tk.Entry(self.frame)
        self.input_entry.grid(row=0, column=1)

        self.sort_button = tk.Button(self.frame, text="Sort", command=self.start_sorting)
        self.sort_button.grid(row=0, column=2)

        self.canvas = tk.Canvas(self.root, width=800, height=400)
        self.canvas.pack()

    def start_sorting(self):
        input_list = [int(x) for x in self.input_entry.get().split()]

        sorting_algorithm = self.selection_sort(input_list.copy()) # Change this to your desired sorting algorithm
        self.animate_sorting(sorting_algorithm)

    def animate_sorting(self, sorting_algorithm):
        for step, arr in enumerate(sorting_algorithm):
            self.draw_array(arr)
            self.root.update_idletasks()
            time.sleep(0.05) # Adjust the speed of animation here

    def draw_array(self, arr):
        self.canvas.delete("all")
        width = 800 / len(arr)
        height_scale = 400 / max(arr)
        for i, num in enumerate(arr):
            self.canvas.create_rectangle(i * width, 400, (i+1) * width, 400 - num * height_scale, fill="blue")

    def selection_sort(self, arr):
        n = len(arr)
        for i in range(n-1):
            min_idx = i
            for j in range(i+1, n):
                if arr[j] < arr[min_idx]:
                    min_idx = j
            arr[i], arr[min_idx] = arr[min_idx], arr[i]
            yield arr

    def insertion_sort(self, arr):
        for i in range(1, len(arr)):
            key = arr[i]
            j = i - 1
            while j >= 0 and arr[j] > key:
                arr[j + 1] = arr[j]
                j -= 1
            arr[j + 1] = key
            yield arr

    def merge_sort(self, arr):
        if len(arr) > 1:
            mid = len(arr) // 2
            L = arr[:mid]
            R = arr[mid:]

            yield from self.merge_sort(L)
            yield from self.merge_sort(R)

            i = j = k = 0

            while i < len(L) and j < len(R):
                if L[i] < R[j]:
                    arr[k] = L[i]
                    i += 1
                else:
                    arr[k] = R[j]
                    j += 1
                k += 1

            while i < len(L):
                arr[k] = L[i]
                i += 1
                k += 1

            while j < len(R):
                arr[k] = R[j]
                j += 1
                k += 1
            yield arr

    def quick_sort(self, arr):
        if len(arr) <= 1:
            return arr
        pivot = arr[len(arr) // 2]
        left = [x for x in arr if x < pivot]
        middle = [x for x in arr if x == pivot]
        right = [x for x in arr if x > pivot]
        return self.quick_sort(left) + middle + self.quick_sort(right)


root = tk.Tk()
app = SortingVisualizer(root)
root.mainloop()
import tkinter as tk
import random
import time

class SortingVisualizer:
    def __init__(self, root):
        self.root = root
        self.root.title("Sorting Algorithm Visualizer")
        self.frame = tk.Frame(self.root)
        self.frame.pack()

        self.label = tk.Label(self.frame, text="Enter numbers separated by space:")
        self.label.grid(row=0, column=0)

        self.input_entry = tk.Entry(self.frame)
        self.input_entry.grid(row=0, column=1)

        self.sort_button = tk.Button(self.frame, text="Sort", command=self.start_sorting)
        self.sort_button.grid(row=0, column=2)

        self.canvas = tk.Canvas(self.root, width=800, height=400)
        self.canvas.pack()

    def start_sorting(self):
        input_list = [int(x) for x in self.input_entry.get().split()]

        sorting_algorithm = self.selection_sort(input_list.copy()) # Change this to your desired sorting algorithm
        self.animate_sorting(sorting_algorithm)

    def animate_sorting(self, sorting_algorithm):
        for step, arr in enumerate(sorting_algorithm):
            self.draw_array(arr)
            self.root.update_idletasks()
            time.sleep(0.05) # Adjust the speed of animation here

    def draw_array(self, arr):
        self.canvas.delete("all")
        width = 800 / len(arr)
        height_scale = 400 / max(arr)
        for i, num in enumerate(arr):
            self.canvas.create_rectangle(i * width, 400, (i+1) * width, 400 - num * height_scale, fill="blue")

    def selection_sort(self, arr):
        n = len(arr)
        for i in range(n-1):
            min_idx = i
            for j in range(i+1, n):
                if arr[j] < arr[min_idx]:
                    min_idx = j
            arr[i], arr[min_idx] = arr[min_idx], arr[i]
            yield arr

    def insertion_sort(self, arr):
        for i in range(1, len(arr)):
            key = arr[i]
            j = i - 1
            while j >= 0 and arr[j] > key:
                arr[j + 1] = arr[j]
                j -= 1
            arr[j + 1] = key
            yield arr

    def merge_sort(self, arr):
        if len(arr) > 1:
            mid = len(arr) // 2
            L = arr[:mid]
            R = arr[mid:]

            yield from self.merge_sort(L)
            yield from self.merge_sort(R)

            i = j = k = 0

            while i < len(L) and j < len(R):
                if L[i] < R[j]:
                    arr[k] = L[i]
                    i += 1
                else:
                    arr[k] = R[j]
                    j += 1
                k += 1

            while i < len(L):
                arr[k] = L[i]
                i += 1
                k += 1

            while j < len(R):
                arr[k] = R[j]
                j += 1
                k += 1
            yield arr

    def quick_sort(self, arr):
        if len(arr) <= 1:
            return arr
        pivot = arr[len(arr) // 2]
        left = [x for x in arr if x < pivot]
        middle = [x for x in arr if x == pivot]
        right = [x for x in arr if x > pivot]
        return self.quick_sort(left) + middle + self.quick_sort(right)


root = tk.Tk()
app = SortingVisualizer(root)
root.mainloop()
