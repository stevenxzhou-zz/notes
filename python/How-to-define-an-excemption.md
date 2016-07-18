```python
class Error(Exception):
  """Base class for exceptions in this module."""


class MultiDayHourLeaveError(Error):
  """Exception raised for errors in the input.

  Attributes:
      msg  -- explanation of the error
  """

  def __init__(self, hours, start, end):
      self.msg = 'Leave of {hours} hours spans >1 days {start}, {end}'.format(
              hours=hours, start=start, end=end)
      super(MultiDayHourLeaveError, self).__init__(self.msg)
		  
```