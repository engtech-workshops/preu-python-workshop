# Data visualiser

??? abstract "Slides"
    <div class="reveal deck1">
      <div class="slides">
        <section data-markdown>
          <textarea data-template>
            # Problem
          	---
            ## Problem
            Create a piece of software to allow a user to import a table and plot a 2D graph with x, y, and color axes. The user can choose the columns to use for the different axes.
          	---
            ## What are the different components/parts to achieve this?
            ---
            Create a piece of software to allow a user to **import a table** and **plot a 2D graph** with x, y, and color axes. The user can **choose the columns** to use for the different axes.
            ---
            ## Structure of the software/<br>flow of the code
            ---
            <svg style="width:600px;height:600px" viewBox="0 0 600 800">
            	<text x="300" y="100" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">Ask user to import a table</text>
            	<text x="300" y="300" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">Load the table</text>
            	<text x="300" y="500" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">
                <tspan x="300" dy="0em">Ask user to choose columns</tspan>
                <tspan x="300" dy="1.2em">for x, y, and color axes</tspan>
              </text>
              <text x="300" y="750" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">Plot 2D graph</text>
            	<path d="M 300,150 l 0,100 l -10,-20 c 0,0 10,15 20,0 l -10,20" style="stroke:var(--r-main-color);fill:var(--r-main-color)"/>
            	<path d="M 300,350 l 0,100 l -10,-20 c 0,0 10,15 20,0 l -10,20" style="stroke:var(--r-main-color);fill:var(--r-main-color)"/>
              <path d="M 300,600 l 0,100 l -10,-20 c 0,0 10,15 20,0 l -10,20" style="stroke:var(--r-main-color);fill:var(--r-main-color)"/>
          	</svg>
            ---
            Before moving forward,
            # Launch Spyder
            <img src="https://www.spyder-ide.org/static/images/spyder_logo.png"/>
            ---
            We have many options to write a software, today we will be using
            ## Python programming language
            ---
            A programming language defines the syntax (i.e. the vocabulary and the grammar) to allow the computer to understand our instructions.
            ---
            <svg style="width:600px;height:600px" viewBox="0 0 600 800">
            	<text x="300" y="100" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">Ask user to import a table</text>
            	<text x="300" y="300" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">Load the table</text>
            	<text x="300" y="500" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">
                <tspan x="300" dy="0em">Ask user to choose columns</tspan>
                <tspan x="300" dy="1.2em">for x, y, and color axes</tspan>
              </text>
              <text x="300" y="750" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">Plot 2D graph</text>
            	<path d="M 300,150 l 0,100 l -10,-20 c 0,0 10,15 20,0 l -10,20" style="stroke:var(--r-main-color);fill:var(--r-main-color)"/>
            	<path d="M 300,350 l 0,100 l -10,-20 c 0,0 10,15 20,0 l -10,20" style="stroke:var(--r-main-color);fill:var(--r-main-color)"/>
              <path d="M 300,600 l 0,100 l -10,-20 c 0,0 10,15 20,0 l -10,20" style="stroke:var(--r-main-color);fill:var(--r-main-color)"/>
          	</svg>
            ---
            ## Ask user to import a table
            We will be asking the user to import a table in the csv file format.
            ---
            CSV (comma-separated values) file looks like this
            <br><br>
            <span class="codespan">
              a,b,c<br>
              1,2,3<br>
              2,4,5<br>
              6,5,4<br>
            </span>
            ---
            ## Make sure you have the `data.csv` file on your machine
            ---
            ## Ask user to import a table
            In Spyder, we need to call a function to let the user to choose the CSV file to be imported.
            ---
            ### A function is a set of code to achieve a specific purpose.
            Functions are provided by libraries (collections of functions) or you can write your own functions.
            ---
            ## Ask user to import a table
            To let the user choose the CSV file, we can use the `askopenfilename` function provided by `tkinter.filedialog`.
            ```python
            from tkinter import Tk, filedialog

            Tk().withdraw()
            filename = filedialog.askopenfilename()
            ```
            Press <kbd>F5</kbd> or click the play button to run the code.
            ---
            ## Ask user to import a table
            The user can now select any file and the variable `filename` will have the path to the file.
            <br><br>
            Try to select any file and go to Variable explorer (on the upper right of the Spyder window) to verify.
            ---
            ## Ask user to import a table
            As we only want the user to choose CSV file and not other types of files, we can specify the file type as the argument to the function.
            ```python
            filename = filedialog.askopenfilename(filetypes=[("CSV file","*.csv")])
            ```
            This will limit the user to only be able to select files with `.csv` extension.
            ---
            We can also show the user the file that has been selected. 
            ```python
            print(filename)
            ```
            ---
            Now that we have the file we want to import,
            <svg style="width:600px;height:600px" viewBox="0 0 600 800">
            	<text x="300" y="100" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">Ask user to import a table</text>
            	<text x="300" y="300" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">Load the table</text>
            	<text x="300" y="500" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">
                <tspan x="300" dy="0em">Ask user to choose columns</tspan>
                <tspan x="300" dy="1.2em">for x, y, and color axes</tspan>
              </text>
              <text x="300" y="750" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">Plot 2D graph</text>
            	<path d="M 300,150 l 0,100 l -10,-20 c 0,0 10,15 20,0 l -10,20" style="stroke:var(--r-main-color);fill:var(--r-main-color)"/>
            	<path d="M 300,350 l 0,100 l -10,-20 c 0,0 10,15 20,0 l -10,20" style="stroke:var(--r-main-color);fill:var(--r-main-color)"/>
              <path d="M 300,600 l 0,100 l -10,-20 c 0,0 10,15 20,0 l -10,20" style="stroke:var(--r-main-color);fill:var(--r-main-color)"/>
          	</svg>
            ---
            ## Load the table
            We need to load the content of the file into the code to use them.
            ---
            ## Load the table
            To do so we need to read the file content and save the content to a variable in the code.
            ```python
            with open(filename, "r") as f:
              ...
            ```
            We read (`r`) the file content using the `open` function.
            ---
            ## Load the table
            Since this is a CSV file, we need to import a library that helps us to read CSV file content correctly.
            ```python
            import csv
            ```
            Add this line at the top of the file
            ---
            ## Load the table
            We will read the CSV content as `dictionary` in Python, and save it to the variable `data` row-by-row.
            ```python
            with open(filename, "r") as f:
              reader = csv.DictReader(f)
              data = []
              for row in reader:
                data.append(row)
            ```
            ---
            The `for`-loop is an iterative (repetitive) loop that goes through CSV content.
            ---
            ## Load the table
            After running the code, go to the variable explorer > find and double click on `data`.
            <br><br>
            You should see that it is a `list` of `dict`. Each row in the CSV file now becomes a `dict` item in the list with the column names as keys.
            ```python
            data = [
              { 'idx': '0', 'age': '59', 'bmi': '32.1', ... },
              ...
            ]
            ```
            ---
            Now that we have load the table into the code, 
            <svg style="width:600px;height:600px" viewBox="0 0 600 800">
            	<text x="300" y="100" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">Ask user to import a table</text>
            	<text x="300" y="300" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">Load the table</text>
            	<text x="300" y="500" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">
                <tspan x="300" dy="0em">Ask user to choose columns</tspan>
                <tspan x="300" dy="1.2em">for x, y, and color axes</tspan>
              </text>
              <text x="300" y="750" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">Plot 2D graph</text>
            	<path d="M 300,150 l 0,100 l -10,-20 c 0,0 10,15 20,0 l -10,20" style="stroke:var(--r-main-color);fill:var(--r-main-color)"/>
            	<path d="M 300,350 l 0,100 l -10,-20 c 0,0 10,15 20,0 l -10,20" style="stroke:var(--r-main-color);fill:var(--r-main-color)"/>
              <path d="M 300,600 l 0,100 l -10,-20 c 0,0 10,15 20,0 l -10,20" style="stroke:var(--r-main-color);fill:var(--r-main-color)"/>
          	</svg>
            ---
            ## Ask user to choose columns
            Before choosing columns, we should tell the user what are the columns available.
            <br>
            <br>
            We can get the column names using
            ```python
            colnames = list(data[0].keys())
            ```
            ---
            You can go to variable explorer > `colnames` to verify after you have ran the code.
            ---
            ## Ask user to choose columns
            We want to make sure the user knows what to do and how to choose, therefore we need to write the instructions using `print`.
            ```python
            print("Select variable for x-axis using the index:")
            ```
            ---
            ## Ask user to choose columns
            As `colnames` is a list, we can use `for`-loop to go through it to `print` each of them on the screen.
            ```python
            for c in colnames:
              print(f"{c}")
            ```
            ---
            ## Ask user to choose columns
            You will see each column name printed on one line. But it doesn't provide an easy way to choose.
            ---
            ## Ask user to choose columns
            We can add an index to each of the column name using `enumerate`.
            ```python
            for i,c in enumerate(colnames):
              print(f"{i} {c}")
            ```
            ---
            ## Ask user to choose columns
            Next we need to let the user to tell us which column is selected.
            ```python
            selection = input("x-axis variable: ")
            ```
            ---
            The code will now stop and wait for a user input when you run the code.
            ---
            ## Ask user to choose columns
            The `selection` will save the user input as a text, not a number. 
            <br><br>
            In our case we will need to convert the user input to number:
            ```python
            xidx = int(selection)
            ```
            ---
            ## Ask user to choose columns
            Then we save the column name that the user has selected into the variable `xvar`.
            ```python
            xvar = colnames[xidx]
            ```
            ---
            At this point, your code should look like
            ```python
            import csv
            from tkinter import Tk, filedialog

            Tk().withdraw()
            filename = filedialog.askopenfilename(filetypes=[("CSV file","*.csv")])

            print(filename)
            with open(filename, "r") as f:
              reader = csv.DictReader(f)
              data = []
              for row in reader:
                data.append(row)

            colnames = list(data[0].keys())

            print("Select variable for x-axis:")
            for i,c in enumerate(colnames):
              print(f"{i} {c}")
            selection = input("x-axis variable: ")
            xidx = int(selection)
            xvar = colnames[xidx]
            ```
            ---
            Now we repeat the code for the user to choose the columns for y-axis,
            ```python
            print("Select variable for y-axis:")
            for i,c in enumerate(colnames):
              print(f"{i} {c}")
            selection = input("y-axis variable: ")
            yidx = int(selection)
            yvar = colnames[yidx]
            ```
            ---
            and color.
            ```python
            print("Select variable for color:")
            for i,c in enumerate(colnames):
              print(f"{i} {c}")
            selection = input("color variable: ")
            cidx = int(selection)
            cvar = colnames[cidx]
            ```
            ---
            Before moving forward to the plotting, we can print out the selections to be viewed.
            ```python
            print(f"Plotting {yvar} against {xvar} with color representing {cvar}...")
            ```
            ---
            <svg style="width:600px;height:600px" viewBox="0 0 600 800">
            	<text x="300" y="100" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">Ask user to import a table</text>
            	<text x="300" y="300" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">Load the table</text>
            	<text x="300" y="500" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">
                <tspan x="300" dy="0em">Ask user to choose columns</tspan>
                <tspan x="300" dy="1.2em">for x, y, and color axes</tspan>
              </text>
              <text x="300" y="750" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">Plot 2D graph</text>
            	<path d="M 300,150 l 0,100 l -10,-20 c 0,0 10,15 20,0 l -10,20" style="stroke:var(--r-main-color);fill:var(--r-main-color)"/>
            	<path d="M 300,350 l 0,100 l -10,-20 c 0,0 10,15 20,0 l -10,20" style="stroke:var(--r-main-color);fill:var(--r-main-color)"/>
              <path d="M 300,600 l 0,100 l -10,-20 c 0,0 10,15 20,0 l -10,20" style="stroke:var(--r-main-color);fill:var(--r-main-color)"/>
          	</svg>
            ---
            ## Plot 2D graph
            To plot a 2D graph with color axis, we need the list of x values, list of y values, and the list of color values.
            ```python
            x = []
            y = []
            c = []
            for d in data:
              x.append(d[xvar])
              y.append(d[yvar])
              c.append(d[cvar])
            ```
            Since the CSV content is read row-by-row, we need to extract the value for the axes from each row.
            ---
            ## Plot 2D graph
            When we read from CSV file, by default, the content in the file is read as texts, not numbers.
            <br><br>
            To plot a graph, we need to convert the text values to be numbers.
            ```python
            for d in data:
              x.append(float(d[xvar]))
              y.append(float(d[yvar]))
              c.append(float(d[cvar]))
            ```
            ---
            ## Plot 2D graph
            The graph plotting functions in Python are provided by the library `matplotlib`.
            <br>
            <br>
            Add `import matplotlib.pyplot as plt` at the beginning of the code.
            ---
            ## Plot 2D graph
            We will be plotting a 2D graph using dots with x and y coordinates and color representing a variable.
            <br>
            <br>
            This is achieved by creating a scatter plot.
            ```python
            plt.scatter(x,y,c=c)
            ```
            ---
            ```python
            for d in data:
              x.append(float(d[xvar]))
              y.append(float(d[yvar]))
              c.append(float(d[cvar]))

            plt.scatter(x, y, c=c)
            ```
            ---
            You can view the plotted graph in the upper right section of Spyder under "Plots".
            ---
            At this point there is no label on x and y axes, and the meaning of the colors.
            ---
            Add labels for x and y axes, and the color bar.
            ```python
            plt.xlabel(xvar)
            plt.ylabel(yvar)
            plt.colorbar()
            ```
            ---
            We can also add title to describe the graph.
            ```python
            plt.title(f"{cvar} at different {xvar} and {yvar}")
            ```
            ---
            ## Additional considerations
            Let's make some modifications to make the code runs continuously so the user can plot different graphs with the same set of data.
            ---
            To do so, we need to make the column choosing and graph plotting to repeat.
            ```python
            while True:
              print("Select variable for x-axis:")
              ...
              plt.title(f"{cvar} at different {xvar} and {yvar}")
            ```
            `while True` allows the part of code repeats infinitely.
            ---
            We can now plot a graph and continue to plot the next graph.
            ---
            However, we can't exit the program, because it will run forever...
            ---
            Let's add an option for the user to exit the program.
            ```python
            for i,c in enumerate(colnames):
              print(f"{i} {c}")
            print("q. Quit") # add this new line
            ```
            Add this line for all x, y, and color selections.
            ---
            Then we need to modify to code so the program knows what to do when the user chooses `q`.
            ```python
            selection = input("x-axis variable: ")
            if selection == "q":
              break
            else:
              xidx = int(selection)
              xvar = colnames[xidx]
            ```
            The `if-else` conditional statement allows the code to behave differently based on certain condition.
            <br><br>
            The `break` keyword will jump out of the `while`-loop and therefore exit the program.
            ---
            Repeat this for y-axis selection and color-axis selection.
            ```python
            selection = input("y-axis variable: ")
            if selection == "q":
              break
            else:
              yidx = int(selection)
              yvar = colnames[yidx]
            ```
            <br>
            ```python
            selection = input("color variable: ")
            if selection == "q":
              break
            else:
              cidx = int(selection)
              cvar = colnames[cidx]
            ```
            ---
            Now we have a program that plots multiple graphs from the same files based on user's inputs and able to exit when asked to.
          </textarea>
        </section>
      </div>
    </div>
    !!! info inline end ""
        <kbd>F</kbd> for fullscreen &middot;
        <kbd>O</kbd> for overview

