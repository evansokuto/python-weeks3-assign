# python-weeks3-assign

def calculate_discount(price, discount_percent):
  """
  Calculates the final price after applying a discount, if the discount is 20% or higher.

  Args:
    price (float): The original price of the item.
    discount_percent (float): The discount percentage.

  Returns:
    float: The final price after applying the discount (if >= 20%),
           or the original price otherwise.
  """
  if discount_percent >= 20:
    # Calculate the discount amount
    discount_amount = price * (discount_percent / 100)
    # Calculate the final price
    final_price = price - discount_amount
    return final_price
  else:
    # No discount applied (or discount < 20%), return original price
    return price

# --- Main part of the script ---
if __name__ == "__main__":
  try:
    # Prompt user for original price
    original_price_str = input("Enter the original price of the item: ")
    original_price = float(original_price_str)

    # Prompt user for discount percentage
    discount_percent_str = input("Enter the discount percentage (e.g., 15 for 15%): ")
    discount_percent = float(discount_percent_str)

    # Basic validation for non-negative inputs
    if original_price < 0 or discount_percent < 0:
        print("Error: Price and discount percentage cannot be negative.")
        sys.exit(1) # Exit if input is invalid

    # Calculate the final price using the function
    final_price_result = calculate_discount(original_price, discount_percent)

    # Print the result
    # Check if the price changed to provide a more informative message
    if final_price_result == original_price:
      print(f"\nThe discount percentage ({discount_percent}%) is less than 20%.")
      print(f"No discount applied. The price remains: ${final_price_result:.2f}")
    else:
      print(f"\nDiscount of {discount_percent}% applied.")
      print(f"The final price after applying the discount is: ${final_price_result:.2f}")

  except ValueError:
    print("\nError: Invalid input. Please enter numeric values for price and discount percentage.")
  except Exception as e:
    print(f"\nAn unexpected error occurred: {e}")
