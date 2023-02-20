# Turkey Last Eartquakes

## Muninn Config

```js
{
  selector: ".content-table tbody tr | array",
  schema: {
    id: "td:nth-child(8) | number",
    date: "td:nth-child(1)",
    latitude: "td:nth-child(2) | float",
    longitude: "td:nth-child(3) | float",
    depth: {
      schema: {
        value: "td:nth-child(4)",
        unit: { fill: "km" },
      },
    },
    type: "td:nth-child(5)",
    magnitude: "td:nth-child(6) | float",
    location: "td:nth-child(7)",
  },
}
```

## Usage

```js
import { parse } from 'muninn';

const config = {...};

// https://deprem.afad.gov.tr/last-earthquakes.html
const content = '<html>...</html>';

const results = parse(content, config);
```

### Output

```json
[
  {
    "id": 551111,
    "date": "2023-02-20 22:53:52",
    "latitude": 37.445,
    "longitude": 36.987,
    "depth": {
      "value": "6.29",
      "unit": "km"
    },
    "type": "ML",
    "magnitude": 1.9,
    "location": "Dulkadiroğlu (Kahramanmaraş)"
  },
  {
    "id": 551110,
    "date": "2023-02-20 22:43:52",
    "latitude": 36.239,
    "longitude": 35.951,
    "depth": {
      "value": "7.0",
      "unit": "km"
    },
    "type": "ML",
    "magnitude": 2.8,
    "location": "Samandağ (Hatay)"
  },
  ...
]
```
