import matplotlib.pyplot as plt
import numpy as np

# Generate some data
categories = ['Category 1', 'Category 2', 'Category 3', 'Category 4', 'Category 5']
values = [100, -20, 50, -80, 70]

# Calculate the cumulative values
cum_values = np.cumsum(values)

# Create the figure and axis objects
fig, ax = plt.subplots()

# Plot the bars
bars = ax.bar(categories, values, color='grey', align='center')
bars[0].set_color('g')
bars[-1].set_color('r')

# Plot the connecting lines
for i in range(len(bars)-1):
    ax.plot([i, i+1], [cum_values[i], cum_values[i+1]], color='k')

# Set the axis labels and title
ax.set_xlabel('Categories')
ax.set_ylabel('Values')
ax.set_title('Waterfall Chart Example')

# Set the y-axis limits
ymin, ymax = ax.get_ylim()
ax.set_ylim(ymin - 10, ymax + 10)

# Save the figure to a file
plt.savefig('waterfall_chart.png', dpi=300, bbox_inches='tight')

# Show the plot
plt.show()
