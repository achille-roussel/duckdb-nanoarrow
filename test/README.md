# Testing this extension

This directory contains all the tests for this extension. The `sql` directory holds tests that are written as [SQLLogicTests](https://duckdb.org/dev/sqllogictest/intro.html).

The root makefile contains targets to build and run all of these tests. To run the SQLLogicTests:

```bash
make test
# or make test_debug
```

If you're using CMake + VSCode, you can run

``` shell
./test_local.sh
```

The test data is generated with:

```python
import nanoarrow as na
from nanoarrow import ipc

url = "https://github.com/apache/arrow-experiments/raw/refs/heads/main/data/arrow-commits/arrow-commits.arrows"
with ipc.StreamWriter.from_path("test/sql/test.arrows") as writer:
    writer.write_stream(na.ArrayStream.from_url(url))
```