## Problem

Create a piece of software to allow a user to import a table and plot a 2D graph with x, y, and color axes. The user can choose the columns to use for the different axes.

## What are the different components/parts to achieve this?

Create a piece of software to allow a user to **import a table** and **plot a 2D graph** with x, y, and color axes. The user can **choose the columns** to use for the different axes.

<figure>
  <svg style="width:600px;height:600px" viewBox="0 0 600 800">
    <text x="300" y="100" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">Ask user to import a table</text>
    <text x="300" y="300" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">Load the table</text>
    <text x="300" y="500" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">
      <tspan x="300" dy="0em">Ask user to choose columns</tspan>
      <tspan x="300" dy="1.2em">for x, y, and color axes</tspan>
    </text>
    <text x="300" y="750" text-anchor="middle" dominant-baseline="middle" style="fill:var(--r-main-color)">Plot 2D graph</text>
    <path d="M 300,150 l 0,100 l -10,-20 c 0,0 10,15 20,0 l -10,20" style="stroke:var(--r-main-color);fill:var(--r-main-color)"/>
    <path d="M 300,350 l 0,100 l -10,-20 c 0,0 10,15 20,0 l -10,20" style="stroke:var(--r-main-color);fill:var(--r-main-color)"/>
    <path d="M 300,600 l 0,100 l -10,-20 c 0,0 10,15 20,0 l -10,20" style="stroke:var(--r-main-color);fill:var(--r-main-color)"/>
  </svg>
  <figcaption>Structure of the software/flow of the code</figcaption>
