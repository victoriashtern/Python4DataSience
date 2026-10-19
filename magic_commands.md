# Important Jupyter Magic Commands

Jupyter Notebook provides special commands called **Magic Commands** that help you perform tasks such as measuring execution time, inspecting variables, and accessing command documentation.

## Common Magic Commands

| Magic Command | Description |
| --- | --- |
| `%time` | Measures the execution time of a single statement. |
| `%%time` | Measures the execution time of all statements in a notebook cell. |
| `%whos` | Displays variables in the current namespace, including their names, types, and values. |
| `%magic` | Displays documentation for IPython Magic commands. |

## Examples

### 1\. `%time` — Measure a Single Statement

```
%time sum(range(1000000))
```

Measures how long the statement takes to execute.

### 2\. `%%time` — Measure an Entire Cell

```
%%time

numbers = list(range(1000000))
total = sum(numbers)
average = total / len(numbers)
```

Measures the total execution time of the entire cell.

### 3\. `%whos` — Inspect Variables

```
name = "Data Analysis"
count = 100
scores = [85, 90, 95]

%whos
```

Displays the variables currently defined in the notebook, along with information such as their types and values.

### 4\. `%magic` — View Magic Command Documentation

```
%magic
```

Displays the general reference documentation for IPython Magic commands.

## Additional Resources

- [IPython Magic Commands Documentation](<https://ipython.readthedocs.io/en/stable/interactive/magics.html>)
- [Jupyter Notebook Documentation](<https://docs.jupyter.org/>)

```
- [Jupyter Magic Commands](data-analysis/jupyter-magic-commands.md)
```
