# pypartpicker

A PCPartPicker data extractor for Python.

### Features:

- Fetch product specs, prices and ratings
- Fetch part lists
- Supports all PCPartPicker regions

# Installation

```
> git clone https://github.com/thefakequake/pypartpicker
> git checkout 2.0
```

# Example

```py
from pypartpicker import Client

client = Client(region="uk")
part = client.get_part(
    "https://pcpartpicker.com/product/fN88TW/amd-ryzen-7-5800xt-38-ghz-8-core-processor-100-100001582box"
)

for spec, value in part.specs.items():
    print(f"{spec}: {value}")

print(part.cheapest_price)
```

# Async Example

```py
from pypartpicker import AsyncClient
import asyncio


async def get_parts():
    async with AsyncClient(region="uk") as client:
        part = await client.get_part(
            "https://pcpartpicker.com/product/fN88TW/amd-ryzen-7-5800xt-38-ghz-8-core-processor-100-100001582box"
        )

    for spec, value in part.specs.items():
        print(f"{spec}: {value}")


asyncio.run(get_parts())

```
