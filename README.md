# Warehouse tools

Small Python utilities for warehouse order and shipping workflows.

Run the tests with `python3 -m unittest discover -s tests -v`.

## Shipping

`shipping_quote(weight_kg, zone, service="standard")` returns a delivery quote
in dollars.

| Parameter   | Values                      | Notes                            |
|-------------|-----------------------------|----------------------------------|
| `weight_kg` | positive float              | Parcel weight in kilograms       |
| `zone`      | `"local"`, `"regional"`     | Delivery zone                    |
| `service`   | `"standard"`, `"express"`   | Defaults to `"standard"`; express adds a flat $7 surcharge |

Unknown zones or services raise `ValueError`.

### CLI usage

```
python -m warehouse.cli <weight_kg> <zone> [--service {standard,express}]
```

Examples:

```bash
# Standard quote – 2 kg, local zone
python -m warehouse.cli 2 local

# Express quote – 2 kg, local zone
python -m warehouse.cli 2 local --service express
```
