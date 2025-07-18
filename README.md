import numpy as np
import matplotlib.pyplot as plt

# Set random seed for reproducibility
np.random.seed(42)

# Number of points to generate
n_points = 1000

# Algorithm 1: Uniform distribution (0, 1)
uniform_x = np.random.uniform(0, 1, n_points)
uniform_y = np.random.uniform(0, 1, n_points)

# Algorithm 2: Non-uniform distribution (clustered around center)
# Using beta distribution which creates clustering
beta_x = np.random.beta(2, 2, n_points)  # Beta(2,2) clusters around 0.5
beta_y = np.random.beta(2, 2, n_points)

# Create subplots
fig, (ax1, ax2) = plt.subplots(1, 2, figsize=(12, 5))

# Plot 1: Uniform distribution
ax1.scatter(uniform_x, uniform_y, alpha=0.6, s=20, color='blue')
ax1.set_title('Uniform Random Distribution', fontsize=14, fontweight='bold')
ax1.set_xlabel('X values')
ax1.set_ylabel('Y values')
ax1.grid(True, alpha=0.3)
ax1.set_xlim(0, 1)
ax1.set_ylim(0, 1)

# Plot 2: Non-uniform distribution
ax2.scatter(beta_x, beta_y, alpha=0.6, s=20, color='red')
ax2.set_title('Non-Uniform Random Distribution\n(Beta Distribution)', fontsize=14, fontweight='bold')
ax2.set_xlabel('X values')
ax2.set_ylabel('Y values')
ax2.grid(True, alpha=0.3)
ax2.set_xlim(0, 1)
ax2.set_ylim(0, 1)

plt.savefig('t1.pdf')
# Adjust layout and show
plt.tight_layout()
plt.show()

# Print some statistics to compare
print("=== Distribution Comparison ===")
print(f"Uniform - Mean X: {np.mean(uniform_x):.3f}, Std X: {np.std(uniform_x):.3f}")
print(f"Uniform - Mean Y: {np.mean(uniform_y):.3f}, Std Y: {np.std(uniform_y):.3f}")
print(f"Beta - Mean X: {np.mean(beta_x):.3f}, Std X: {np.std(beta_x):.3f}")
print(f"Beta - Mean Y: {np.mean(beta_y):.3f}, Std Y: {np.std(beta_y):.3f}")

# Additional visualization: Histograms to show distribution shapes
fig, ((ax3, ax4), (ax5, ax6)) = plt.subplots(2, 2, figsize=(10, 8))

# Histograms for uniform distribution
ax3.hist(uniform_x, bins=30, alpha=0.7, color='blue', edgecolor='black')
ax3.set_title('Uniform X Distribution')
ax3.set_xlabel('Value')
ax3.set_ylabel('Frequency')

ax4.hist(uniform_y, bins=30, alpha=0.7, color='blue', edgecolor='black')
ax4.set_title('Uniform Y Distribution')
ax4.set_xlabel('Value')
ax4.set_ylabel('Frequency')

# Histograms for beta distribution
ax5.hist(beta_x, bins=30, alpha=0.7, color='red', edgecolor='black')
ax5.set_title('Beta X Distribution')
ax5.set_xlabel('Value')
ax5.set_ylabel('Frequency')

ax6.hist(beta_y, bins=30, alpha=0.7, color='red', edgecolor='black')
ax6.set_title('Beta Y Distribution')
ax6.set_xlabel('Value')
ax6.set_ylabel('Frequency')

plt.savefig('tt.pdf')
plt.tight_layout()
plt.show()
