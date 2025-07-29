def calculate_bmi(weight_kg, height_cm):
    """
    Calculate BMI given weight in kilograms and height in centimeters.

    Args:
        weight_kg (float): Weight in kilograms.
        height_cm (float): Height in centimeters.

    Returns:
        float: Calculated BMI.
    """
    height_m = height_cm / 100
    bmi = weight_kg / (height_m ** 2)
    return bmi

def bmi_category(bmi, gender):
    """
    Return the BMI category for a given BMI and gender.
    While BMI calculation is the same for males and females,
    the interpretation (category) thresholds can sometimes differ.
    Here we use standard WHO categories, which are the same for both.

    Args:
        bmi (float): Calculated BMI.
        gender (str): 'male' or 'female' (for future customization).

    Returns:
        str: BMI category.
    """
    if bmi < 18.5:
        return "Underweight"
    elif 18.5 <= bmi < 25:
        return "Normal weight"
    elif 25 <= bmi < 30:
        return "Overweight"
    else:
        return "Obese"

def main():
    print("BMI Calculator")
    gender = input("Enter gender (male/female): ").strip().lower()
    if gender not in ("male", "female"):
        print("Invalid gender.")
        return
    try:
        weight = float(input("Enter weight (kg): "))
        height = float(input("Enter height (cm): "))
    except ValueError:
        print("Invalid input for weight or height.")
        return

    bmi = calculate_bmi(weight, height)
    category = bmi_category(bmi, gender)
    print(f"\nGender: {gender.capitalize()}")
    print(f"Weight: {weight} kg")
    print(f"Height: {height} cm")
    print(f"BMI: {bmi:.2f}")
    print(f"Category: {category}")

if __name__ == "__main__":
    main()
