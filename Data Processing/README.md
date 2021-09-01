# Data Processing

## Batch vs Stream

| Batch      | Stream |
| ----------- | ----------- |
| Larger datasets      | Simpler analysis: aggregation / filtering       |
| More complex analysis   | Individual records / micro batches        |
| Slower moving data (hours, days)   | Data moves FAST       |
| With batch processing, a batch of information is collected before being sent in for processing | With streaming, data is sent for analysis piece-by-piece, and processed in **real time**|

## Stream

### Roles vs Users

| Roles     | Users |
| ----------- | ----------- |
| Live in IAM      | Live in IAM       |
| Have permissions policies   | Have permissions policies        |
| **Only attach to other services**  | **Can act on their own**       |
| **Do not have keys nor login** | **Can have keys or login**|

--------------------------------

### Convert Pandas DataFrame to bytes-like object

```python

import io

towrite = io.BytesIO()
df.to_excel(towrite)  # write to BytesIO buffer
towrite.seek(0) 

print(towrite)
> b''
print(type(towrite))
> _io.BytesIO
```

if you want to see the bytes-like object use `getvalue`,

```python
print(towrite.getvalue())
> b'PK\x03\x04\x14\x00\x00\x00\x08\x00\x00\x00!\x00<\xb
```