</figure>

!!! info "Before moving forward"
    Launch Spyder
    
    <img src="https://www.spyder-ide.org/static/images/spyder_logo.png"/>

## Ask user to import a table
1. We will be asking the user to import a table in the csv file format.
    
    !!! info "CSV (comma-separated values) file looks like this"
        <span class="codespan">
          a,b,c<br>
          1,2,3<br>
          2,4,5<br>
          6,5,4<br>
        </span>

    !!! info 
        Make sure you have the `data.csv` file on your machine

2. In Spyder, we need to call a function to let the user to choose the CSV file to be imported.

    !!! info "Functions"
        A function is a set of code to achieve a specific purpose.

        Functions are provided by libraries (collections of functions) or you can write your own functions.

3. To let the user choose the CSV file, we can use the `askopenfilename` function provided by `tkinter.filedialog`.
    ```python
    from tkinter import Tk, filedialog

    Tk().withdraw()
    filename = filedialog.askopenfilename()
    ```
    Press <kbd>F5</kbd> or click the play button to run the code.

4. The user can now select any file and the variable `filename` will have the path to the file.

5. Try to select any file and go to Variable explorer (on the upper right of the Spyder window) to verify.

6. As we only want the user to choose CSV file and not other types of files, we can specify the file type as the argument to the function.
    ```python
    filename = filedialog.askopenfilename(filetypes=[("CSV file","*.csv")])
    ```
    This will limit the user to only be able to select files with `.csv` extension.

