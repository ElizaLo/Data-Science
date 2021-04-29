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
