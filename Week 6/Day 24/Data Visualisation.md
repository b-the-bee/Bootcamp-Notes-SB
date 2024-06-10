#data-science #data-engineering 

## Learning Objectives
- Understand what data visualisation is and when to use it
- Identify some data visualisation tools
- Discover some data visualisation techniques
- Gain insight into when to use Jupyter Notebook
- Implement visualisations using Jupyter and matplotlib


## What is data visualisation?
- A graphical representation of any data or information
- Visual elements such as charts, graphs, tables and maps are some tools that provide viewers with an easy and accessible way of understanding information
- Assists in understanding patterns or trends in data that otherwise wouldn't be spotted in raw data
- Used in all aspects of industries


## Why is it important?
- Easy to digest large quantities of information in a small space
- Establishes relationships between data
- Easy to share (image, web page, git repo etc.)
- Can be interactive with clicks, zoom and expanded areas
- Much more intuitive than raw data

## Data Visualisation Tools
We'll be using two tools.

The first is called `Jupyter Notebook`, an open-source web-based interactive computational environment. We will be utilising a `VSCode` extension for running these.

The second is called `matplotlib`, a plotting library in Python to generate visualisations from code.

You can use `matplotlib` on its own in Python or use it alongside `Jupyter`.

Notes: For fun, Jupyter is a portmanteau of the programming languages - Julia, Python and R.


## Data Visualisation Techniques
- Know the audience / who is going to be viewing it
- Set goals for what you want to convey through the viz
- Choose a relevant chart type that best represents the data
- Use a colour scheme that represents different aspects of the data
- Use the best tools for the job

## Data Visualisation in Business
Data visualisations are not just for scientific research, we see them everywhere in life and business.

- Reports
- Displays
- Operation alerting
- Business growth / financial objectives
- Many more!

## Graphs

- Used when you want to show patterns, trends and relationships in the numbers
- An excellent way to tell a story or to summarise something complex
- Can reveal insights that would otherwise be hidden
- Great for spotting errors or outliers in the data

### Components of Effective Graphs...

Not all components outlined in the following slides must be included in every graph. However, it's essential to consider them when designing your graph. The primary question you should be asking is:

**Does this element make my graph easier to understand and interpret?**


- **Title**: Provide a concise and descriptive title that summarizes the main message, giving context to the viewer
- **Axes**: Label each axis clearly, indicating what is plotted on both axes of the graph. Include relevant units, if applicable. For self-explanatory axes, such as years, labels may be optional
- **Scale**: Choose an appropriate scale for both axes to ensure that the data is displayed clearly and accurately. Consider using logarithmic scales if necessary

- **Annotations**: Incorporate annotations to emphasize key areas, guide the viewer's attention, or to better explain the data story
- **Legend**: Include a legend if multiple data series or points are represented by different colors, symbols, or line styles. Ensure the legend is clear, concise, and easy to read
- **Data visualization type**: Select the most appropriate type of graph for your data, such as bar graphs, line charts, scatter plots, or pie charts, based on the data you want to present

- **Consistent formatting**: Use consistent formatting for elements like fonts, colors, and line styles to make your graph aesthetically pleasing and easy to understand
- **Grid lines**: Consider adding grid lines to improve readability, especially when dealing with large datasets or complex graphs. However, avoid cluttering the graph with too many lines
- **Citing data sources**: If you are using data from external sources, provide proper attribution and citations at the bottom of your graph or in the accompanying notes

## Bar Graphs

- Work well for comparing the magnitude of different categories
- Can also be used to show time-series, deviation and distributions
- Have either horizontal or vertical bars

Notes: Deviation is a measure of difference between the observed value of a variable and some other value, often that variable's mean.

Probability distribution is the mathematical function that gives the probabilities of occurrence of different possible outcomes for an experiment.

We won't be delving into statistics so don't worry.


## Line Graphs

- Displays information as a series of points connected by straight line segments
- Often used to visualise a trend in data over a time series


## Pie/Donut Chart

- Work well for showing part-to-whole relationships (how values can be split into parts)
- Clearly shows 'parts' add up to the 'whole'
- Donut charts differ slightly to pie - the central part is a convenient place to show the value of the total

Use one if:

- There are five or fewer categories
- The differences between categories are not significant
- You need to break up a page of bar graphs

## Tables

- Used to present numbers in a clear and systematic way
- Harder for viewers to see patterns in a table than a graph
- Use a table to show multiple unrelated values at once. However, if the values are related then a graph would be more appropriate

A table is better if:

- You ask the viewer to compare individual values
- You want to include summary statistics such as means or totals
- You want to include values and measures such as percentages
- There is no trend / pattern / relationship between the values


## Jupyter Notebook

- An open-source web-based interactive computational environment that allows you to create live code, equations, visualisations, explanatory text and more
- A VSCode extension is available to take advantage of Notebooks

Can be used for:

- Data viz
- Data cleaning / transformation
- Statistical modelling
- Machine Learning
- And more!


## When to Use Jupyter Notebook?

Jupyter Notebook offers unique features compared to standard Python scripts. Consider using it:

- For remote execution on servers or in Docker containers
- During presentations with real-time data analysis
- To combine code and markdown documentation
- To utilise built-in features, e.g. magic commands (`%sql`)
- For exploratory coding with line-by-line execution
- To facilitate collaboration and sharing of code/results

Choose Jupyter Notebook when it enhances your workflow and presentation.

### matplotlib

- An open-source plotting library for Python
- Provides an API for embedding plots into applications
- Widely used for creating static, animated, and interactive visualizations

To install matplotlib, run the following command in the terminal:

```
# Mac/Unix
$ python3 -m pip install matplotlib
# or on Windows
$ py -m pip install matplotlib
```

![[Pasted image 20240610104736.png]]

![[Pasted image 20240610105252.png]]