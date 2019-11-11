# Aquarius Time: Scientific time library for Python

**Development status:** in development

Aquarius Time is a Python library for performing time
calculations which aims to be more convenient for scientific applications than
the default Python time library (datetime).
It uses the standard of Julian date,
the fractional number of days from -4712-01-01 12:00 as the basis for time
representation, and allows conversion between Python datetime, date arrays
and ISO 8601 time.

## Installation

Requirements:

- Python 2.7 or Python 3

**Note:** To install with Python 3 instead of Python 2 replace `python` in the
commands below with `python3`.

To install in system directories:

```sh
python setup.py install
```

To install in user directories:

```sh
python setup.py install --user
```

## Python functions

```python
import aquarius_time as aq
```

### from_datetime

```python
from_datetime(x)
```

Convert Python datetime `x` to Julian date.

- `x` - datetime instance or a list of datetime instances (datetime or list).

Returns Julian date (float) or a numpy array of Julian dates (float64) if `x`
is a list.

### to_datetime

```python
to_datetime(x)
```

Convert Julian date `x` to Python datetime.

- `x` - Julian date (float) or a numpy array of Julian dates (float64).

Returns datetime or a list of datetimes if `x` is a numpy array.

### from_iso

```python
from_iso(x)
```

Convert ISO 8601 time to Julian date.

- `x` - ISO 8601 time (str) or a list of ISO 8601 times (list of str).

Returns Julian date (float) or a numpy array (float64) if `x` is a list.

### to_iso

```python
to_iso(x)
```

Convert Julian date to ISO 8601 time.

- `x` - Julian date (float) or a numpy array of Julian dates (float64).

Returns ISO 8601 time (str) of a list of ISO 8601 times (list of str)
if `x` a numpy array.

### from_date

```python
from_date(x)
```

Convert date (see Date) to Julian date.

- `x` - Date (see Date),

Returns Julian date (float) or a numpy array of Julian dates.

### to_date

```python
to_date(x)
```

Convert Julian date to date (see Date).

- `x` - Julian date (float) or a numpy array of Julian dates (float64).

Returns date.

## Date

Date is a list containing numbers or numpy arrays in the following order: 

0. Calendar (see Calendar below) (int8).
1. Year (int32).
2. Month (int8).
3. Day (int8).
4. Hour (int8).
5. Minute (int8).
6. Second (int8).
7. Fraction of a second (float64).

Calendar:

- `1`: Gregorian calendar.

## License

MIT. See [LICENSE.md](LICENSE.md).

