# Heat-Exchanger-Design
Python-based Heat Exchanger Design Tool for calculating Reynolds Number, Nusselt Number, Convective Heat Transfer Coefficient, and Heat Transfer Rate using fundamental heat transfer and fluid mechanics correlations.
import math

def reynolds_number(rho, velocity, diameter, mu):
    return (rho * velocity * diameter) / mu

def nusselt_number(Re, Pr):
    if Re < 2300:
        return 3.66
    else:
        return 0.023 * (Re ** 0.8) * (Pr ** 0.4)

def heat_transfer_coefficient(Nu, k, diameter):
    return (Nu * k) / diameter

def heat_transfer_rate(h, area, delta_t):
    return h * area * delta_t

print("=== Heat Exchanger Design Tool ===")

rho = float(input("Fluid Density (kg/m³): "))
velocity = float(input("Velocity (m/s): "))
diameter = float(input("Pipe Diameter (m): "))
mu = float(input("Dynamic Viscosity (Pa.s): "))
Pr = float(input("Prandtl Number: "))
k = float(input("Thermal Conductivity (W/m.K): "))
area = float(input("Heat Transfer Area (m²): "))
delta_t = float(input("Temperature Difference (°C): "))

Re = reynolds_number(rho, velocity, diameter, mu)
Nu = nusselt_number(Re, Pr)
h = heat_transfer_coefficient(Nu, k, diameter)
Q = heat_transfer_rate(h, area, delta_t)

print("\n===== RESULTS =====")
print(f"Reynolds Number : {Re:.2f}")
print(f"Nusselt Number  : {Nu:.2f}")
print(f"h Coefficient   : {h:.2f} W/m².K")
print(f"Heat Transfer   : {Q:.2f} W")
