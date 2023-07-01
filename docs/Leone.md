Result 


![graph](https://github.com/AyanleN/KEYS2023/assets/111706166/6b4a1a3d-554e-4a3a-a1dd-6dc28435c62e)

import cyvcf2
import matplotlib.pyplot as plt

# Read the vcf.gz file and create a VCF object
vcf = cyvcf2.VCF("/home/jovyan/data-store/home/ayanle/keys/ALL.chr21.phase3_shapeit2_mvncall_integrated_v5b.20130502.genotypes.vcf")

# Extract variant positions and frequencies for the first 100 samples
positions = []
frequencies = []
for variant in vcf:
    positions.append(variant.POS)
    frequencies.append(variant.INFO["AF"])
    if len(positions) >= 100:
        break

# Create a scatter plot
plt.scatter(positions, frequencies)
plt.xlabel("Variant Positions")
plt.ylabel("Frequencies")
plt.title("Variant Positions vs Frequencies (First 100 Samples)")
plt.show()

