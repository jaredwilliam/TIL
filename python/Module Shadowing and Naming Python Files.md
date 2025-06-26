---
created: 2025-06-26
tags:
  - TIL
categories:
  - "[[Python]]"
---

I came across this when I was playing around with Python's logging library. I had this code:

```python
import logging

def main() -> None:
	logging.basicConfig(level=logging.WARNING)
	
	logging.debug("This is a debug message.")
	logging.info("This is an info message.")
	logging.warning("This is a warning message.")
	logging.error("This is an error message.")
	logging.critical("This is a critical message.")

if __name__ == "__main__":
	main()
```

When I ran it though, I received an `AttributeError` saying that logging did not have a `basicConfig` attribute, but I know it does, and initially I was scratching my head why it didn't work. 

Turns out that the folder that this script was stored in was named `logging` as well. So when the script ran it imported logging, but it imported **my** folder, and not Python's logging library. 

Renaming the folder fixed the issue. 