7. We can also show the user the file that has been selected. 
    ```python
    print(filename)
    ```

## Load the table
1. We need to load the content of the file into the code to use them.
2. To do so we need to read the file content and save the content to a variable in the code.
    ```python
    with open(filename, "r") as f:
      ...
    ```
    We read (`r`) the file content using the `open` function.
3. Since this is a CSV file, we need to import a library that helps us to read CSV file content correctly.
    ```python
    import csv
    ```
    Add this line at the top of the file
4. We will read the CSV content as `dictionary` in Python, and save it to the variable `data` row-by-row.
    ```python
    with open(filename, "r") as f:
      reader = csv.DictReader(f)
      data = []
      for row in reader:
        data.append(row)
    ```

    !!! info "for-loop"
        The `for`-loop is an iterative (repetitive) loop that goes through CSV content.

5. After running the code, go to the variable explorer > find and double click on `data`.

    You should see that it is a `list` of `dict`. Each row in the CSV file now becomes a `dict` item in the list with the column names as keys.
    ```python
    data = [
      { 'idx': '0', 'age': '59', 'bmi': '32.1', ... },
      ...
    ]
    ```

## Ask user to choose columns
1. Before choosing columns, we should tell the user what are the columns available.
2. We can get the column names using
    ```python
    colnames = list(data[0].keys())
    ```
    
    !!! info
        You can go to variable explorer > `colnames` to verify after you have ran the code.

