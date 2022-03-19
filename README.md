# save-cache-action
Github action to explicitly save paths to cache. 

Github's existing actions only save when the key doesn't have a cache-hit and only saves at the end of the job.  This action saves everytime and saves immediately.

## Saving
```
- name: Cache multiple paths
  uses: mstate/save-cache-action@main
  with:
    action: save
    paths: |
      ~/cache
      !~/cache/exclude
    key: ${{ runner.os }}-${{ hashFiles('**/lockfiles') }}
```

## Restoring

You can restore from multple keys.
```
- name: Restor multiple keys to path
  uses: mstate/save-cache-action@main
  with:
    action: restore
    paths:
      ./restore-here
    keys: |
    ${{ runner.os }}-${{ hashFiles('**/lockfiles') }}
```
