<div align="center">

# 📊 Data Visualization Tools - Complete Guide

![Visualization](https://img.shields.io/badge/Visualization-Python-blue?style=for-the-badge&logo=python)
![Charts](https://img.shields.io/badge/Charts-Interactive-green?style=for-the-badge)
![Level](https://img.shields.io/badge/Level-All_Levels-orange?style=for-the-badge)

### _A picture is worth a thousand data points_ 📈

**Data tells stories, visualization makes them unforgettable** 🎨

</div>

---

## 📚 Table of Contents

- [🎨 Visualization Fundamentals](#-visualization-fundamentals)
- [📈 Matplotlib - Foundation](#-matplotlib---foundation)
- [🎯 Seaborn - Statistical Plots](#-seaborn---statistical-plots)
- [⚡ Plotly - Interactive Viz](#-plotly---interactive-viz)
- [🌟 Advanced Libraries](#-advanced-libraries)
- [📱 Dashboard Tools](#-dashboard-tools)
- [🎨 Design Principles](#-design-principles)
- [📊 Chart Selection Guide](#-chart-selection-guide)
- [🚀 Real-World Examples](#-real-world-examples)
- [✅ Best Practices](#-best-practices)

---

<div align="center">

## 🎨 Visualization Fundamentals

</div>

### Understanding Data Visualization 📖

```bash
# ═══════════════════════════════════════════
# WHAT IS DATA VISUALIZATION?
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   WHY VISUALIZE DATA?                      ║
╚════════════════════════════════════════════════════════════╝

Benefits of Data Visualization:
─────────────────────────────────────────────────────────────
✅ Quickly identify patterns and trends
✅ Communicate insights effectively
✅ Make data-driven decisions faster
✅ Spot outliers and anomalies
✅ Compare multiple variables
✅ Tell compelling data stories
✅ Engage non-technical audiences

The Visualization Pipeline:
─────────────────────────────────────────────────────────────

Raw Data → Clean Data → Analysis → Visualization → Insights

1. Understand Your Data
   • What type of data? (numeric, categorical, time-series)
   • What's the distribution?
   • Any missing values or outliers?

2. Define Your Message
   • What story are you telling?
   • Who is the audience?
   • What action do you want?

3. Choose the Right Chart
   • Comparison? → Bar chart
   • Distribution? → Histogram
   • Relationship? → Scatter plot
   • Trend over time? → Line chart

4. Design Effectively
   • Clear labels and titles
   • Appropriate colors
   • Minimal clutter
   • Proper scale

5. Iterate and Refine
   • Get feedback
   • Test with audience
   • Improve clarity

# ═══════════════════════════════════════════
# PYTHON VISUALIZATION ECOSYSTEM
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   LIBRARY COMPARISON                       ║
╚════════════════════════════════════════════════════════════╝
```

| Library        | Type        | Complexity | Interactive | Best For                    | Learning Curve |
| -------------- | ----------- | ---------- | ----------- | --------------------------- | -------------- |
| **Matplotlib** | Static      | ⭐⭐⭐     | ❌          | Publications, fine control  | Medium         |
| **Seaborn**    | Static      | ⭐         | ❌          | Statistical analysis        | Easy           |
| **Plotly**     | Interactive | ⭐⭐       | ✅          | Web dashboards, exploration | Medium         |
| **Bokeh**      | Interactive | ⭐⭐⭐     | ✅          | Web apps, streaming data    | Hard           |
| **Altair**     | Interactive | ⭐         | ✅          | Declarative viz             | Easy           |
| **Plotnine**   | Static      | ⭐⭐       | ❌          | Grammar of graphics         | Medium         |
| **Holoviews**  | Both        | ⭐⭐       | ✅          | Multi-dimensional data      | Medium         |

---

<div align="center">

## 📈 Matplotlib - Foundation

</div>

### The Grandfather of Python Visualization 🎨

```python
# ═══════════════════════════════════════════
# MATPLOTLIB BASICS
# ═══════════════════════════════════════════

"""
Matplotlib: The foundational plotting library
- Most flexible and powerful
- All other libraries build on it
- Can create any type of plot
- Publication-quality figures
"""

import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

# Set style
plt.style.use('seaborn-v0_8-darkgrid')

# ═══════════════════════════════════════════
# BASIC PLOTTING
# ═══════════════════════════════════════════

# Simple line plot
x = np.linspace(0, 10, 100)
y = np.sin(x)

plt.figure(figsize=(10, 6))
plt.plot(x, y)
plt.title('Sine Wave')
plt.xlabel('X axis')
plt.ylabel('Y axis')
plt.grid(True, alpha=0.3)
plt.show()

# Multiple lines
plt.figure(figsize=(12, 6))
plt.plot(x, np.sin(x), label='sin(x)', linewidth=2)
plt.plot(x, np.cos(x), label='cos(x)', linewidth=2, linestyle='--')
plt.plot(x, np.sin(x) * np.cos(x), label='sin(x) * cos(x)', linewidth=2, linestyle=':')
plt.title('Trigonometric Functions', fontsize=16, fontweight='bold')
plt.xlabel('X axis', fontsize=12)
plt.ylabel('Y axis', fontsize=12)
plt.legend(loc='upper right', fontsize=10)
plt.grid(True, alpha=0.3)
plt.tight_layout()
plt.show()

# ═══════════════════════════════════════════
# PLOT TYPES
# ═══════════════════════════════════════════

fig, axes = plt.subplots(2, 3, figsize=(18, 10))
fig.suptitle('Common Plot Types', fontsize=18, fontweight='bold')

# 1. Line Plot
axes[0, 0].plot(x, y, color='#2E86AB', linewidth=2)
axes[0, 0].set_title('Line Plot')
axes[0, 0].set_xlabel('X')
axes[0, 0].set_ylabel('Y')
axes[0, 0].grid(True, alpha=0.3)

# 2. Scatter Plot
np.random.seed(42)
x_scatter = np.random.randn(100)
y_scatter = 2 * x_scatter + np.random.randn(100)
axes[0, 1].scatter(x_scatter, y_scatter, alpha=0.6, c='#A23B72', s=50)
axes[0, 1].set_title('Scatter Plot')
axes[0, 1].set_xlabel('X')
axes[0, 1].set_ylabel('Y')
axes[0, 1].grid(True, alpha=0.3)

# 3. Bar Chart
categories = ['A', 'B', 'C', 'D', 'E']
values = [23, 45, 56, 78, 32]
axes[0, 2].bar(categories, values, color='#F18F01', alpha=0.8)
axes[0, 2].set_title('Bar Chart')
axes[0, 2].set_xlabel('Category')
axes[0, 2].set_ylabel('Value')
axes[0, 2].grid(axis='y', alpha=0.3)

# 4. Histogram
data = np.random.randn(1000)
axes[1, 0].hist(data, bins=30, color='#06A77D', alpha=0.7, edgecolor='black')
axes[1, 0].set_title('Histogram')
axes[1, 0].set_xlabel('Value')
axes[1, 0].set_ylabel('Frequency')
axes[1, 0].grid(axis='y', alpha=0.3)

# 5. Box Plot
data_box = [np.random.normal(0, std, 100) for std in range(1, 4)]
axes[1, 1].boxplot(data_box, labels=['Group 1', 'Group 2', 'Group 3'])
axes[1, 1].set_title('Box Plot')
axes[1, 1].set_xlabel('Group')
axes[1, 1].set_ylabel('Value')
axes[1, 1].grid(axis='y', alpha=0.3)

# 6. Pie Chart
sizes = [30, 25, 20, 15, 10]
colors = ['#FF6B6B', '#4ECDC4', '#45B7D1', '#FFA07A', '#98D8C8']
axes[1, 2].pie(sizes, labels=categories, autopct='%1.1f%%', colors=colors, startangle=90)
axes[1, 2].set_title('Pie Chart')

plt.tight_layout()
plt.savefig('matplotlib_plot_types.png', dpi=300, bbox_inches='tight')
plt.show()

# ═══════════════════════════════════════════
# CUSTOMIZATION
# ═══════════════════════════════════════════

# Detailed customization
fig, ax = plt.subplots(figsize=(12, 7))

# Plot data
x = np.linspace(0, 10, 100)
y1 = np.sin(x)
y2 = np.cos(x)

line1 = ax.plot(x, y1, color='#E63946', linewidth=2.5,
                label='sin(x)', marker='o', markersize=4,
                markevery=10, alpha=0.8)

line2 = ax.plot(x, y2, color='#457B9D', linewidth=2.5,
                label='cos(x)', marker='s', markersize=4,
                markevery=10, alpha=0.8, linestyle='--')

# Titles and labels
ax.set_title('Customized Plot', fontsize=18, fontweight='bold', pad=20)
ax.set_xlabel('X Axis', fontsize=14, fontweight='bold')
ax.set_ylabel('Y Axis', fontsize=14, fontweight='bold')

# Grid
ax.grid(True, linestyle='--', alpha=0.3, linewidth=0.8)

# Legend
ax.legend(loc='upper right', fontsize=12, frameon=True,
          shadow=True, fancybox=True)

# Spine customization
ax.spines['top'].set_visible(False)
ax.spines['right'].set_visible(False)
ax.spines['left'].set_linewidth(1.5)
ax.spines['bottom'].set_linewidth(1.5)

# Tick customization
ax.tick_params(axis='both', which='major', labelsize=11,
               length=6, width=1.5)

# Set limits
ax.set_xlim(0, 10)
ax.set_ylim(-1.5, 1.5)

# Add annotations
ax.annotate('Maximum', xy=(np.pi/2, 1), xytext=(np.pi/2 + 1, 1.3),
            arrowprops=dict(facecolor='red', shrink=0.05, width=2),
            fontsize=12, fontweight='bold')

# Add horizontal/vertical lines
ax.axhline(y=0, color='black', linestyle='-', linewidth=0.8, alpha=0.5)
ax.axvline(x=np.pi, color='green', linestyle=':', linewidth=1.5, alpha=0.5)

# Add text
ax.text(8, -1.2, 'Custom Text', fontsize=12,
        bbox=dict(boxstyle='round', facecolor='wheat', alpha=0.5))

plt.tight_layout()
plt.show()

# ═══════════════════════════════════════════
# SUBPLOTS & LAYOUTS
# ═══════════════════════════════════════════

# Method 1: plt.subplots
fig, axes = plt.subplots(2, 2, figsize=(14, 10))

axes[0, 0].plot(x, y)
axes[0, 0].set_title('Plot 1')

axes[0, 1].scatter(x_scatter, y_scatter)
axes[0, 1].set_title('Plot 2')

axes[1, 0].bar(categories, values)
axes[1, 0].set_title('Plot 3')

axes[1, 1].hist(data, bins=30)
axes[1, 1].set_title('Plot 4')

plt.tight_layout()
plt.show()

# Method 2: GridSpec (more control)
import matplotlib.gridspec as gridspec

fig = plt.figure(figsize=(15, 10))
gs = gridspec.GridSpec(3, 3, figure=fig, hspace=0.3, wspace=0.3)

# Large plot spanning multiple cells
ax1 = fig.add_subplot(gs[0:2, 0:2])
ax1.plot(x, y)
ax1.set_title('Large Plot', fontsize=14, fontweight='bold')

# Smaller plots
ax2 = fig.add_subplot(gs[0, 2])
ax2.scatter(x_scatter[:50], y_scatter[:50], alpha=0.5)
ax2.set_title('Top Right')

ax3 = fig.add_subplot(gs[1, 2])
ax3.bar(categories, values)
ax3.set_title('Middle Right')

ax4 = fig.add_subplot(gs[2, :])
ax4.hist(data, bins=50, alpha=0.7)
ax4.set_title('Bottom Spanning')

plt.show()

# ═══════════════════════════════════════════
# COLORMAPS & COLORS
# ═══════════════════════════════════════════

# Create data for colormap example
x = np.linspace(-5, 5, 100)
y = np.linspace(-5, 5, 100)
X, Y = np.meshgrid(x, y)
Z = np.sin(np.sqrt(X**2 + Y**2))

fig, axes = plt.subplots(2, 3, figsize=(18, 10))

colormaps = ['viridis', 'plasma', 'inferno', 'magma', 'cividis', 'coolwarm']

for ax, cmap in zip(axes.flat, colormaps):
    im = ax.contourf(X, Y, Z, levels=20, cmap=cmap)
    ax.set_title(f'Colormap: {cmap}', fontsize=12, fontweight='bold')
    plt.colorbar(im, ax=ax)

plt.tight_layout()
plt.show()

# Custom colors
custom_colors = ['#FF6B6B', '#4ECDC4', '#45B7D1', '#FFA07A', '#98D8C8']

plt.figure(figsize=(10, 6))
for i, color in enumerate(custom_colors):
    plt.plot(x, y + i, color=color, linewidth=3, label=f'Line {i+1}')

plt.title('Custom Color Palette', fontsize=16, fontweight='bold')
plt.legend()
plt.grid(True, alpha=0.3)
plt.show()

# ═══════════════════════════════════════════
# 3D PLOTTING
# ═══════════════════════════════════════════

from mpl_toolkits.mplot3d import Axes3D

fig = plt.figure(figsize=(15, 5))

# 3D Surface plot
ax1 = fig.add_subplot(131, projection='3d')
ax1.plot_surface(X, Y, Z, cmap='viridis', alpha=0.9)
ax1.set_title('3D Surface', fontsize=14, fontweight='bold')
ax1.set_xlabel('X')
ax1.set_ylabel('Y')
ax1.set_zlabel('Z')

# 3D Scatter plot
ax2 = fig.add_subplot(132, projection='3d')
n = 100
xs = np.random.randn(n)
ys = np.random.randn(n)
zs = np.random.randn(n)
colors = np.random.rand(n)
ax2.scatter(xs, ys, zs, c=colors, cmap='rainbow', s=50, alpha=0.6)
ax2.set_title('3D Scatter', fontsize=14, fontweight='bold')
ax2.set_xlabel('X')
ax2.set_ylabel('Y')
ax2.set_zlabel('Z')

# 3D Line plot
ax3 = fig.add_subplot(133, projection='3d')
theta = np.linspace(-4 * np.pi, 4 * np.pi, 100)
z = np.linspace(-2, 2, 100)
r = z**2 + 1
x = r * np.sin(theta)
y = r * np.cos(theta)
ax3.plot(x, y, z, label='Spiral', linewidth=2)
ax3.set_title('3D Spiral', fontsize=14, fontweight='bold')
ax3.legend()

plt.tight_layout()
plt.show()

# ═══════════════════════════════════════════
# ANIMATIONS
# ═══════════════════════════════════════════

from matplotlib.animation import FuncAnimation

# Create animated sine wave
fig, ax = plt.subplots(figsize=(10, 6))
xdata, ydata = [], []
ln, = ax.plot([], [], 'r-', linewidth=2)

def init():
    ax.set_xlim(0, 2*np.pi)
    ax.set_ylim(-1.5, 1.5)
    ax.set_title('Animated Sine Wave', fontsize=16, fontweight='bold')
    ax.grid(True, alpha=0.3)
    return ln,

def update(frame):
    xdata.append(frame)
    ydata.append(np.sin(frame))
    ln.set_data(xdata, ydata)
    return ln,

ani = FuncAnimation(fig, update, frames=np.linspace(0, 2*np.pi, 128),
                    init_func=init, blit=True, interval=50)

# Save animation
# ani.save('sine_wave.gif', writer='pillow', fps=30)

plt.show()

# ═══════════════════════════════════════════
# SAVING FIGURES
# ═══════════════════════════════════════════

fig, ax = plt.subplots(figsize=(10, 6))
ax.plot(x, y)
ax.set_title('Sample Plot')

# Save in different formats
plt.savefig('plot.png', dpi=300, bbox_inches='tight')
plt.savefig('plot.pdf', dpi=300, bbox_inches='tight')
plt.savefig('plot.svg', dpi=300, bbox_inches='tight')
plt.savefig('plot.jpg', dpi=300, bbox_inches='tight', quality=95)

# Transparent background
plt.savefig('plot_transparent.png', dpi=300, bbox_inches='tight',
            transparent=True)

# High resolution for publication
plt.savefig('plot_publication.png', dpi=600, bbox_inches='tight')

plt.close()
```

---

<div align="center">

## 🎯 Seaborn - Statistical Plots

</div>

### Beautiful Statistical Visualizations Made Easy 📊

```python
# ═══════════════════════════════════════════
# SEABORN BASICS
# ═══════════════════════════════════════════

"""
Seaborn: High-level statistical visualization
- Built on top of Matplotlib
- Beautiful default styles
- Statistical functions built-in
- Great for data exploration
"""

import seaborn as sns
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

# Set style
sns.set_style("whitegrid")
sns.set_palette("husl")

# Load sample dataset
tips = sns.load_dataset('tips')
iris = sns.load_dataset('iris')
flights = sns.load_dataset('flights')
titanic = sns.load_dataset('titanic')

print("Tips dataset shape:", tips.shape)
print(tips.head())

# ═══════════════════════════════════════════
# DISTRIBUTION PLOTS
# ═══════════════════════════════════════════

fig, axes = plt.subplots(2, 3, figsize=(18, 10))
fig.suptitle('Seaborn Distribution Plots', fontsize=18, fontweight='bold')

# 1. Histogram with KDE
sns.histplot(data=tips, x='total_bill', kde=True, ax=axes[0, 0])
axes[0, 0].set_title('Histogram with KDE')

# 2. KDE Plot
sns.kdeplot(data=tips, x='total_bill', fill=True, ax=axes[0, 1])
axes[0, 1].set_title('KDE Plot')

# 3. ECDF Plot (Empirical Cumulative Distribution)
sns.ecdfplot(data=tips, x='total_bill', ax=axes[0, 2])
axes[0, 2].set_title('ECDF Plot')

# 4. Distribution with Rug plot
sns.histplot(data=tips, x='total_bill', kde=True, ax=axes[1, 0])
sns.rugplot(data=tips, x='total_bill', ax=axes[1, 0], color='red', alpha=0.5)
axes[1, 0].set_title('Histogram + Rug Plot')

# 5. Multiple distributions
sns.histplot(data=tips, x='total_bill', hue='time', multiple='dodge', ax=axes[1, 1])
axes[1, 1].set_title('Multiple Distributions')

# 6. 2D KDE
sns.kdeplot(data=tips, x='total_bill', y='tip', fill=True, cmap='viridis', ax=axes[1, 2])
axes[1, 2].set_title('2D KDE Plot')

plt.tight_layout()
plt.show()

# ═══════════════════════════════════════════
# CATEGORICAL PLOTS
# ═══════════════════════════════════════════

fig, axes = plt.subplots(2, 3, figsize=(18, 10))
fig.suptitle('Seaborn Categorical Plots', fontsize=18, fontweight='bold')

# 1. Count Plot
sns.countplot(data=tips, x='day', ax=axes[0, 0])
axes[0, 0].set_title('Count Plot')
axes[0, 0].tick_params(axis='x', rotation=45)

# 2. Bar Plot (with aggregation)
sns.barplot(data=tips, x='day', y='total_bill', estimator=np.mean, ax=axes[0, 1])
axes[0, 1].set_title('Bar Plot (Mean)')
axes[0, 1].tick_params(axis='x', rotation=45)

# 3. Box Plot
sns.boxplot(data=tips, x='day', y='total_bill', ax=axes[0, 2])
axes[0, 2].set_title('Box Plot')
axes[0, 2].tick_params(axis='x', rotation=45)

# 4. Violin Plot
sns.violinplot(data=tips, x='day', y='total_bill', ax=axes[1, 0])
axes[1, 0].set_title('Violin Plot')
axes[1, 0].tick_params(axis='x', rotation=45)

# 5. Strip Plot
sns.stripplot(data=tips, x='day', y='total_bill', ax=axes[1, 1])
axes[1, 1].set_title('Strip Plot')
axes[1, 1].tick_params(axis='x', rotation=45)

# 6. Swarm Plot
sns.swarmplot(data=tips, x='day', y='total_bill', ax=axes[1, 2])
axes[1, 2].set_title('Swarm Plot')
axes[1, 2].tick_params(axis='x', rotation=45)

plt.tight_layout()
plt.show()

# ═══════════════════════════════════════════
# RELATIONSHIP PLOTS
# ═══════════════════════════════════════════

fig, axes = plt.subplots(2, 2, figsize=(14, 10))
fig.suptitle('Seaborn Relationship Plots', fontsize=18, fontweight='bold')

# 1. Scatter Plot
sns.scatterplot(data=tips, x='total_bill', y='tip', hue='time',
                size='size', sizes=(50, 200), ax=axes[0, 0])
axes[0, 0].set_title('Scatter Plot')

# 2. Regression Plot
sns.regplot(data=tips, x='total_bill', y='tip', ax=axes[0, 1])
axes[0, 1].set_title('Regression Plot')

# 3. Residual Plot
sns.residplot(data=tips, x='total_bill', y='tip', ax=axes[1, 0])
axes[1, 0].set_title('Residual Plot')

# 4. Joint Plot (create separately)
axes[1, 1].text(0.5, 0.5, 'See joint plot below',
                ha='center', va='center', fontsize=14)
axes[1, 1].axis('off')

plt.tight_layout()
plt.show()

# Joint plot (separate figure)
g = sns.jointplot(data=tips, x='total_bill', y='tip', kind='reg', height=8)
g.fig.suptitle('Joint Plot with Regression', y=1.02, fontsize=16, fontweight='bold')
plt.show()

# ═══════════════════════════════════════════
# MATRIX PLOTS
# ═══════════════════════════════════════════

# Correlation heatmap
plt.figure(figsize=(10, 8))
correlation = tips.select_dtypes(include=[np.number]).corr()
sns.heatmap(correlation, annot=True, cmap='coolwarm', center=0,
            square=True, linewidths=1, cbar_kws={"shrink": 0.8})
plt.title('Correlation Heatmap', fontsize=16, fontweight='bold', pad=20)
plt.tight_layout()
plt.show()

# Pivot table heatmap
flights_pivot = flights.pivot(index='month', columns='year', values='passengers')
plt.figure(figsize=(12, 8))
sns.heatmap(flights_pivot, annot=True, fmt='d', cmap='YlGnBu',
            linewidths=0.5, cbar_kws={"shrink": 0.8})
plt.title('Flights Passengers by Month and Year', fontsize=16, fontweight='bold', pad=20)
plt.tight_layout()
plt.show()

# Clustermap
g = sns.clustermap(correlation, cmap='coolwarm', center=0,
                   annot=True, figsize=(10, 10))
g.fig.suptitle('Clustered Correlation Heatmap', y=1.02, fontsize=16, fontweight='bold')
plt.show()

# ═══════════════════════════════════════════
# PAIRPLOT
# ═══════════════════════════════════════════

# Pairplot for exploring relationships
g = sns.pairplot(iris, hue='species', height=2.5, aspect=1.2,
                 diag_kind='kde', corner=True, palette='Set2')
g.fig.suptitle('Iris Dataset Pairplot', y=1.02, fontsize=16, fontweight='bold')
plt.show()

# Custom pairplot
g = sns.pairplot(tips, vars=['total_bill', 'tip', 'size'],
                 hue='time', kind='reg', height=3)
g.fig.suptitle('Tips Dataset Pairplot', y=1.02, fontsize=16, fontweight='bold')
plt.show()

# ═══════════════════════════════════════════
# FACET GRIDS
# ═══════════════════════════════════════════

# FacetGrid for small multiples
g = sns.FacetGrid(tips, col='time', row='sex', hue='smoker', height=4, aspect=1.2)
g.map(sns.scatterplot, 'total_bill', 'tip', alpha=0.7)
g.add_legend()
g.fig.suptitle('Facet Grid: Tips Analysis', y=1.02, fontsize=16, fontweight='bold')
plt.show()

# ═══════════════════════════════════════════
# RELPLOT & CATPLOT (HIGH-LEVEL INTERFACES)
# ═══════════════════════════════════════════

# relplot - relationship plots
g = sns.relplot(data=tips, x='total_bill', y='tip',
                hue='time', size='size', col='sex', row='smoker',
                kind='scatter', height=3, aspect=1.2)
g.fig.suptitle('Relplot: Multi-dimensional Analysis', y=1.02, fontsize=16, fontweight='bold')
plt.show()

# catplot - categorical plots
g = sns.catplot(data=tips, x='day', y='total_bill',
                hue='sex', col='time', kind='box',
                height=4, aspect=1.2)
g.fig.suptitle('Catplot: Categorical Analysis', y=1.02, fontsize=16, fontweight='bold')
plt.show()

# ═══════════════════════════════════════════
# STYLING & THEMES
# ═══════════════════════════════════════════

# Available styles
styles = ['darkgrid', 'whitegrid', 'dark', 'white', 'ticks']

fig, axes = plt.subplots(2, 3, figsize=(18, 10))
fig.suptitle('Seaborn Styles', fontsize=18, fontweight='bold')

for ax, style in zip(axes.flat[:5], styles):
    sns.set_style(style)
    sns.scatterplot(data=tips, x='total_bill', y='tip', ax=ax)
    ax.set_title(f'Style: {style}')

# Color palettes
axes.flat[5].axis('off')

plt.tight_layout()
plt.show()

# Reset to default
sns.set_style("whitegrid")

# Color palettes
fig, axes = plt.subplots(2, 3, figsize=(18, 10))
fig.suptitle('Seaborn Color Palettes', fontsize=18, fontweight='bold')

palettes = ['deep', 'muted', 'bright', 'pastel', 'dark', 'colorblind']

for ax, palette in zip(axes.flat, palettes):
    sns.set_palette(palette)
    sns.barplot(data=tips, x='day', y='total_bill', ax=ax)
    ax.set_title(f'Palette: {palette}')
    ax.tick_params(axis='x', rotation=45)

plt.tight_layout()
plt.show()

# Custom color palette
custom_palette = ['#FF6B6B', '#4ECDC4', '#45B7D1', '#FFA07A']
sns.set_palette(custom_palette)

plt.figure(figsize=(10, 6))
sns.barplot(data=tips, x='day', y='total_bill', hue='sex')
plt.title('Custom Color Palette', fontsize=16, fontweight='bold')
plt.show()

# ═══════════════════════════════════════════
# ADVANCED: COMBINING SEABORN & MATPLOTLIB
# ═══════════════════════════════════════════

# Create complex visualizations
fig, axes = plt.subplots(2, 2, figsize=(14, 10))
fig.suptitle('Combined Seaborn & Matplotlib', fontsize=18, fontweight='bold')

# Plot 1: Seaborn plot with Matplotlib customization
sns.violinplot(data=tips, x='day', y='total_bill', ax=axes[0, 0])
axes[0, 0].set_title('Violin Plot', fontsize=14, fontweight='bold')
axes[0, 0].axhline(y=tips['total_bill'].mean(), color='red',
                   linestyle='--', label='Mean')
axes[0, 0].legend()

# Plot 2: Multiple Seaborn layers
sns.boxplot(data=tips, x='day', y='total_bill', ax=axes[0, 1])
sns.stripplot(data=tips, x='day', y='total_bill',
              color='black', alpha=0.3, size=3, ax=axes[0, 1])
axes[0, 1].set_title('Box + Strip Plot', fontsize=14, fontweight='bold')

# Plot 3: Seaborn with annotations
sns.scatterplot(data=tips, x='total_bill', y='tip',
                hue='time', size='size', ax=axes[1, 0])
axes[1, 0].set_title('Scatter with Annotations', fontsize=14, fontweight='bold')

# Add annotation to highest tip
max_tip_idx = tips['tip'].idxmax()
max_tip_row = tips.loc[max_tip_idx]
axes[1, 0].annotate(f'Max tip: ${max_tip_row["tip"]:.2f}',
                    xy=(max_tip_row['total_bill'], max_tip_row['tip']),
                    xytext=(max_tip_row['total_bill'] + 5, max_tip_row['tip'] + 1),
                    arrowprops=dict(facecolor='red', shrink=0.05),
                    fontsize=10, fontweight='bold')

# Plot 4: Regression with confidence interval
sns.regplot(data=tips, x='total_bill', y='tip', ax=axes[1, 1])
axes[1, 1].set_title('Regression with CI', fontsize=14, fontweight='bold')

# Calculate and display R²
from scipy import stats
slope, intercept, r_value, p_value, std_err = stats.linregress(
    tips['total_bill'], tips['tip']
)
axes[1, 1].text(0.05, 0.95, f'R² = {r_value**2:.3f}',
                transform=axes[1, 1].transAxes,
                verticalalignment='top',
                bbox=dict(boxstyle='round', facecolor='wheat', alpha=0.5))

plt.tight_layout()
plt.show()
```

---

<div align="center">

## ⚡ Plotly - Interactive Viz

</div>

### Creating Interactive Visualizations 🖱️

```python
# ═══════════════════════════════════════════
# PLOTLY BASICS
# ═══════════════════════════════════════════

"""
Plotly: Interactive, publication-quality graphs
- Hover tooltips
- Zoom, pan, export
- Animations
- 3D plots
- Web-ready
"""

import plotly.express as px
import plotly.graph_objects as go
from plotly.subplots import make_subplots
import pandas as pd
import numpy as np

# Load sample data
df = px.data.gapminder()
iris = px.data.iris()
tips = px.data.tips()

# ═══════════════════════════════════════════
# PLOTLY EXPRESS (HIGH-LEVEL API)
# ═══════════════════════════════════════════

# 1. Scatter Plot
fig = px.scatter(df, x='gdpPercap', y='lifeExp',
                 color='continent', size='pop',
                 hover_name='country',
                 log_x=True, size_max=60,
                 title='Life Expectancy vs GDP per Capita')
fig.update_layout(height=600)
# fig.show()

# 2. Line Plot with Animation
fig = px.line(df, x='year', y='lifeExp',
              color='continent',
              title='Life Expectancy Over Time')
# fig.show()

# 3. Animated Scatter Plot
fig = px.scatter(df, x='gdpPercap', y='lifeExp',
                 animation_frame='year',
                 animation_group='country',
                 size='pop', color='continent',
                 hover_name='country',
                 log_x=True, size_max=55,
                 range_x=[100, 100000], range_y=[25, 90],
                 title='Animated GDP vs Life Expectancy')
# fig.show()

# 4. Bar Chart
df_2007 = df[df['year'] == 2007].nlargest(10, 'pop')
fig = px.bar(df_2007, x='country', y='pop',
             color='continent',
             title='Top 10 Countries by Population (2007)')
fig.update_xaxis(tickangle=-45)
# fig.show()

# 5. Box Plot
fig = px.box(tips, x='day', y='total_bill', color='sex',
             title='Total Bill Distribution by Day and Gender')
# fig.show()

# 6. Violin Plot
fig = px.violin(tips, x='day', y='total_bill', color='sex',
                box=True, points='all',
                title='Violin Plot: Total Bill by Day')
# fig.show()

# 7. Histogram
fig = px.histogram(tips, x='total_bill', nbins=30,
                   marginal='box',  # or 'violin', 'rug'
                   title='Total Bill Distribution')
# fig.show()

# 8. Scatter Matrix (Pairplot)
fig = px.scatter_matrix(iris,
                        dimensions=['sepal_width', 'sepal_length',
                                   'petal_width', 'petal_length'],
                        color='species',
                        title='Iris Dataset - Scatter Matrix')
# fig.show()

# 9. Parallel Coordinates
fig = px.parallel_coordinates(iris,
                              dimensions=['sepal_width', 'sepal_length',
                                        'petal_width', 'petal_length'],
                              color='species_id',
                              title='Parallel Coordinates Plot')
# fig.show()

# 10. Sunburst Chart
fig = px.sunburst(df, path=['continent', 'country'],
                  values='pop',
                  color='lifeExp',
                  hover_data=['iso_alpha'],
                  title='World Population by Continent and Country')
# fig.show()

# ═══════════════════════════════════════════
# GEOGRAPHIC VISUALIZATIONS
# ═══════════════════════════════════════════

# 1. Choropleth Map
fig = px.choropleth(df, locations='iso_alpha',
                    color='lifeExp',
                    hover_name='country',
                    animation_frame='year',
                    color_continuous_scale=px.colors.sequential.Plasma,
                    title='Life Expectancy Around the World')
# fig.show()

# 2. Scatter Geo
df_2007 = df[df['year'] == 2007]
fig = px.scatter_geo(df_2007, locations='iso_alpha',
                     color='continent', size='pop',
                     hover_name='country',
                     projection='natural earth',
                     title='World Countries by Population (2007)')
# fig.show()

# 3. Line Geo (Flight Paths)
# Example with custom data
flight_paths = pd.DataFrame({
    'start_lat': [40.7128, 51.5074, 35.6762],
    'start_lon': [-74.0060, -0.1278, 139.6503],
    'end_lat': [51.5074, 35.6762, 40.7128],
    'end_lon': [-0.1278, 139.6503, -74.0060],
    'city': ['NYC-London', 'London-Tokyo', 'Tokyo-NYC']
})

fig = go.Figure()

for i, row in flight_paths.iterrows():
    fig.add_trace(go.Scattergeo(
        lon=[row['start_lon'], row['end_lon']],
        lat=[row['start_lat'], row['end_lat']],
        mode='lines',
        line=dict(width=2, color='red'),
        name=row['city']
    ))

fig.update_layout(
    title='Flight Paths',
    geo=dict(
        projection_type='orthographic',
        showland=True,
        landcolor='rgb(243, 243, 243)',
        coastlinecolor='rgb(204, 204, 204)',
    ),
    height=600
)
# fig.show()

# ═══════════════════════════════════════════
# PLOTLY GRAPH OBJECTS (LOW-LEVEL API)
# ═══════════════════════════════════════════

# More control over plots
x = np.linspace(0, 10, 100)
y1 = np.sin(x)
y2 = np.cos(x)

fig = go.Figure()

# Add traces
fig.add_trace(go.Scatter(x=x, y=y1,
                         mode='lines',
                         name='sin(x)',
                         line=dict(color='blue', width=2)))

fig.add_trace(go.Scatter(x=x, y=y2,
                         mode='lines',
                         name='cos(x)',
                         line=dict(color='red', width=2, dash='dash')))

# Update layout
fig.update_layout(
    title='Trigonometric Functions',
    xaxis_title='X axis',
    yaxis_title='Y axis',
    hovermode='x unified',
    template='plotly_white',
    height=600
)

# fig.show()

# ═══════════════════════════════════════════
# SUBPLOTS
# ═══════════════════════════════════════════

# Create subplots
fig = make_subplots(
    rows=2, cols=2,
    subplot_titles=('Scatter', 'Bar', 'Line', 'Box'),
    specs=[[{'type': 'scatter'}, {'type': 'bar'}],
           [{'type': 'scatter'}, {'type': 'box'}]]
)

# Add traces to subplots
fig.add_trace(
    go.Scatter(x=[1, 2, 3], y=[4, 5, 6], name='Scatter'),
    row=1, col=1
)

fig.add_trace(
    go.Bar(x=['A', 'B', 'C'], y=[10, 20, 15], name='Bar'),
    row=1, col=2
)

fig.add_trace(
    go.Scatter(x=[1, 2, 3], y=[2, 4, 6], mode='lines+markers', name='Line'),
    row=2, col=1
)

fig.add_trace(
    go.Box(y=[1, 2, 3, 4, 5, 6, 7, 8, 9], name='Box'),
    row=2, col=2
)

fig.update_layout(height=700, showlegend=True,
                  title_text='Plotly Subplots Example')
# fig.show()

# ═══════════════════════════════════════════
# 3D VISUALIZATIONS
# ═══════════════════════════════════════════

# 3D Scatter
fig = px.scatter_3d(iris, x='sepal_length', y='sepal_width', z='petal_width',
                    color='species', size='petal_length',
                    title='Iris Dataset - 3D Visualization')
# fig.show()

# 3D Surface
x = np.linspace(-5, 5, 50)
y = np.linspace(-5, 5, 50)
X, Y = np.meshgrid(x, y)
Z = np.sin(np.sqrt(X**2 + Y**2))

fig = go.Figure(data=[go.Surface(z=Z, x=X, y=Y, colorscale='Viridis')])
fig.update_layout(
    title='3D Surface Plot',
    scene=dict(
        xaxis_title='X',
        yaxis_title='Y',
        zaxis_title='Z',
    ),
    height=600
)
# fig.show()

# ═══════════════════════════════════════════
# ADVANCED FEATURES
# ═══════════════════════════════════════════

# 1. Dropdown Buttons
fig = go.Figure()

# Add traces
fig.add_trace(go.Scatter(x=x, y=np.sin(x), name='sin(x)'))
fig.add_trace(go.Scatter(x=x, y=np.cos(x), name='cos(x)', visible=False))
fig.add_trace(go.Scatter(x=x, y=np.tan(x), name='tan(x)', visible=False))

# Add dropdown
fig.update_layout(
    updatemenus=[
        dict(
            buttons=list([
                dict(label='sin(x)',
                     method='update',
                     args=[{'visible': [True, False, False]},
                           {'title': 'Sine Wave'}]),
                dict(label='cos(x)',
                     method='update',
                     args=[{'visible': [False, True, False]},
                           {'title': 'Cosine Wave'}]),
                dict(label='tan(x)',
                     method='update',
                     args=[{'visible': [False, False, True]},
                           {'title': 'Tangent Wave'}]),
                dict(label='All',
                     method='update',
                     args=[{'visible': [True, True, True]},
                           {'title': 'All Functions'}]),
            ]),
            direction='down',
            showactive=True,
        )
    ],
    title='Interactive Dropdown'
)
# fig.show()

# 2. Slider
fig = px.scatter(df, x='gdpPercap', y='lifeExp',
                 animation_frame='year',
                 size='pop', color='continent',
                 hover_name='country',
                 log_x=True, size_max=60,
                 range_x=[100, 100000], range_y=[25, 90])

fig.update_layout(
    title='GDP vs Life Expectancy with Slider',
    xaxis_title='GDP per Capita',
    yaxis_title='Life Expectancy'
)
# fig.show()

# 3. Custom Hover Information
fig = px.scatter(tips, x='total_bill', y='tip',
                 color='sex', size='size')

fig.update_traces(
    hovertemplate='<b>Total Bill</b>: $%{x:.2f}<br>' +
                  '<b>Tip</b>: $%{y:.2f}<br>' +
                  '<extra></extra>'
)

fig.update_layout(title='Custom Hover Information')
# fig.show()

# ═══════════════════════════════════════════
# THEMES & STYLING
# ═══════════════════════════════════════════

# Available templates
templates = ['plotly', 'plotly_white', 'plotly_dark', 'ggplot2',
             'seaborn', 'simple_white', 'none']

# Example with different templates
fig = px.scatter(iris, x='sepal_width', y='sepal_length',
                 color='species',
                 title='Different Templates',
                 template='plotly_dark')  # Try different templates
# fig.show()

# Custom theme
custom_template = dict(
    layout=dict(
        font=dict(family='Arial', size=14),
        title=dict(font=dict(size=20, color='#2C3E50')),
        plot_bgcolor='#ECF0F1',
        paper_bgcolor='#FFFFFF',
    )
)

fig = px.scatter(tips, x='total_bill', y='tip', template=custom_template)
fig.update_layout(title='Custom Theme')
# fig.show()

# ═══════════════════════════════════════════
# EXPORTING
# ═══════════════════════════════════════════

# Save as HTML (interactive)
# fig.write_html('plot.html')

# Save as static image (requires kaleido)
# pip install kaleido
# fig.write_image('plot.png', width=1200, height=800)
# fig.write_image('plot.pdf')
# fig.write_image('plot.svg')

print("Plotly visualizations created!")
```

---

<div align="center">

## 🌟 Advanced Libraries

</div>

### Specialized Visualization Tools 🛠️

```python
# ═══════════════════════════════════════════
# ALTAIR - DECLARATIVE VISUALIZATION
# ═══════════════════════════════════════════

"""
Altair: Declarative statistical visualization
- Grammar of graphics
- Concise syntax
- Interactive by default
- Built on Vega-Lite
"""

import altair as alt
import pandas as pd

# Enable Altair for large datasets
alt.data_transformers.enable('default', max_rows=None)

# Sample data
cars = pd.read_json('https://cdn.jsdelivr.net/npm/vega-datasets@v1.29.0/data/cars.json')

# Basic scatter plot
chart = alt.Chart(cars).mark_point().encode(
    x='Horsepower',
    y='Miles_per_Gallon',
    color='Origin',
    size='Acceleration',
    tooltip=['Name', 'Horsepower', 'Miles_per_Gallon']
).properties(
    width=600,
    height=400,
    title='Cars Dataset'
).interactive()

# chart.show()

# Layered chart
base = alt.Chart(cars).encode(
    x='Horsepower:Q',
    y='Miles_per_Gallon:Q'
)

points = base.mark_point().encode(
    color='Origin:N',
    tooltip=['Name', 'Origin']
)

line = base.mark_line(color='red').transform_regression(
    'Horsepower', 'Miles_per_Gallon'
)

layered = (points + line).properties(
    width=600,
    height=400,
    title='Cars with Regression Line'
).interactive()

# layered.show()

# Faceted chart
faceted = alt.Chart(cars).mark_point().encode(
    x='Horsepower',
    y='Miles_per_Gallon',
    color='Origin'
).properties(
    width=250,
    height=250
).facet(
    column='Origin'
).resolve_scale(
    y='independent'
)

# faceted.show()

# Interactive selection
brush = alt.selection_interval()

points = alt.Chart(cars).mark_point().encode(
    x='Horsepower',
    y='Miles_per_Gallon',
    color=alt.condition(brush, 'Origin', alt.value('lightgray')),
    tooltip=['Name', 'Horsepower', 'Miles_per_Gallon']
).add_selection(
    brush
).properties(
    width=600,
    height=400,
    title='Interactive Selection (Click and Drag)'
)

# points.show()

# ═══════════════════════════════════════════
# BOKEH - INTERACTIVE WEB PLOTTING
# ═══════════════════════════════════════════

"""
Bokeh: Interactive visualization for web browsers
- Interactive widgets
- Streaming data
- Server-side rendering
- Large datasets
"""

from bokeh.plotting import figure, show, output_file
from bokeh.layouts import row, column
from bokeh.models import HoverTool, ColumnDataSource
from bokeh.palettes import Category20_20
import numpy as np

# Basic plot
p = figure(title='Bokeh Line Plot', width=800, height=400)
x = np.linspace(0, 4*np.pi, 100)
y = np.sin(x)
p.line(x, y, line_width=2, color='navy', alpha=0.8)
p.circle(x[::5], y[::5], size=8, color='red', alpha=0.5)

# output_file('bokeh_plot.html')
# show(p)

# Interactive hover
source = ColumnDataSource(data=dict(
    x=[1, 2, 3, 4, 5],
    y=[6, 7, 2, 4, 5],
    desc=['A', 'B', 'C', 'D', 'E']
))

hover = HoverTool(tooltips=[
    ('Index', '$index'),
    ('(X,Y)', '($x, $y)'),
    ('Desc', '@desc')
])

p = figure(title='Bokeh with Hover', width=600, height=400, tools=[hover])
p.circle('x', 'y', size=15, source=source)

# output_file('bokeh_hover.html')
# show(p)

# Multiple plots
p1 = figure(title='Plot 1', width=400, height=300)
p1.line([1, 2, 3, 4, 5], [6, 7, 2, 4, 5])

p2 = figure(title='Plot 2', width=400, height=300)
p2.circle([1, 2, 3, 4, 5], [2, 5, 8, 2, 7], size=10)

layout = row(p1, p2)
# output_file('bokeh_layout.html')
# show(layout)

# ═══════════════════════════════════════════
# PLOTNINE - GRAMMAR OF GRAPHICS
# ═══════════════════════════════════════════

"""
Plotnine: Grammar of graphics (ggplot2 for Python)
- Declarative syntax
- Layer-based approach
- Consistent API
- Similar to R's ggplot2
"""

from plotnine import ggplot, aes, geom_point, geom_line, theme_minimal, labs
import pandas as pd

# Create sample data
df = pd.DataFrame({
    'x': range(10),
    'y': [i**2 for i in range(10)],
    'category': ['A', 'B'] * 5
})

# Basic plot
plot = (
    ggplot(df, aes(x='x', y='y', color='category')) +
    geom_point(size=3) +
    geom_line() +
    labs(title='Plotnine Example', x='X axis', y='Y axis') +
    theme_minimal()
)

# plot.save('plotnine_plot.png', dpi=300)

# ═══════════════════════════════════════════
# HOLOVIEWS - DECLARATIVE VISUALIZATION
# ═══════════════════════════════════════════

"""
HoloViews: Declarative data structures
- Automatic visualization
- Interactive exploration
- Works with many backends
- Great for large datasets
"""

import holoviews as hv
from holoviews import opts
hv.extension('bokeh')

# Create data
x = np.linspace(0, 4*np.pi, 100)
y = np.sin(x)

# Create curve
curve = hv.Curve((x, y), 'x', 'sin(x)')
curve.opts(width=600, height=400, tools=['hover'], color='red', line_width=2)

# curve

# Multiple elements
points = hv.Points((x[::5], y[::5]))
layout = (curve * points).opts(
    opts.Curve(color='blue', line_width=2),
    opts.Points(color='red', size=8, tools=['hover'])
)

# layout

print("Advanced libraries examples created!")
```

---

<div align="center">

## 📱 Dashboard Tools

</div>

### Building Interactive Dashboards 🎛️

```python
# ═══════════════════════════════════════════
# STREAMLIT - FASTEST WAY TO BUILD DASHBOARDS
# ═══════════════════════════════════════════

"""
Streamlit: Turn data scripts into shareable web apps
- Pure Python
- No HTML/CSS/JavaScript needed
- Real-time updates
- Easy deployment
"""

# Create file: dashboard.py
"""
import streamlit as st
import pandas as pd
import numpy as np
import plotly.express as px

# Page config
st.set_page_config(
    page_title="Sales Dashboard",
    page_icon="📊",
    layout="wide"
)

# Title
st.title("📊 Sales Analytics Dashboard")

# Sidebar
st.sidebar.header("Filters")
date_range = st.sidebar.date_input("Date Range", [])
category = st.sidebar.selectbox("Category", ["All", "Electronics", "Clothing", "Food"])

# Generate sample data
@st.cache_data
def load_data():
    dates = pd.date_range('2024-01-01', periods=100)
    df = pd.DataFrame({
        'date': dates,
        'sales': np.random.randint(100, 1000, 100),
        'profit': np.random.randint(10, 200, 100),
        'category': np.random.choice(['Electronics', 'Clothing', 'Food'], 100)
    })
    return df

df = load_data()

# Metrics
col1, col2, col3, col4 = st.columns(4)
with col1:
    st.metric("Total Sales", f"${df['sales'].sum():,}", delta="12%")
with col2:
    st.metric("Total Profit", f"${df['profit'].sum():,}", delta="-3%")
with col3:
    st.metric("Avg Order", f"${df['sales'].mean():.2f}", delta="5%")
with col4:
    st.metric("Orders", len(df), delta="23")

# Charts
col1, col2 = st.columns(2)

with col1:
    st.subheader("Sales Trend")
    fig = px.line(df, x='date', y='sales', title='Daily Sales')
    st.plotly_chart(fig, use_container_width=True)

with col2:
    st.subheader("Category Distribution")
    fig = px.pie(df, names='category', values='sales', title='Sales by Category')
    st.plotly_chart(fig, use_container_width=True)

# Data table
st.subheader("Raw Data")
if st.checkbox("Show Data"):
    st.dataframe(df, use_container_width=True)

# Interactive widgets
st.subheader("Interactive Analysis")
selected_category = st.selectbox("Select Category", df['category'].unique())
filtered_df = df[df['category'] == selected_category]

fig = px.scatter(filtered_df, x='sales', y='profit',
                 title=f'{selected_category} - Sales vs Profit')
st.plotly_chart(fig, use_container_width=True)

# File uploader
st.subheader("Upload Your Data")
uploaded_file = st.file_uploader("Choose a CSV file", type="csv")
if uploaded_file is not None:
    user_df = pd.read_csv(uploaded_file)
    st.write(user_df)
"""

# Run with: streamlit run dashboard.py

# ═══════════════════════════════════════════
# DASH - PRODUCTION-READY DASHBOARDS
# ═══════════════════════════════════════════

"""
Dash by Plotly: Build analytical web apps
- Production-ready
- Highly customizable
- Built on Flask
- React.js components
"""

# Create file: dash_app.py
"""
import dash
from dash import dcc, html, Input, Output
import plotly.express as px
import pandas as pd
import numpy as np

# Initialize app
app = dash.Dash(__name__)

# Generate data
df = pd.DataFrame({
    'x': np.random.randn(1000),
    'y': np.random.randn(1000),
    'category': np.random.choice(['A', 'B', 'C'], 1000)
})

# Layout
app.layout = html.Div([
    html.H1('Dash Dashboard', style={'textAlign': 'center'}),

    html.Div([
        html.Label('Select Category:'),
        dcc.Dropdown(
            id='category-dropdown',
            options=[{'label': cat, 'value': cat} for cat in df['category'].unique()],
            value='A',
            multi=True
        ),
    ], style={'width': '48%', 'display': 'inline-block'}),

    html.Div([
        html.Label('Number of bins:'),
        dcc.Slider(
            id='bin-slider',
            min=10,
            max=100,
            step=10,
            value=30,
            marks={i: str(i) for i in range(10, 101, 10)}
        ),
    ], style={'width': '48%', 'float': 'right', 'display': 'inline-block'}),

    dcc.Graph(id='scatter-plot'),
    dcc.Graph(id='histogram'),
])

# Callbacks
@app.callback(
    Output('scatter-plot', 'figure'),
    Input('category-dropdown', 'value')
)
def update_scatter(selected_categories):
    if isinstance(selected_categories, str):
        selected_categories = [selected_categories]

    filtered_df = df[df['category'].isin(selected_categories)]
    fig = px.scatter(filtered_df, x='x', y='y', color='category',
                     title='Scatter Plot')
    return fig

@app.callback(
    Output('histogram', 'figure'),
    [Input('category-dropdown', 'value'),
     Input('bin-slider', 'value')]
)
def update_histogram(selected_categories, n_bins):
    if isinstance(selected_categories, str):
        selected_categories = [selected_categories]

    filtered_df = df[df['category'].isin(selected_categories)]
    fig = px.histogram(filtered_df, x='x', nbins=n_bins,
                       title=f'Histogram ({n_bins} bins)')
    return fig

if __name__ == '__main__':
    app.run_server(debug=True)
"""

# Run with: python dash_app.py

# ═══════════════════════════════════════════
# PANEL - FLEXIBLE DASHBOARDS
# ═══════════════════════════════════════════

"""
Panel: Create custom dashboards from any Python object
- Works with many viz libraries
- Flexible layouts
- Real-time updates
"""

# Example Panel dashboard
"""
import panel as pn
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

pn.extension()

# Create data
df = pd.DataFrame({
    'x': np.random.randn(100),
    'y': np.random.randn(100)
})

# Create widgets
bins = pn.widgets.IntSlider(name='Bins', start=5, end=50, value=20)
color = pn.widgets.ColorPicker(name='Color', value='#FF6B6B')

# Create interactive plot
@pn.depends(bins.param.value, color.param.value)
def plot(bins, color):
    fig, ax = plt.subplots(figsize=(10, 6))
    ax.hist(df['x'], bins=bins, color=color, alpha=0.7, edgecolor='black')
    ax.set_title(f'Histogram with {bins} bins')
    ax.set_xlabel('Value')
    ax.set_ylabel('Frequency')
    plt.close(fig)
    return fig

# Create dashboard
dashboard = pn.Column(
    '# Interactive Dashboard',
    pn.Row(bins, color),
    plot
)

# dashboard.servable()
# Run with: panel serve dashboard.py
"""

print("Dashboard examples created!")
```

---

<div align="center">

## 🎨 Design Principles

</div>

### Creating Effective Visualizations 🖼️

```bash
# ═══════════════════════════════════════════
# VISUALIZATION DESIGN PRINCIPLES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   1. CLARITY & SIMPLICITY                  ║
╚════════════════════════════════════════════════════════════╝

✅ DO:
─────────────────────────────────────────────────────────────
• Keep it simple - remove unnecessary elements
• Use clear, descriptive titles and labels
• Choose appropriate chart types
• Highlight key insights
• Use consistent formatting
• Provide context with annotations

❌ DON'T:
─────────────────────────────────────────────────────────────
• Overcrowd with too much information
• Use 3D effects unnecessarily
• Distort scales or axes
• Use too many colors
• Include chart junk (unnecessary decorations)

╔════════════════════════════════════════════════════════════╗
║                   2. COLOR USAGE                           ║
╚════════════════════════════════════════════════════════════╝

Color Principles:
─────────────────────────────────────────────────────────────
✅ Use color purposefully (highlight, categorize, show magnitude)
✅ Ensure accessibility (colorblind-friendly palettes)
✅ Limit color palette (3-5 colors maximum)
✅ Use consistent colors across charts
✅ Consider cultural meanings of colors

Recommended Color Palettes:
─────────────────────────────────────────────────────────────
Sequential:     Use for continuous data (e.g., temperature)
  • Blues, Greens, Oranges
  • Viridis, Plasma, Inferno

Diverging:      Use for data with meaningful midpoint
  • RdYlBu (Red-Yellow-Blue)
  • RdYlGn (Red-Yellow-Green)
  • Coolwarm

Categorical:    Use for distinct categories
  • Set1, Set2, Set3
  • Paired
  • Category10

Colorblind-friendly:
  • ColorBrewer qualitative schemes
  • Viridis family
  • Tableau 10

╔════════════════════════════════════════════════════════════╗
║                   3. TYPOGRAPHY                            ║
╚════════════════════════════════════════════════════════════╝

Text Guidelines:
─────────────────────────────────────────────────────────────
Title:          16-20pt, bold
Axis labels:    12-14pt, regular
Tick labels:    10-12pt, regular
Annotations:    10-12pt, italic for explanations

Font Choices:
• Sans-serif fonts (Arial, Helvetica, Open Sans)
• Avoid decorative fonts
• Maintain consistency

╔════════════════════════════════════════════════════════════╗
║                   4. DATA-INK RATIO                        ║
╚════════════════════════════════════════════════════════════╝

Maximize data-ink ratio:
─────────────────────────────────────────────────────────────
Data-ink ratio = (Data ink) / (Total ink used to print graphic)

✅ Increase:
• Focus on data
• Remove grid lines (or make subtle)
• Eliminate unnecessary borders
• Remove redundant labels
• Simplify legends

❌ Decrease:
• Heavy grid lines
• Thick borders
• Decorative elements
• Excessive colors
• 3D effects

╔════════════════════════════════════════════════════════════╗
║                   5. CONTEXT & STORYTELLING                ║
╚════════════════════════════════════════════════════════════╝

Every Visualization Should:
─────────────────────────────────────────────────────────────
1. Have a clear message
2. Provide context (what, when, where, how)
3. Guide the viewer's attention
4. Support decision-making
5. Be self-explanatory

Storytelling Structure:
─────────────────────────────────────────────────────────────
Beginning:  Introduce the question/problem
Middle:     Present the data and analysis
End:        Deliver insights and recommendations

╔════════════════════════════════════════════════════════════╗
║                   6. ACCESSIBILITY                         ║
╚════════════════════════════════════════════════════════════╝

Make visualizations accessible:
─────────────────────────────────────────────────────────────
✅ Use colorblind-friendly palettes
✅ Provide text alternatives
✅ Ensure sufficient contrast
✅ Use patterns in addition to colors
✅ Include descriptive titles and labels
✅ Make interactive elements keyboard-accessible
✅ Provide data tables as alternative

Common Color Blindness Types:
• Deuteranomaly (green-weak) - 6% of males
• Protanomaly (red-weak) - 1% of males
• Tritanomaly (blue-weak) - rare

Test your visualizations:
• Coblis (Color Blindness Simulator)
• Color Oracle
• Colorblind filters in design tools

╔════════════════════════════════════════════════════════════╗
║                   7. COMMON MISTAKES TO AVOID              ║
╚════════════════════════════════════════════════════════════╝

❌ Truncating Y-axis to exaggerate differences
❌ Using pie charts for too many categories (>5)
❌ Dual Y-axes with misleading scales
❌ 3D charts that distort perception
❌ Too many gridlines
❌ Cluttered legends
❌ Inconsistent scales across related charts
❌ Missing units or unclear labels
❌ Overusing animations
❌ Ignoring mobile responsiveness
```

---

<div align="center">

## 📊 Chart Selection Guide

</div>

### Choosing the Right Visualization 🎯

```bash
# ═══════════════════════════════════════════
# CHART TYPE SELECTION GUIDE
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   CHART SELECTION MATRIX                   ║
╚════════════════════════════════════════════════════════════╝
```

| Purpose          | Chart Type         | Best For                        | Avoid When                |
| ---------------- | ------------------ | ------------------------------- | ------------------------- |
| **Compare**      | Bar Chart          | Comparing categories            | Too many categories (>10) |
|                  | Column Chart       | Comparing over time             | Continuous data           |
|                  | Grouped Bar        | Multiple series comparison      | Complex relationships     |
|                  | Bullet Chart       | Performance vs target           | Multiple metrics          |
| **Distribution** | Histogram          | Show frequency distribution     | Categorical data          |
|                  | Box Plot           | Show statistical distribution   | Small datasets (<20)      |
|                  | Violin Plot        | Distribution shape              | Simple comparisons        |
|                  | Density Plot       | Smooth distribution             | Precise values needed     |
| **Relationship** | Scatter Plot       | Correlation between variables   | No clear relationship     |
|                  | Bubble Chart       | 3+ dimensions                   | Too many points           |
|                  | Heatmap            | Matrix of values                | Sparse data               |
|                  | Correlation Matrix | Variable relationships          | Non-numeric data          |
| **Composition**  | Pie Chart          | Parts of whole (<5 categories)  | Precise comparisons       |
|                  | Donut Chart        | Parts of whole with center info | Many categories           |
|                  | Stacked Bar        | Composition over categories     | Many components           |
|                  | Treemap            | Hierarchical data               | Deep hierarchies          |
|                  | Sunburst           | Hierarchical proportions        | Flat data                 |
| **Trend**        | Line Chart         | Trend over time                 | Few data points           |
|                  | Area Chart         | Magnitude and trend             | Negative values           |
|                  | Sparkline          | Inline trends                   | Detailed analysis         |
| **Geographic**   | Choropleth         | Regional comparisons            | Uneven geography          |
|                  | Bubble Map         | Location + magnitude            | Dense points              |
|                  | Heat Map           | Density visualization           | Precise locations         |
| **Hierarchical** | Tree Diagram       | Parent-child relationships      | Flat structures           |
|                  | Network Diagram    | Connections/relationships       | Simple hierarchies        |
|                  | Sankey Diagram     | Flow between stages             | Few connections           |

```bash
╔════════════════════════════════════════════════════════════╗
║                   DECISION TREE                            ║
╚════════════════════════════════════════════════════════════╝

What do you want to show?

1. COMPARISON
   ├─ Few categories (<7)?
   │  └─ YES → Bar Chart or Column Chart
   └─ Many categories (>7)?
      └─ YES → Sorted Bar Chart or Grouped Bar Chart

2. DISTRIBUTION
   ├─ Single variable?
   │  └─ YES → Histogram or Density Plot
   └─ Multiple variables?
      └─ YES → Box Plot or Violin Plot

3. RELATIONSHIP
   ├─ Two variables?
   │  └─ YES → Scatter Plot
   ├─ Three variables?
   │  └─ YES → Bubble Chart
   └─ Many variables?
      └─ YES → Heatmap or Correlation Matrix

4. COMPOSITION
   ├─ Simple (<5 categories)?
   │  └─ YES → Pie Chart
   ├─ Change over time?
   │  └─ YES → Stacked Area Chart
   └─ Hierarchical?
      └─ YES → Treemap or Sunburst

5. TREND OVER TIME
   ├─ Single metric?
   │  └─ YES → Line Chart
   ├─ Multiple metrics?
   │  └─ YES → Multiple Line Chart
   └─ With magnitude?
      └─ YES → Area Chart

6. GEOGRAPHIC
   ├─ Regions/countries?
   │  └─ YES → Choropleth Map
   ├─ Specific locations?
   │  └─ YES → Bubble Map
   └─ Density/heat?
      └─ YES → Heat Map

╔════════════════════════════════════════════════════════════╗
║                   CHART TYPE EXAMPLES                      ║
╚════════════════════════════════════════════════════════════╝

Bar Chart:
  When: Compare categories
  Example: Sales by region, Survey responses
  Best practices: Sort bars, start Y-axis at zero

Line Chart:
  When: Show trend over time
  Example: Stock prices, Temperature over days
  Best practices: Use for continuous time, clear labels

Scatter Plot:
  When: Show relationship between two variables
  Example: Height vs Weight, Price vs Sales
  Best practices: Add trendline, use color for categories

Pie Chart:
  When: Show parts of a whole (few categories)
  Example: Market share, Budget allocation
  Best practices: Limit to 5 slices, order by size

Heatmap:
  When: Show patterns in matrix data
  Example: Correlation matrix, Time-series patterns
  Best practices: Choose appropriate color scheme

Box Plot:
  When: Compare distributions across groups
  Example: Test scores by class, Salary by department
  Best practices: Show outliers, provide legend

Histogram:
  When: Show frequency distribution
  Example: Age distribution, Response times
  Best practices: Choose appropriate bin size

Treemap:
  When: Show hierarchical data as nested rectangles
  Example: Disk space usage, Budget breakdown
  Best practices: Use size and color meaningfully

Sankey Diagram:
  When: Show flow between categories
  Example: Customer journey, Energy flow
  Best practices: Limit complexity, clear labels

Network Diagram:
  When: Show connections between entities
  Example: Social networks, Dependencies
  Best practices: Layout matters, limit nodes
```

---

<div align="center">

## 🚀 Real-World Examples

</div>

### Complete Visualization Projects 💼

```python
# ═══════════════════════════════════════════
# PROJECT 1: SALES DASHBOARD
# ═══════════════════════════════════════════

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
import plotly.express as px
from datetime import datetime, timedelta

# Generate realistic sales data
np.random.seed(42)
dates = pd.date_range('2023-01-01', '2024-12-31', freq='D')
n_days = len(dates)

sales_data = pd.DataFrame({
    'date': dates,
    'product': np.random.choice(['Product A', 'Product B', 'Product C', 'Product D'], n_days),
    'region': np.random.choice(['North', 'South', 'East', 'West'], n_days),
    'sales': np.random.randint(100, 1000, n_days) + np.random.randn(n_days) * 50,
    'profit': np.random.randint(10, 200, n_days) + np.random.randn(n_days) * 20,
    'quantity': np.random.randint(1, 50, n_days),
    'customer_segment': np.random.choice(['Enterprise', 'SMB', 'Consumer'], n_days)
})

# Add seasonal trend
sales_data['sales'] += np.sin(np.arange(n_days) * 2 * np.pi / 365) * 200 + 500

print("Sales Data Shape:", sales_data.shape)
print("\nFirst rows:")
print(sales_data.head())

# ═══════════════════════════════════════════
# COMPREHENSIVE SALES ANALYSIS DASHBOARD
# ═══════════════════════════════════════════

fig = plt.figure(figsize=(20, 12))
gs = fig.add_gridspec(3, 3, hspace=0.3, wspace=0.3)

# Title
fig.suptitle('📊 Sales Analytics Dashboard - 2023-2024',
             fontsize=24, fontweight='bold', y=0.98)

# ─────────────────────────────────────────────
# 1. KPI Cards (Top row)
# ─────────────────────────────────────────────
kpi_ax = fig.add_subplot(gs[0, :])
kpi_ax.axis('off')

total_sales = sales_data['sales'].sum()
total_profit = sales_data['profit'].sum()
avg_order_value = sales_data['sales'].mean()
total_orders = len(sales_data)

kpis = [
    ('Total Sales', f'${total_sales:,.0f}', '+12.5%'),
    ('Total Profit', f'${total_profit:,.0f}', '+8.3%'),
    ('Avg Order Value', f'${avg_order_value:.2f}', '+5.2%'),
    ('Total Orders', f'{total_orders:,}', '+15.1%')
]

for i, (label, value, change) in enumerate(kpis):
    x_pos = 0.125 + i * 0.22

    # Card background
    rect = plt.Rectangle((x_pos - 0.08, 0.3), 0.16, 0.4,
                         facecolor='#ECF0F1', edgecolor='#3498DB',
                         linewidth=2, transform=kpi_ax.transAxes)
    kpi_ax.add_patch(rect)

    # Text
    kpi_ax.text(x_pos, 0.6, label, ha='center', va='center',
               fontsize=12, fontweight='bold', transform=kpi_ax.transAxes)
    kpi_ax.text(x_pos, 0.45, value, ha='center', va='center',
               fontsize=18, fontweight='bold', color='#2C3E50',
               transform=kpi_ax.transAxes)

    # Change indicator
    change_color = '#27AE60' if '+' in change else '#E74C3C'
    kpi_ax.text(x_pos, 0.35, change, ha='center', va='center',
               fontsize=11, fontweight='bold', color=change_color,
               transform=kpi_ax.transAxes)

# ─────────────────────────────────────────────
# 2. Sales Trend (Time Series)
# ─────────────────────────────────────────────
ax1 = fig.add_subplot(gs[1, :2])
monthly_sales = sales_data.groupby(pd.Grouper(key='date', freq='M'))['sales'].sum()
ax1.plot(monthly_sales.index, monthly_sales.values, linewidth=3,
         color='#3498DB', marker='o', markersize=6)
ax1.fill_between(monthly_sales.index, monthly_sales.values, alpha=0.3, color='#3498DB')
ax1.set_title('Monthly Sales Trend', fontsize=14, fontweight='bold', pad=15)
ax1.set_xlabel('Month', fontsize=11, fontweight='bold')
ax1.set_ylabel('Sales ($)', fontsize=11, fontweight='bold')
ax1.grid(True, alpha=0.3, linestyle='--')
ax1.spines['top'].set_visible(False)
ax1.spines['right'].set_visible(False)

# Add moving average
ma_30 = monthly_sales.rolling(window=3).mean()
ax1.plot(ma_30.index, ma_30.values, linewidth=2,
         color='#E74C3C', linestyle='--', label='3-Month MA')
ax1.legend(loc='upper left')

# ─────────────────────────────────────────────
# 3. Top Products (Bar Chart)
# ─────────────────────────────────────────────
ax2 = fig.add_subplot(gs[1, 2])
product_sales = sales_data.groupby('product')['sales'].sum().sort_values(ascending=True)
colors = ['#E74C3C', '#F39C12', '#27AE60', '#3498DB']
ax2.barh(product_sales.index, product_sales.values, color=colors, alpha=0.8)
ax2.set_title('Sales by Product', fontsize=14, fontweight='bold', pad=15)
ax2.set_xlabel('Total Sales ($)', fontsize=11, fontweight='bold')
ax2.spines['top'].set_visible(False)
ax2.spines['right'].set_visible(False)
ax2.grid(axis='x', alpha=0.3, linestyle='--')

# Add value labels
for i, (product, value) in enumerate(product_sales.items()):
    ax2.text(value + 5000, i, f'${value:,.0f}',
            va='center', fontsize=10, fontweight='bold')

# ─────────────────────────────────────────────
# 4. Regional Distribution (Pie Chart)
# ─────────────────────────────────────────────
ax3 = fig.add_subplot(gs[2, 0])
region_sales = sales_data.groupby('region')['sales'].sum()
colors_pie = ['#FF6B6B', '#4ECDC4', '#45B7D1', '#FFA07A']
wedges, texts, autotexts = ax3.pie(region_sales.values, labels=region_sales.index,
                                     autopct='%1.1f%%', colors=colors_pie,
                                     startangle=90, textprops={'fontsize': 11})
for autotext in autotexts:
    autotext.set_color('white')
    autotext.set_fontweight('bold')
ax3.set_title('Sales by Region', fontsize=14, fontweight='bold', pad=15)

# ─────────────────────────────────────────────
# 5. Customer Segment Analysis (Stacked Bar)
# ─────────────────────────────────────────────
ax4 = fig.add_subplot(gs[2, 1])
segment_product = sales_data.groupby(['customer_segment', 'product'])['sales'].sum().unstack()
segment_product.plot(kind='bar', stacked=True, ax=ax4,
                     color=['#E74C3C', '#F39C12', '#27AE60', '#3498DB'],
                     alpha=0.8)
ax4.set_title('Sales by Segment & Product', fontsize=14, fontweight='bold', pad=15)
ax4.set_xlabel('Customer Segment', fontsize=11, fontweight='bold')
ax4.set_ylabel('Sales ($)', fontsize=11, fontweight='bold')
ax4.legend(title='Product', bbox_to_anchor=(1.05, 1), loc='upper left')
ax4.tick_params(axis='x', rotation=45)
ax4.spines['top'].set_visible(False)
ax4.spines['right'].set_visible(False)
ax4.grid(axis='y', alpha=0.3, linestyle='--')

# ─────────────────────────────────────────────
# 6. Sales vs Profit Scatter
# ─────────────────────────────────────────────
ax5 = fig.add_subplot(gs[2, 2])
for region in sales_data['region'].unique():
    region_data = sales_data[sales_data['region'] == region]
    ax5.scatter(region_data['sales'], region_data['profit'],
               alpha=0.5, s=50, label=region)
ax5.set_title('Sales vs Profit by Region', fontsize=14, fontweight='bold', pad=15)
ax5.set_xlabel('Sales ($)', fontsize=11, fontweight='bold')
ax5.set_ylabel('Profit ($)', fontsize=11, fontweight='bold')
ax5.legend(title='Region', loc='upper left')
ax5.grid(True, alpha=0.3, linestyle='--')
ax5.spines['top'].set_visible(False)
ax5.spines['right'].set_visible(False)

plt.savefig('sales_dashboard.png', dpi=300, bbox_inches='tight', facecolor='white')
print("\n✅ Sales dashboard saved to 'sales_dashboard.png'")
plt.show()

# ═══════════════════════════════════════════
# PROJECT 2: CUSTOMER ANALYTICS
# ═══════════════════════════════════════════

# Generate customer data
np.random.seed(42)
n_customers = 1000

customer_data = pd.DataFrame({
    'customer_id': range(1, n_customers + 1),
    'age': np.random.randint(18, 70, n_customers),
    'income': np.random.lognormal(10.5, 0.5, n_customers),
    'spending_score': np.random.randint(1, 100, n_customers),
    'tenure_months': np.random.randint(1, 60, n_customers),
    'num_purchases': np.random.randint(1, 50, n_customers),
    'satisfaction': np.random.uniform(1, 5, n_customers),
    'segment': np.random.choice(['High Value', 'Medium Value', 'Low Value', 'Churned'],
                                n_customers, p=[0.15, 0.35, 0.40, 0.10])
})

# Customer analytics visualizations
fig, axes = plt.subplots(2, 3, figsize=(18, 10))
fig.suptitle('👥 Customer Analytics Dashboard', fontsize=20, fontweight='bold')

# 1. Age Distribution
axes[0, 0].hist(customer_data['age'], bins=20, color='#3498DB', alpha=0.7, edgecolor='black')
axes[0, 0].set_title('Age Distribution', fontsize=13, fontweight='bold')
axes[0, 0].set_xlabel('Age')
axes[0, 0].set_ylabel('Frequency')
axes[0, 0].axvline(customer_data['age'].mean(), color='red', linestyle='--',
                   linewidth=2, label=f'Mean: {customer_data["age"].mean():.1f}')
axes[0, 0].legend()
axes[0, 0].grid(axis='y', alpha=0.3)

# 2. Income vs Spending
scatter = axes[0, 1].scatter(customer_data['income'], customer_data['spending_score'],
                             c=customer_data['age'], cmap='viridis', alpha=0.6, s=50)
axes[0, 1].set_title('Income vs Spending Score', fontsize=13, fontweight='bold')
axes[0, 1].set_xlabel('Income ($)')
axes[0, 1].set_ylabel('Spending Score')
plt.colorbar(scatter, ax=axes[0, 1], label='Age')
axes[0, 1].grid(True, alpha=0.3)

# 3. Customer Segments
segment_counts = customer_data['segment'].value_counts()
colors = ['#27AE60', '#3498DB', '#F39C12', '#E74C3C']
axes[0, 2].bar(segment_counts.index, segment_counts.values, color=colors, alpha=0.8)
axes[0, 2].set_title('Customer Segments', fontsize=13, fontweight='bold')
axes[0, 2].set_xlabel('Segment')
axes[0, 2].set_ylabel('Count')
axes[0, 2].tick_params(axis='x', rotation=45)
for i, v in enumerate(segment_counts.values):
    axes[0, 2].text(i, v + 10, str(v), ha='center', fontweight='bold')
axes[0, 2].grid(axis='y', alpha=0.3)

# 4. Tenure Analysis
axes[1, 0].hist(customer_data['tenure_months'], bins=30, color='#9B59B6',
                alpha=0.7, edgecolor='black')
axes[1, 0].set_title('Customer Tenure Distribution', fontsize=13, fontweight='bold')
axes[1, 0].set_xlabel('Tenure (months)')
axes[1, 0].set_ylabel('Frequency')
axes[1, 0].grid(axis='y', alpha=0.3)

# 5. Satisfaction by Segment
segment_satisfaction = customer_data.groupby('segment')['satisfaction'].mean().sort_values()
axes[1, 1].barh(segment_satisfaction.index, segment_satisfaction.values,
                color=['#E74C3C', '#F39C12', '#3498DB', '#27AE60'], alpha=0.8)
axes[1, 1].set_title('Average Satisfaction by Segment', fontsize=13, fontweight='bold')
axes[1, 1].set_xlabel('Satisfaction Score')
axes[1, 1].set_xlim(0, 5)
for i, v in enumerate(segment_satisfaction.values):
    axes[1, 1].text(v + 0.1, i, f'{v:.2f}', va='center', fontweight='bold')
axes[1, 1].grid(axis='x', alpha=0.3)

# 6. Purchase Behavior
axes[1, 2].scatter(customer_data['tenure_months'], customer_data['num_purchases'],
                   c=customer_data['satisfaction'], cmap='RdYlGn', alpha=0.6, s=50)
axes[1, 2].set_title('Tenure vs Purchase Frequency', fontsize=13, fontweight='bold')
axes[1, 2].set_xlabel('Tenure (months)')
axes[1, 2].set_ylabel('Number of Purchases')
axes[1, 2].grid(True, alpha=0.3)

plt.tight_layout()
plt.savefig('customer_analytics.png', dpi=300, bbox_inches='tight')
print("✅ Customer analytics saved to 'customer_analytics.png'")
plt.show()

# ═══════════════════════════════════════════
# PROJECT 3: FINANCIAL ANALYSIS
# ═══════════════════════════════════════════

# Generate stock data
dates = pd.date_range('2023-01-01', '2024-12-31', freq='D')
n_days = len(dates)

# Simulate stock prices (random walk with drift)
np.random.seed(42)
returns = np.random.normal(0.001, 0.02, n_days)
price = 100 * np.exp(np.cumsum(returns))

stock_data = pd.DataFrame({
    'date': dates,
    'price': price,
    'volume': np.random.randint(1000000, 5000000, n_days)
})

# Calculate technical indicators
stock_data['MA20'] = stock_data['price'].rolling(window=20).mean()
stock_data['MA50'] = stock_data['price'].rolling(window=50).mean()
stock_data['returns'] = stock_data['price'].pct_change()

# Financial analysis dashboard
fig = plt.figure(figsize=(16, 10))
gs = fig.add_gridspec(3, 2, hspace=0.3, wspace=0.3)

fig.suptitle('📈 Financial Analysis Dashboard', fontsize=20, fontweight='bold')

# 1. Price Chart with Moving Averages
ax1 = fig.add_subplot(gs[0, :])
ax1.plot(stock_data['date'], stock_data['price'], linewidth=2,
         color='#2C3E50', label='Price', alpha=0.8)
ax1.plot(stock_data['date'], stock_data['MA20'], linewidth=2,
         color='#3498DB', label='MA20', linestyle='--')
ax1.plot(stock_data['date'], stock_data['MA50'], linewidth=2,
         color='#E74C3C', label='MA50', linestyle='--')
ax1.set_title('Stock Price with Moving Averages', fontsize=14, fontweight='bold')
ax1.set_ylabel('Price ($)', fontsize=11, fontweight='bold')
ax1.legend(loc='upper left')
ax1.grid(True, alpha=0.3)
ax1.spines['top'].set_visible(False)
ax1.spines['right'].set_visible(False)

# 2. Volume
ax2 = fig.add_subplot(gs[1, :], sharex=ax1)
ax2.bar(stock_data['date'], stock_data['volume'], color='#95A5A6', alpha=0.6)
ax2.set_title('Trading Volume', fontsize=14, fontweight='bold')
ax2.set_ylabel('Volume', fontsize=11, fontweight='bold')
ax2.grid(axis='y', alpha=0.3)
ax2.spines['top'].set_visible(False)
ax2.spines['right'].set_visible(False)

# 3. Returns Distribution
ax3 = fig.add_subplot(gs[2, 0])
returns_clean = stock_data['returns'].dropna()
ax3.hist(returns_clean, bins=50, color='#3498DB', alpha=0.7, edgecolor='black')
ax3.axvline(returns_clean.mean(), color='red', linestyle='--',
            linewidth=2, label=f'Mean: {returns_clean.mean():.4f}')
ax3.set_title('Daily Returns Distribution', fontsize=13, fontweight='bold')
ax3.set_xlabel('Returns')
ax3.set_ylabel('Frequency')
ax3.legend()
ax3.grid(axis='y', alpha=0.3)

# 4. Monthly Returns Heatmap
stock_data['year'] = stock_data['date'].dt.year
stock_data['month'] = stock_data['date'].dt.month
monthly_returns = stock_data.groupby(['year', 'month'])['returns'].sum().unstack()

ax4 = fig.add_subplot(gs[2, 1])
im = ax4.imshow(monthly_returns.values, cmap='RdYlGn', aspect='auto')
ax4.set_xticks(range(12))
ax4.set_xticklabels(['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun',
                     'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec'])
ax4.set_yticks(range(len(monthly_returns)))
ax4.set_yticklabels(monthly_returns.index)
ax4.set_title('Monthly Returns Heatmap', fontsize=13, fontweight='bold')
plt.colorbar(im, ax=ax4, label='Returns')

plt.savefig('financial_analysis.png', dpi=300, bbox_inches='tight')
print("✅ Financial analysis saved to 'financial_analysis.png'")
plt.show()

# ═══════════════════════════════════════════
# INTERACTIVE PLOTLY DASHBOARD
# ═══════════════════════════════════════════

# Create interactive version with Plotly
fig = make_subplots(
    rows=3, cols=2,
    subplot_titles=('Monthly Sales Trend', 'Sales by Product',
                    'Regional Distribution', 'Customer Segments',
                    'Sales vs Profit', 'Top Products'),
    specs=[[{'type': 'scatter'}, {'type': 'bar'}],
           [{'type': 'pie'}, {'type': 'bar'}],
           [{'type': 'scatter'}, {'type': 'bar'}]],
    row_heights=[0.35, 0.35, 0.30]
)

# 1. Sales Trend
monthly_sales_df = sales_data.groupby(pd.Grouper(key='date', freq='M'))['sales'].sum().reset_index()
fig.add_trace(
    go.Scatter(x=monthly_sales_df['date'], y=monthly_sales_df['sales'],
               mode='lines+markers', name='Sales',
               line=dict(color='#3498DB', width=3),
               marker=dict(size=8)),
    row=1, col=1
)

# 2. Sales by Product
product_sales_df = sales_data.groupby('product')['sales'].sum().reset_index()
fig.add_trace(
    go.Bar(x=product_sales_df['product'], y=product_sales_df['sales'],
           marker_color='#27AE60', name='Product Sales'),
    row=1, col=2
)

# 3. Regional Distribution
region_sales_df = sales_data.groupby('region')['sales'].sum().reset_index()
fig.add_trace(
    go.Pie(labels=region_sales_df['region'], values=region_sales_df['sales'],
           marker=dict(colors=['#FF6B6B', '#4ECDC4', '#45B7D1', '#FFA07A'])),
    row=2, col=1
)

# 4. Customer Segments
segment_sales_df = sales_data.groupby('customer_segment')['sales'].sum().reset_index()
fig.add_trace(
    go.Bar(x=segment_sales_df['customer_segment'], y=segment_sales_df['sales'],
           marker_color='#E74C3C'),
    row=2, col=2
)

# 5. Sales vs Profit Scatter
for region in sales_data['region'].unique():
    region_data = sales_data[sales_data['region'] == region]
    fig.add_trace(
        go.Scatter(x=region_data['sales'], y=region_data['profit'],
                   mode='markers', name=region,
                   marker=dict(size=5, opacity=0.6)),
        row=3, col=1
    )

# 6. Top Products
top_products = sales_data.groupby('product')['sales'].sum().nlargest(4).reset_index()
fig.add_trace(
    go.Bar(x=top_products['product'], y=top_products['sales'],
           marker_color='#F39C12'),
    row=3, col=2
)

# Update layout
fig.update_layout(
    height=1200,
    showlegend=True,
    title_text="📊 Interactive Sales Dashboard",
    title_font_size=24,
    template='plotly_white'
)

# fig.write_html('interactive_dashboard.html')
print("✅ Interactive dashboard would be saved to 'interactive_dashboard.html'")

print("\n" + "="*60)
print("All real-world examples completed successfully!")
print("="*60)
```

---

<div align="center">

## ✅ Best Practices

</div>

### Professional Visualization Standards 📋

```bash
# ═══════════════════════════════════════════
# VISUALIZATION BEST PRACTICES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   GENERAL GUIDELINES                       ║
╚════════════════════════════════════════════════════════════╝

✅ DO:
─────────────────────────────────────────────────────────────
• Start with a clear question or message
• Know your audience
• Choose the right chart type
• Use consistent colors and styles
• Label everything clearly
• Provide context (title, axis labels, units)
• Show data honestly (don't distort scales)
• Test with real users
• Make it accessible (colorblind-friendly)
• Cite data sources
• Keep it simple
• Use annotations to highlight key points
• Ensure readability at target size
• Provide legends when necessary
• Use whitespace effectively

❌ DON'T:
─────────────────────────────────────────────────────────────
• Mislead with truncated axes
• Use too many colors
• Overload with information
• Use 3D unnecessarily
• Ignore accessibility
• Forget to label axes
• Use unclear abbreviations
• Make font too small
• Use pie charts for many categories
• Rely solely on color to convey information
• Create chart junk
• Use Excel defaults blindly

╔════════════════════════════════════════════════════════════╗
║                   COLOR BEST PRACTICES                     ║
╚════════════════════════════════════════════════════════════╝

Color Selection:
─────────────────────────────────────────────────────────────
✅ Use colorblind-friendly palettes
   • Viridis, Plasma, Cividis
   • ColorBrewer schemes
   • Avoid red-green combinations

✅ Limit your palette
   • 3-5 colors for categorical data
   • Single hue for sequential data
   • Diverging for data with meaningful midpoint

✅ Use color purposefully
   • Highlight important data
   • Show categories
   • Indicate magnitude
   • Draw attention

✅ Ensure sufficient contrast
   • Text should be readable
   • WCAG AA standard: 4.5:1 ratio
   • Test in grayscale

✅ Be consistent across charts
   • Same categories = same colors
   • Create a style guide

❌ Avoid:
   • Rainbow color maps (except for specific cases)
   • Red-green for colorblind users
   • Too many colors
   • Low contrast combinations

╔════════════════════════════════════════════════════════════╗
║                   TYPOGRAPHY GUIDELINES                    ║
╚════════════════════════════════════════════════════════════╝

Font Sizes:
─────────────────────────────────────────────────────────────
Title:          18-24pt
Subtitle:       14-16pt
Axis labels:    12-14pt
Tick labels:    10-12pt
Annotations:    10-12pt
Legend:         10-11pt

Font Families:
─────────────────────────────────────────────────────────────
• Sans-serif for screens (Arial, Helvetica, Open Sans, Roboto)
• Serif for print (Times New Roman, Georgia)
• Monospace for code/data (Courier, Consolas)
• Avoid decorative fonts

Typography Tips:
─────────────────────────────────────────────────────────────
✅ Use bold for emphasis, not color alone
✅ Maintain consistent font family
✅ Use appropriate line spacing
✅ Keep text horizontal when possible
✅ Align text consistently

╔════════════════════════════════════════════════════════════╗
║                   LAYOUT & COMPOSITION                     ║
╚════════════════════════════════════════════════════════════╝

Layout Principles:
─────────────────────────────────────────────────────────────
✅ Visual Hierarchy
   • Most important elements first
   • Use size and position
   • Guide the eye

✅ White Space
   • Don't fill every pixel
   • Let visualizations breathe
   • Improve focus

✅ Alignment
   • Align elements consistently
   • Create visual connections
   • Use grids

✅ Balance
   • Distribute visual weight
   • Symmetric or asymmetric
   • Consider negative space

✅ Proximity
   • Group related elements
   • Separate unrelated elements
   • Create clear sections

╔════════════════════════════════════════════════════════════╗
║                   AXES & SCALES                            ║
╚════════════════════════════════════════════════════════════╝

Axis Best Practices:
─────────────────────────────────────────────────────────────
✅ Start Y-axis at zero (for bar charts)
✅ Use appropriate scale (linear vs log)
✅ Label axes clearly with units
✅ Use round numbers for tick marks
✅ Remove unnecessary gridlines
✅ Consider dual axes carefully (can mislead)
✅ Show data range appropriately

Scale Types:
─────────────────────────────────────────────────────────────
Linear:     Default, equal intervals
Log:        Large range of values, exponential growth
Sqrt:       Count data with many small values
Symlog:     Data spanning positive and negative with large range

When to use log scale:
• Data spans multiple orders of magnitude
• Exponential growth/decay
• Multiplicative relationships
• Percentage changes matter more than absolute

╔════════════════════════════════════════════════════════════╗
║                   ANNOTATIONS & LABELS                     ║
╚════════════════════════════════════════════════════════════╝

Effective Annotations:
─────────────────────────────────────────────────────────────
✅ Highlight key insights
✅ Explain anomalies
✅ Provide context
✅ Show trends
✅ Add data points for clarity
✅ Use arrows to direct attention
✅ Keep text concise

Annotation Types:
─────────────────────────────────────────────────────────────
• Text labels (explain data points)
• Reference lines (show targets, averages)
• Shaded regions (highlight periods)
• Arrows (show trends, connections)
• Callout boxes (detailed explanations)

╔════════════════════════════════════════════════════════════╗
║                   LEGENDS & TITLES                         ║
╚════════════════════════════════════════════════════════════╝

Titles:
─────────────────────────────────────────────────────────────
✅ Be descriptive and specific
✅ Include key takeaway when appropriate
✅ Use sentence case or title case consistently

Examples:
❌ "Sales Data"
✅ "Monthly Sales Increased 25% in Q4 2024"

❌ "Chart 1"
✅ "Customer Satisfaction by Product Category"

Legends:
─────────────────────────────────────────────────────────────
✅ Place near relevant data
✅ Use clear, descriptive labels
✅ Order logically (alphabetically or by value)
✅ Consider direct labeling instead of legend
✅ Make interactive when possible

╔════════════════════════════════════════════════════════════╗
║                   TESTING & VALIDATION                     ║
╚════════════════════════════════════════════════════════════╝

Before Publishing:
─────────────────────────────────────────────────────────────
☐ Verify data accuracy
☐ Check calculations
☐ Test with target audience
☐ View at intended size
☐ Check on different devices
☐ Test in grayscale
☐ Validate with colorblind simulation
☐ Proofread all text
☐ Ensure all elements are visible
☐ Check export quality
☐ Test interactivity (if applicable)
☐ Review accessibility

Questions to Ask:
─────────────────────────────────────────────────────────────
• Can I understand it in 5 seconds?
• Is the main message clear?
• Are labels readable?
• Is color used effectively?
• Would it work in black and white?
• Is it accessible to all users?
• Does it answer the question?

╔════════════════════════════════════════════════════════════╗
║                   EXPORT & SHARING                         ║
╚════════════════════════════════════════════════════════════╝

Export Guidelines:
─────────────────────────────────────────────────────────────
Format Selection:
• PNG: Web, presentations (raster)
• SVG: Scaling, print, web (vector)
• PDF: Print, reports (vector)
• HTML: Interactive dashboards
• JPG: Photos only (lossy compression)

Resolution:
• Screen: 72-96 DPI
• Print: 300+ DPI
• Large format: 150-300 DPI

File Size:
• Optimize for web (<1MB)
• Balance quality vs size
• Compress appropriately

Sharing Best Practices:
─────────────────────────────────────────────────────────────
✅ Include data source
✅ Provide context
✅ Share interactive version when possible
✅ Include alt text for accessibility
✅ Document methodology
✅ Make data available if appropriate
✅ License clearly
```

---

<div align="center">

## 📚 Quick Reference

</div>

### Common Operations Cheat Sheet 🚀

```python
# ═══════════════════════════════════════════
# MATPLOTLIB QUICK REFERENCE
# ═══════════════════════════════════════════

import matplotlib.pyplot as plt
import numpy as np

# Basic plot
plt.plot([1, 2, 3], [1, 4, 9])
plt.show()

# Save figure
plt.savefig('plot.png', dpi=300, bbox_inches='tight')

# Common plot types
plt.plot(x, y)              # Line
plt.scatter(x, y)           # Scatter
plt.bar(x, y)               # Bar
plt.hist(data, bins=30)     # Histogram
plt.boxplot(data)           # Box plot
plt.pie(sizes, labels=labels)  # Pie

# Customization
plt.title('Title')
plt.xlabel('X Label')
plt.ylabel('Y Label')
plt.legend()
plt.grid(True)
plt.xlim(0, 10)
plt.ylim(0, 100)

# Subplots
fig, axes = plt.subplots(2, 2, figsize=(12, 8))
axes[0, 0].plot(x, y)

# Style
plt.style.use('seaborn-v0_8')
plt.rcParams['figure.figsize'] = (10, 6)

# ═══════════════════════════════════════════
# SEABORN QUICK REFERENCE
# ═══════════════════════════════════════════

import seaborn as sns

# Distribution
sns.histplot(data=df, x='column', kde=True)
sns.kdeplot(data=df, x='column')
sns.boxplot(data=df, x='category', y='value')
sns.violinplot(data=df, x='category', y='value')

# Categorical
sns.countplot(data=df, x='category')
sns.barplot(data=df, x='category', y='value')
sns.pointplot(data=df, x='category', y='value')

# Relationship
sns.scatterplot(data=df, x='x', y='y', hue='category')
sns.lineplot(data=df, x='x', y='y')
sns.regplot(data=df, x='x', y='y')

# Matrix
sns.heatmap(data=df.corr(), annot=True, cmap='coolwarm')

# Multi-plot
sns.pairplot(df, hue='category')
sns.FacetGrid(df, col='category').map(plt.hist, 'value')

# Style
sns.set_style('whitegrid')
sns.set_palette('husl')

# ═══════════════════════════════════════════
# PLOTLY QUICK REFERENCE
# ═══════════════════════════════════════════

import plotly.express as px
import plotly.graph_objects as go

# Express (high-level)
fig = px.scatter(df, x='x', y='y', color='category')
fig = px.line(df, x='x', y='y')
fig = px.bar(df, x='category', y='value')
fig = px.histogram(df, x='value')
fig = px.box(df, x='category', y='value')

# Graph objects (low-level)
fig = go.Figure()
fig.add_trace(go.Scatter(x=x, y=y, mode='lines'))
fig.update_layout(title='Title', xaxis_title='X', yaxis_title='Y')

# Show/Save
fig.show()
fig.write_html('plot.html')
fig.write_image('plot.png')

# ═══════════════════════════════════════════
# COLOR PALETTES
# ═══════════════════════════════════════════

# Matplotlib
colors = ['#FF6B6B', '#4ECDC4', '#45B7D1']
plt.plot(x, y, color=colors[0])

# Seaborn
sns.color_palette('husl', 8)
sns.color_palette('Set2')

# Plotly
colors = px.colors.qualitative.Plotly
colors = px.colors.sequential.Viridis
```

---

<div align="center">

## 🎓 Learning Resources

</div>

### Essential Visualization Resources 📖

```
📘 Books
   • The Visual Display of Quantitative Information (Edward Tufte)
   • Storytelling with Data (Cole Nussbaumer Knaflic)
   • The Truthful Art (Alberto Cairo)
   • Fundamentals of Data Visualization (Claus O. Wilke)

📗 Online Courses
   • Data Visualization with Python (Coursera)
   • Data Visualization (DataCamp)
   • Plotly & Dash (Udemy)

📙 Documentation
   • Matplotlib: https://matplotlib.org/
   • Seaborn: https://seaborn.pydata.org/
   • Plotly: https://plotly.com/python/
   • Altair: https://altair-viz.github.io/

🎥 YouTube Channels
   • Matplotlib Tutorials
   • Data Science Dojo
   • Corey Schafer

🛠️ Tools & Resources
   • ColorBrewer: https://colorbrewer2.org/
   • Coolors: https://coolors.co/
   • Data Viz Project: https://datavizproject.com/
   • From Data to Viz: https://www.data-to-viz.com/

💬 Communities
   • r/dataisbeautiful
   • r/dataviz
   • Data Visualization Society
   • Plotly Community Forum
```

---

<div align="center">

## 🎯 Summary

</div>

### Key Takeaways 💡

```bash
╔════════════════════════════════════════════════════════════╗
║                   REMEMBER                                 ║
╚════════════════════════════════════════════════════════════╝

1. Choose the Right Tool
   • Matplotlib: Full control, publication-quality
   • Seaborn: Statistical analysis, beautiful defaults
   • Plotly: Interactive, web-ready
   • Choose based on needs

2. Select Appropriate Charts
   • Comparison → Bar charts
   • Distribution → Histograms, box plots
   • Relationship → Scatter plots
   • Trend → Line charts
   • Composition → Pie, stacked bar

3. Design Effectively
   • Keep it simple
   • Use color purposefully
   • Label clearly
   • Make accessible
   • Tell a story

4. Test & Iterate
   • Get feedback
   • Test with users
   • Check accessibility
   • Refine continuously

5. Share Responsibly
   • Cite sources
   • Be truthful
   • Provide context
   • Make data available

"A visualization that doesn't communicate is just decoration."
```

---

<div align="center">

**Built with 📊 by MrDib, for data storytellers**

_Remember: "The greatest value of a picture is when it forces us to notice what we never expected to see."_ - John Tukey

**Happy Visualizing!** 🎨
