# CBAR Rates

A Python library to work with Azerbaijani manat (AZN) official exchange rates based on [CBAR](https://cbar.az/currency/rates?language=en) (The Central Bank of the Republic of Azerbaijan).

## Features
- Retrieve official CBAR exchange rates for the Azerbaijani manat (AZN).
- Compare exchange rates between two dates and calculate differences.
- Filter results by specific currency codes (e.g., USD, EUR).

## Requirements
- Python 3.7 or higher
- `requests` library

## Installation

Install the library using pip:

```bash
pip install cbar-rates --upgrade
```

For isolated installations, use a virtual environment:

```bash
python3 -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install cbar-rates
```

## Examples

### Usage of `get_rates()`
```python
from datetime import date
import cbar

rates_date = date.today()
currencies = ["USD", "EUR"]

rates = cbar.get_rates(rates_date, currencies)

print(rates)
# Output:
{
    "date": "18.11.2024",
    "currencies": {
        "USD": {
            "nominal": "1",
            "value": 1.7
        },
        "EUR": {
            "nominal": "1",
            "value": 1.7919
        },
    }
}
```

### Usage of `get_rates_with_diff()`
```python
from datetime import date
import cbar

previous_date = date(2024, 11, 25)
next_date = date(2024, 11, 26)
currencies = ["USD", "EUR"]

rates = cbar.get_rates_with_diff(previous_date, next_date, currencies)

print(rates)
# Output:
{
    "previous_date": "25.11.2024",
    "next_date": "26.11.2024",
    "currencies": {
        "USD": {
            "nominal": "1",
            "previous_value": 1.7,
            "next_value": 1.7,
            "difference": 0.0,
        },
        "EUR": {
            "nominal": "1",
            "previous_value": 1.7814,
            "next_value": 1.7815,
            "difference": 0.0001,
        },
    }
}
```

You can find all available currency codes on the [CBAR website](https://www.cbar.az/currency/rates?language=en)

## License
This project is licensed under the MIT License.
