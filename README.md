# PRODIGY_CS_03
PASSWORD STRENGTH CHECKER

import re

def check_password_strength(password):
    if len(password) < 8:
        return "Weak: Password must be at least 8 characters long."

    # Check for character variety
    has_lowercase = bool(re.search(r'[a-z]', password))
    has_uppercase = bool(re.search(r'[A-Z]', password))
    has_digit = bool(re.search(r'\d', password))
    has_special = bool(re.search(r'[!@#$%^&*(),.?":{}|<>]', password))

    # Check for common patterns
    common_passwords = ['123456', 'password', 'qwerty', 'abc123']
    if password.lower() in common_passwords:
        return "Weak: Password is too common."

    # Assess password strength
    if has_lowercase and has_uppercase and has_digit and has_special:
        return "Strong: Your password is secure."
    elif has_lowercase and has_uppercase and has_digit:
        return "Moderate: Add special characters for a stronger password."
    else:
        return "Weak: Use a mix of uppercase, lowercase, digits, and special characters."

# Example usage
password = input("Enter your password: ")
strength = check_password_strength(password)
print(strength)
