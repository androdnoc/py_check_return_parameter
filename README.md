# check_return_parameter py function

returns value if present in list of given valid values.
* if list of dicts, a key can be given to do a key:value check and return the valid dict.
* a default value can be given to be returned in case of no match.


```python
datums = [
	{
		"code": "msl",
		"name": "Mean Sea Level",
	},
	{
		"code": "lat",
		"name": "Lowest Astronomical Tide",
	},
	{
		"code": "man",
		"name": "Manual",
	},
	{
		"code": "chart",
		"name": "Chart",
	},
	{
		"code": "ord",
		"name": "Ordnance",
	},
]

time_intervals = [5, 6, 10, 12, 15, 20, 30, 60]


check_return_parameter(15, time_intervals)                 # return 15
check_return_parameter(24, time_intervals)                 # returns False
check_return_parameter(24, time_intervals, default=15)     # returns 15

check_return_parameter("lat", datums, param_key="code")                  # returns { "code": "lat", "name": "Lowest Astronomical Tide" }
check_return_parameter("abc", datums, param_key="code")                  # returns false
check_return_parameter("abc", datums, param_key="code", default="msl")   # returns { "code": "msl", "name": "Mean Sea Level" }
check_return_parameter("abc", datums, param_key="code", default="def")   # returns 'AttributeError: default value given is not present in list'
```
