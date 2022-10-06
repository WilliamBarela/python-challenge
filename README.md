# python-challenge

Using Python 3.10 to write a collection service which consumes the [Coffee API](https://sampleapis.com/api-list/coffee).

##Specifications:
1. Write a Python module which includes a `class ApiService` which includes at minimum the following method signature:

- `def get(api_base_uri, endpoint)`
- specifications:
  - Use [Requests library](https://requests.readthedocs.io/en/latest/) to call a given API with a given endpoint:
  - Example arguments: `api_base_uri = https://api.sampleapis.com/` and `endpoint = /coffee/hot`

Include logging and excepting handling for calls to the API.
This can be as simple as appending a print statement to a `run.log` file. You may also use a logging library if you desire.
The entries to log file should include the datetime of the exception in ISO-8601 format, the HTTP status code, and the error message:
```
2022-10-06T00:30:42-05:00 | 500 | coffee API unreachable
```

The ISO-8601 formatted timestamp can be computed as follows:
```python
import datetime
datetime.datetime.now().astimezone().replace(microsecond=0).isoformat()
```

### example usage:
```python
from apiservice import ApiService
from config.api import COFFEE

coffeeApi = ApiService(COFFEE.api_base_uri)
coffeeApi.get(COFFEE.endpoint)
```

2. Write a Python class, `CoffeeDeserializer` which models a given coffee JSON object:
```json
{
  "title": "Iced Coffee",
  "description": "A coffee with ice, typically served with a dash of milk, cream or sweetener—iced coffee is really as simple as that.",
  "ingredients": [
    "Coffee",
    "Ice",
    "Sugar*",
    "Cream*"
  ],
  "image": "https://upload.wikimedia.org/wikipedia/commons/d/d8/Blue_Bottle%2C_Kyoto_Style_Ice_Coffee_%285909775445%29.jpg",
  "id": 1
}
```

So that for each coffee JSON object, you can instantiate a coffee object with the following getters:
  - title
  - description 
  - ingredients
  - image
  - id

3. Write a Python class `CoffeeDeserializer` which has a class method, `json_to_list`:
- `def self.json_to_list(coffee_json)`
- For a given serialized coffee object, `coffee_object`, the `json_to_list` class method should return the following values interpolated:
```python
[
  coffee_object.title,
  coffee_object.description,
  coffee_object.,
  coffee_object.,
  coffee_object.
]
```

4. 
standard library only
