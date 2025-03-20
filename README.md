```
import itertools

# Define values for R, L, C
R_values = [1, 2, 3]  # Example values for resistors
L_values = [1, 2, 3]  # Example values for inductors
C_values = [1, 2, 3]  # Example values for capacitors

# Function to calculate total resistance in series
def total_resistance_series(resistances):
    return sum(resistances)

# Function to calculate total resistance in parallel
def total_resistance_parallel(resistances):
    return 1 / sum(1 / r for r in resistances)

# Function to generate RLC combinations
def generate_combinations():
    circuits = []
    
    # Generate all combinations of R, L, C
    for R_comb in itertools.permutations(R_values):
        for L_comb in itertools.permutations(L_values):
            for C_comb in itertools.permutations(C_values):
                # Series combinations
                series_circuit = {
                    'type': 'series',
                    'R': total_resistance_series(R_comb),
                    'L': total_resistance_series(L_comb),
                    'C': total_resistance_series(C_comb)
                }
                circuits.append(series_circuit)

                # Parallel combinations
                parallel_circuit = {
                    'type': 'parallel',
                    'R': total_resistance_parallel(R_comb),
                    'L': total_resistance_parallel(L_comb),
                    'C': total_resistance_parallel(C_comb)
                }
                circuits.append(parallel_circuit)

    return circuits

# Generate and display circuits
all_circuits = generate_combinations()
for circuit in all_circuits:
    print(circuit)
```
