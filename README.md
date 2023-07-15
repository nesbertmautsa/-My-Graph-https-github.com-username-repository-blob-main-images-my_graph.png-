import matplotlib.pyplot as plt

# Sample data
data = {'Category A': [100, -20, -30, -50], 'Category B': [80, -10, -25, -45], 'Category C': [70, -15, -20, -35]}

# Convert data to a stacked format
stacked_data = []
for i in range(len(data.keys())):
    if i == 0:
        stacked_data.append(data[list(data.keys())[i]])
    else:
        stacked_data.append([sum(x) for x in zip(stacked_data[i-1], data[list(data.keys())[i]])])

# Create the waterfall chart
fig, ax = plt.subplots(figsize=(8,6))

# Plot the bars
for i in range(len(data.keys())):
    if i == 0:
        ax.bar(list(data.keys())[i], stacked_data[i][0], color='blue')
    else:
        ax.bar(list(data.keys())[i], stacked_data[i-1][-1], color='blue', alpha=0.5)
        ax.bar(list(data.keys())[i], stacked_data[i][-1], color='red')

# Add the labels
ax.set_xticklabels([''] + list(data.keys()))
ax.set_ylabel('Value')
ax.set_title('Waterfall Chart')

plt.show()
import matplotlib.pyplot as plt

# Code for creating the waterfall chart

# Save the chart as an image file
plt.savefig('waterfall.png')
