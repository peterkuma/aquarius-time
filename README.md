# Aquarius Time: Scientific time library for Python

Aquarius Time is a Python library for performing time calculations which aims
to be more convenient for scientific applications than the default Python time
library (datetime). It uses the standard of Julian date, i.e. the fractional
number of days from -4712-01-01 12:00 as the basis for time representation, and
allows conversion between Python datetime, date arrays and ISO 8601 time.

## Installation

### Default Python distribution on Linux

1. Install the required system packages. On Debian-based distributions (Ubuntu,
   Devuan, ...):

   ```
   sudo apt install python3 python3-pip python3-venv python3-pipx
   ```

   On Fedora:

   ```
   sudo yum install python3 python3-pip python3-pipx
   ```

2. To install Aquarius Time in a Python virtual environment:

   ```
   python3 -m venv venv
   . venv/bin/activate
   pip install aquarius-time
   ```

   Replace `python3` with `python` if `python3` is not available.

   To install Aquarius Time in the user's home directory:

   ```
   pip3 install aquarius-time
   ```

   Replace `pip3` with `pip` if `pip3` is not available. You might have to add
   `--break-system-packages` if your distribution does not allow installation of
   Python packages in the home directory and you
   want to override this.

   To install Aquarius Time with pipx (if you want to use the command-line
   interface):

   ```
   pipx install aquarius-time
   ```

   You might have to add `$HOME/.local/bin` to the PATH environment variable if
   not present already.

### Anaconda on Linux, macOS and Windows

1. Install [Anaconda](https://www.anaconda.com/download).

2. Install Aquarius Time in the terminal (Linux, macOS) or Anaconda Prompt
   (Windows):

   ```
   pip install aquarius-time
   ```

## Python interface

```python
import aquarius_time as aq
```

### from_datetime

```python
aq.from_datetime(x)
```

Convert Python datetime `x` to Julian date.

- `x` - datetime instance or a list of datetime instances (datetime or list).

Returns Julian date (float) or a numpy array of Julian dates (float64) if `x`
is a list.

### to_datetime

```python
aq.to_datetime(x)
```

Convert Julian date `x` to Python datetime.

- `x` - Julian date (float) or a numpy array of Julian dates (float64).

Returns datetime or a list of datetimes if `x` is a numpy array.

### from_iso

```python
aq.from_iso(x)
```

Convert ISO 8601 time to Julian date.

- `x` - ISO 8601 time (str) or a list of ISO 8601 times (list of str).

Returns Julian date (float) or a numpy array (float64) if `x` is a list.

### to_iso

```python
aq.to_iso(x)
```

Convert Julian date to ISO 8601 time.

- `x` - Julian date (float) or a numpy array of Julian dates (float64).

Returns ISO 8601 time (str) of a list of ISO 8601 times (list of str)
if `x` a numpy array.

### from_date

```python
aq.from_date(x)
```

Convert date (see Date) to Julian date.

- `x` - Date (see Date),

Returns Julian date (float) or a numpy array of Julian dates.

### to_date

```python
aq.to_date(x)
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

## Command line interface

### aq

```sh
aq <from> <to> [<value>...]
```

Convert value(s) from one time format to another. The converted value(s) is
printed to the standard output. If no values are provided as command line
arguments, read values from the standard input, separated by new lines.
If a value cannot be converted, print `none`.

Arguments:

- `from` - From format (see Format below).
- `to` - To format (see Format below).
- `value` - Value to be converted.

Format:

- `jd` - Julian date.
- `iso` - ISO 8601.

## License

MIT. See [LICENSE.md](LICENSE.md).

## Releases

### 0.2.0 (2023-03-24)

- Fixed handling of fractions of a second in from\_date.
- Discontinued support for Python 2.

### 0.1.0 (2020-04-29)

- Initial development release.
