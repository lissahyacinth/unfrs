# Univeral Numeric Fingerprint

Efficiently create an identifiable hash for a dataset that is independent of column or row ordering. 

More information on the creation of the UNF can be found [here](https://guides.dataverse.org/en/latest/developers/unf/index.html)


## Examples
```python
import pandas as pd
import pyarrow as pa
from unf_rs import unf, UnfHash

def unf_pd(df: pd.DataFrame) -> UnfHash:
    dtypes = [str(df.dtypes[x]) for x in df.columns]
    df_batches = pa.Table.from_pandas(x).to_batches()
    return unf(df_batches, df.columns, dtypes)

x=pd.DataFrame.from_dict({'a': [1,2,3]})
unf_hash = unf_pd(x)
print(unf_hash.short_hash)
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