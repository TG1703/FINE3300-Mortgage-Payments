    def mortgage_payments(principal, rate, amortization):
    """
    Calculate mortgage payments with different payment frequencies, adjusted for semi-annual compounding.

    Parameters:
    principal (float): The loan amount
    rate (float): Annual interest rate (in percent, for example, 5 for 5%).
    amortization (int): Amortization period in years.

    Returns:
    (monthly, semi-monthly, bi-weekly, weekly, rapid bi-weekly, rapid weekly) payments
    """
    annual_rate = rate / 100  # Convert percentage to decimal

    # Adjust for semi-annual compounding to get the effective monthly rate
    monthly_rate = (1 + annual_rate / 2) ** (1 / 6) - 1
    num_monthly_payments = amortization * 12

    # Standard Monthly Payment
    monthly = (principal * monthly_rate * (1 + monthly_rate) ** num_monthly_payments) / \
              ((1 + monthly_rate) ** num_monthly_payments - 1)

    # Semi-Monthly Payment (24 payments per year)
    semi_monthly = monthly / 2

    # Bi-Weekly Payment (26 payments per year)
    bi_weekly = monthly * 12 / 26

    # Weekly Payment (52 payments per year)
    weekly = monthly * 12 / 52

    # Rapid Bi-Weekly Payment (half of monthly payment, paid 26 times a year)
    rapid_bi_weekly = monthly / 2

    # Rapid Weekly Payment (quarter of monthly payment, paid 52 times a year)
    rapid_weekly = monthly / 4

    # Formatting output
    print(f"Monthly Payment: ${monthly:.2f}")
    print(f"Semi-monthly Payment: ${semi_monthly:.2f}")
    print(f"Bi-weekly Payment: ${bi_weekly:.2f}")
    print(f"Weekly Payment: ${weekly:.2f}")
    print(f"Rapid Bi-weekly Payment: ${rapid_bi_weekly:.2f}")
    print(f"Rapid Weekly Payment: ${rapid_weekly:.2f}")

    return (round(monthly, 2), round(semi_monthly, 2), round(bi_weekly, 2),
            round(weekly, 2), round(rapid_bi_weekly, 2), round(rapid_weekly, 2))
    # Example
    # principal = 100,000, rate = 5.5% annually, amortization = 25 years
    # Enter parameters below
    mortgage_payments(100000, 5.5, 25)
