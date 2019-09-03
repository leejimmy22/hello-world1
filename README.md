# hello-world
Just another repository

#!/usr/bin/env python3
import pytz
import sys
from datetime import datetime


def main(argv):
    """
    Entry point to program. Accepts user-supplied value.
    """
    # Assign first element of sys args list to uniqname.
    uniqname = argv[0]

    # Invoke the function and assign its return value to the variable cheer.
    cheer = huzzah(uniqname)

    # Print the message to the screen.
    print(cheer)
    
    
def huzzah(name):
    """
    Function accepts a user provided name and then declares victory
    by returning a string that includes the current date and time.
    The new string is assembled using the new f-string
    formatted string literal syntax.
    """
    claim = f"Huzzah! {name} writes first Python program at {umich_now()}"

    return claim
   
   
def umich_now():
    """
    Convert naive time (i.e., no notion of timezone) to UTC and then
    add offset for eastern time zone. Return as an ISO 8601 formatted string.
    """
    server_now = pytz.utc.localize(datetime.utcnow())
    detroit_now = server_now.astimezone(pytz.timezone("America/Detroit"))

    return detroit_now.isoformat()
    
    
if __name__ == '__main__':
    # Slice on the user-supplied value, ignoring first element in sys.argv (the file path).
    
    main(sys.argv[1:])
