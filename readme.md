# Edit /etc/hosts

```
127.0.0.1 xhprof.local
```

# Run xhprof profiler from the php code

##### start

```php
include_once "/usr/local/lib/php/xhprof_lib/utils/xhprof_lib.php";
include_once "/usr/local/lib/php/xhprof_lib/utils/xhprof_runs.php";
xhprof_enable(XHPROF_FLAGS_CPU + XHPROF_FLAGS_MEMORY);
```

``` debug code ```

##### finish
```php
(new XHProfRuns_Default)->save_run(xhprof_disable(), "test");
```
