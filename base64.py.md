#python #built-in

A built-in module for [[Base64]] operations
```python
import base64

# Encoding a string into Base64
input_string = "Hell"
input_string_in_bytes = input_string.encode()
base64_bytes = base64.b64encode(input_string_in_bytes)
base64_string = base64_bytes.decode()
print(base64_string) # Output: SGVsbA==

# Decoding from Base64
base64_bytes = base64_string.encode()
decoded_bytes = base64.b64decode(base64_bytes)
decoded_string = decoded_bytes.decode('utf-8')
print(decoded_string) # Output: Hell
```
- `.encode()` Converts a string to a byte object
- `.decode()` Converts a byte object back into a string
- **`base64.b64encode()`**: Encodes a byte-like object into Base64.
- **`base64.b64decode()`**: Decodes a Base64 encoded string back into its original byte form.