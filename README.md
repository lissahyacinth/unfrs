# Univeral Numeric Fingerprint

Efficiently create an identifiable hash for a dataset that is independent of column or row ordering. 

More information on the creation of the UNF can be found [here](https://guides.dataverse.org/en/latest/developers/unf/index.html)


## Examples
```python
import pandas as pd
import pyarrow as pa
from unf_rs import unf

x=pd.DataFrame.from_dict({'a': [1,2,3]})
b=pa.Table.from_pandas(x).to_batches()
z=unf(b, ['a'], ['int64'])
print(z.short_hash)
> 4azsEFx0zdIIlq6uXGpG4g==
```

### Support
| UNF Version      | Supported |
| ----------- | ----------- |
| 3      | <ul><li>- [ ] </li></ul>       |
| 4   | <ul><li>- [ ] </li></ul>       |
| 5      | <ul><li>- [ ] </li></ul>     |
| 6   | <ul><li>- [x] </li></ul>        |


### Sources
This package is primarily a port of the fantastic UNF [package in R](https://github.com/leeper/UNF) with an intention on making the features available on significantly bigger datasets with low memory usage.