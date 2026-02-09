# Ev-charging-calculator
A Java-based EV charging calculator that estimates required energy, charging time, and cost based on battery capacity and charger detail.

import java.util.Scanner;

public class EVChargingCalculator {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Input section
        System.out.print("Enter battery capacity (kWh): ");
        double batteryCapacity = sc.nextDouble();

        System.out.print("Enter current charge level (%): ");
        double currentCharge = sc.nextDouble();

        System.out.print("Enter charger rating (kW): ");
        double chargerRating = sc.nextDouble();

        System.out.print("Enter charging efficiency (%): ");
        double efficiency = sc.nextDouble();

        System.out.print("Enter cost per unit (₹ per kWh): ");
        double costPerUnit = sc.nextDouble();

        // Calculations
        double requiredEnergy =
                batteryCapacity * (100 - currentCharge) / 100;

        double actualEnergy =
                requiredEnergy / (efficiency / 100);

        double chargingTime =
                actualEnergy / chargerRating;

        double chargingCost =
                actualEnergy * costPerUnit;

        // Output section
        System.out.println("\n EV Charging Details");
        System.out.println("Required Energy: " + requiredEnergy + " kWh");
        System.out.println("Charging Time: " + chargingTime + " hours");
        System.out.println("Charging Cost: ₹" + chargingCost);

        sc.close();
    }
}