4. We want to make sure the user knows what to do and how to choose, therefore we need to write the instructions using `print`.
    ```python
    print("Select variable for x-axis using the index:")
    ```
5. As `colnames` is a list, we can use `for`-loop to go through it to `print` each of them on the screen.
    ```python
    for c in colnames:
      print(f"{c}")
    ```
    You will see each column name printed on one line. But it doesn't provide an easy way to choose.
7. We can add an index to each of the column name using `enumerate`.
    ```python
    for i,c in enumerate(colnames):
      print(f"{i} {c}")
    ```
8. Next we need to let the user to tell us which column is selected.
    ```python
    selection = input("x-axis variable: ")
    ```
9. The code will now stop and wait for a user input when you run the code.
10. The `selection` will save the user input as a text, not a number. In our case we will need to convert the user input to number:
    ```python
    xidx = int(selection)
    ```
11. Then we save the column name that the user has selected into the variable `xvar`.
    ```python
    xvar = colnames[xidx]
    ```
12. At this point, your code should look like
    ```python
    import csv
    from tkinter import Tk, filedialog

    Tk().withdraw()
    filename = filedialog.askopenfilename(filetypes=[("CSV file","*.csv")])

    print(filename)
    with open(filename, "r") as f:
      reader = csv.DictReader(f)
      data = []
      for row in reader:
        data.append(row)

    colnames = list(data[0].keys())

    print("Select variable for x-axis:")
    for i,c in enumerate(colnames):
      print(f"{i} {c}")
    selection = input("x-axis variable: ")
    xidx = int(selection)
    xvar = colnames[xidx]
    ```
