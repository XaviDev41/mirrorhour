mirrorhour --tz Europe/Madrid


# mirrorhour

Utilities to detect and work with mirror hours (when the hour and minute are the same, e.g., 11:11 or 22:22) in local time or any arbitrary timezone.

## Installation

```bash
pip install mirrorhour[cli]
```


## Quick usage (CLI)

```bash
# Run the CLI with your current environment (if installed as a script):
mirrorhour --tz Europe/Madrid

# Or run directly with Python (from project root):
C:/Users/UserName/mirrorhour/.venv/Scripts/python.exe -m mirrorhour.cli --tz Europe/Madrid

# 12-hour mode example:
mirrorhour --tz Europe/Madrid --twelve
```

Options:
- `--tz <zone>`: Specify the IANA timezone (e.g., Europe/Madrid).
- `--twelve`: Use 12-hour mirror mode (01:01 to 12:12).

## How to test the Python API

```bash
# Run the test suite (from project root):
C:/Users/UserName/mirrorhour/.venv/Scripts/python.exe -m pytest src/tests/test_core.py
```

Or, try the API interactively:

```python
from mirrorhour import is_mirror_time, next_mirror_time, all_mirror_times
from datetime import datetime

now = datetime.now()
print(is_mirror_time(now))
print(next_mirror_time(now))
print(all_mirror_times())
```

## Example usage in Python

```python
from mirrorhour import is_mirror_time, next_mirror_time, all_mirror_times
from datetime import datetime

now = datetime.now()
if is_mirror_time(now):
	print("It's a mirror hour!")
else:
	print("Not a mirror hour. Next is:", next_mirror_time(now))

print("All mirror hours today:", all_mirror_times())
```

## API

- `is_mirror_time(dt, tz=None, use_24h=True)`: Returns `True` if `dt` is a mirror hour.
- `next_mirror_time(dt, tz=None, use_24h=True)`: Returns the next `datetime` that will be a mirror hour.
- `all_mirror_times(day=None, use_24h=True)`: Lists all possible mirror hours for a day.

## Requirements
- Python >= 3.9
- [tzdata](https://pypi.org/project/tzdata/) (only if your system lacks a timezone database)

## Credits
Author: XaviDev41 (<4152@xavi.com.es>)
License: MIT
Repository: https://github.com/XaviDev41/mirrorhour
