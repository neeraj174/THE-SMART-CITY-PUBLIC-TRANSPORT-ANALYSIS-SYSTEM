# SMART TRANSPORT PUBLIC ANALYSIS SYSTEM CODE
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# 1. Create simple transport data
np.random.seed(0)
routes = ['Route A', 'Route B', 'Route C', 'Route D', 'Route E']

data = {
    'route': np.random.choice(routes, 100),
    'passengers': np.random.randint(15, 60, 100),
    'delay_mins': np.random.randint(-2, 25, 100)
}
df = pd.DataFrame(data)

# 2. Analyze data
summary = df.groupby('route').mean()
print(summary)

# 3. Plot results
plt.figure(figsize=(10, 4))

# Graph 1: Average Delay per Route
plt.subplot(1, 2, 1)
plt.bar(summary.index, summary['delay_mins'], color='orange')
plt.title('Avg Delay per Route')
plt.ylabel('Minutes')

# Graph 2: Average Passengers per Route
plt.subplot(1, 2, 2)
plt.bar(summary.index, summary['passengers'], color='teal')
plt.title('Avg Passengers per Route')
plt.ylabel('Passengers')

plt.tight_layout()
plt.show()