13. Now we repeat the code for the user to choose the columns for y-axis,
    ```python
    print("Select variable for y-axis:")
    for i,c in enumerate(colnames):
      print(f"{i} {c}")
    selection = input("y-axis variable: ")
    yidx = int(selection)
    yvar = colnames[yidx]
    ```
    and color.
    ```python
    print("Select variable for color:")
    for i,c in enumerate(colnames):
      print(f"{i} {c}")
    selection = input("color variable: ")
    cidx = int(selection)
    cvar = colnames[cidx]
    ```
14. Before moving forward to the plotting, we can print out the selections to be viewed.
    ```python
    print(f"Plotting {yvar} against {xvar} with color representing {cvar}...")
    ```

## Plot 2D graph
1. To plot a 2D graph with color axis, we need the list of x values, list of y values, and the list of color values.
    ```python
    x = []
    y = []
    c = []
    for d in data:
      x.append(d[xvar])
      y.append(d[yvar])
      c.append(d[cvar])
    ```
    Since the CSV content is read row-by-row, we need to extract the value for the axes from each row.
2. When we read from CSV file, by default, the content in the file is read as texts, not numbers. To plot a graph, we need to convert the text values to be numbers.
    ```python
    for d in data:
      x.append(float(d[xvar]))
      y.append(float(d[yvar]))
      c.append(float(d[cvar]))
    ```
3. The graph plotting functions in Python are provided by the library `matplotlib`. Add `import matplotlib.pyplot as plt` at the beginning of the code.
4. We will be plotting a 2D graph using dots with x and y coordinates and color representing a variable. This is achieved by creating a scatter plot.
    ```python
    plt.scatter(x,y,c=c)
    ```

    !!! info
        You can view the plotted graph in the upper right section of Spyder under "Plots".

6. At this point there is no label on x and y axes, and the meaning of the colors. Add labels for x and y axes, and the color bar.
    ```python
    plt.xlabel(xvar)
    plt.ylabel(yvar)
    plt.colorbar()
    ```
7. We can also add title to describe the graph.
    ```python
    plt.title(f"{cvar} at different {xvar} and {yvar}")
    ```

## Additional considerations
1. Let's make some modifications to make the code runs continuously so the user can plot different graphs with the same set of data.
2. To do so, we need to make the column choosing and graph plotting to repeat.
    ```python
    while True:
      print("Select variable for x-axis:")
      ...
      plt.title(f"{cvar} at different {xvar} and {yvar}")
    ```
    `while True` allows the part of code repeats infinitely.
3. We can now plot a graph and continue to plot the next graph. However, we can't exit the program, because it will run forever...
4. Let's add an option for the user to exit the program.
    ```python
    for i,c in enumerate(colnames):
      print(f"{i} {c}")
    print("q. Quit") # add this new line
    ```
    Add this line for all x, y, and color selections.
5. Then we need to modify to code so the program knows what to do when the user chooses `q`.
    ```python
    selection = input("x-axis variable: ")
    if selection == "q":
      break
    else:
      xidx = int(selection)
      xvar = colnames[xidx]
    ```
   
    !!! info 
        The `if-else` conditional statement allows the code to behave differently based on certain condition.

    !!! info
        The `break` keyword will jump out of the `while`-loop and therefore exit the program.

6. Repeat this for y-axis selection and color-axis selection.
    ```python
    selection = input("y-axis variable: ")
    if selection == "q":
      break
    else:
      yidx = int(selection)
      yvar = colnames[yidx]
    ```

    ```python
    selection = input("color variable: ")
    if selection == "q":
      break
    else:
      cidx = int(selection)
      cvar = colnames[cidx]
    ```

7. Now we have a program that plots multiple graphs from the same files based on user's inputs and able to exit when asked to.