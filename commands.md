# Splunk Commands

Below are some basic Splunk commands and examples to help you get started:

## 1. Searching Data

- **Basic Search**: Search for a specific term in your data.

  ```
  index=main "error"
  ```

  This searches for the term `"error"` in the `main` index.

- **Search in a Specific Index**:

  ```
  index=web_logs "login failed"
  ```

  Searches for `"login failed"` in the `web_logs` index.


## 2. Filtering Results

- **Field-Based Search**:

  ```plaintext
  index=main status=404
  ```

  Searches for events where the `status` field equals `404`


- **Multiple Conditions**:

  ```plaintext
  index=main status=404 AND source="/var/log/access.log"
  ```

  Searches for events with `status=404` and `source="/var/log/access.log"`.

## 3. Using Wildcards

- **Wildcard Search**:

  ```plaintext
  index=main "failed*"
  ```

  Searches for events containing terms that start with `"failed"`.

## 4. Time Range

- **Search Within a Time Range**:

  ```plaintext
  index=main "error" earliest=-24h latest=now
  ```

  Searches for `"error"` in the last 24 hours.

- **Relative Time**:

  ```plaintext
  index=main "error" earliest=-7d
  ```

  Searches for `"error"` in the last 7 days.

## 5. Stats Command

- **Count Events**:

  ```plaintext
  index=main | stats count
  ```

  Counts the total number of events in the `main` index.

- **Group By Field**:

  ```plaintext
  index=main | stats count by status
  ```

  Counts events grouped by the `status` field.

## 6. Top Command

- **Most Common Values**:

  ```plaintext
  index=main | top limit=5 status
  ```

  Displays the top 5 most common values for the `status` field.

## 7. Table Command

- **Display Specific Fields**:

  ```plaintext
  index=main | table _time, status, source
  ```

  Displays only the `_time`, `status`, and `source` fields.

## 8. Rex Command (Regex Extraction)

- **Extract Fields**:

  ```plaintext
  index=main | rex field=_raw "user=(?<user>\w+)"
  ```

  Extracts the `user` field from the raw data using regex.

## 9. Eval Command

- **Perform Calculations**:

  ```plaintext
  index=main | eval response_time_sec = response_time_ms / 1000
  ```

  Creates a new field `response_time_sec` by dividing `response_time_ms` by 1000.

## 10. Sort Command

- **Sort Results**:

  ```plaintext
  index=main | sort - _time
  ```

  Sorts events by `_time` in descending order.

## 11. Dedup Command

- **Remove Duplicates**:

  ```plaintext
  index=main | dedup user
  ```

  Removes duplicate events based on the `user` field.

## 12. Rare Command

- **Find Rare Values**:

  ```plaintext
  index=main | rare status
  ```

  Displays the least common values for the `status` field.

## 13. Transaction Command

- **Group Events into Transactions**:

  ```plaintext
  index=web_logs | transaction user maxspan=5m
  ```

  Groups events into transactions based on the `user` field, with a maximum span of 5 minutes.

## 14. Timechart Command

- **Create Time-Based Charts**:

  ```plaintext
  index=main | timechart span=1h count by status
  ```

  Creates a timechart showing the count of events per hour, grouped by `status`.

## 15. Lookup Command

- **Enrich Data with Lookups**:

  ```plaintext
  index=main | lookup user_info user OUTPUT full_name
  ```

  Uses a lookup table `user_info` to add the `full_name` field based on the `user` field.

## 16. Subsearch

- **Nested Search**:

  ```plaintext
  index=main [search index=web_logs status=404 | table user]
  ```

  Uses a subsearch to find users with `status=404` and then searches for those users in the `main` index.

## 17. Macros

- **Use a Macro**:

  ```plaintext
  `error_search`
  ```

  If you have a macro named `error_search`, you can use it in your search.

## 18. Save and Schedule Searches

- **Save a Search**:

  ```plaintext
  | save search_name="My Search"
  ```

- **Schedule a Search**:
  Use the Splunk UI to schedule a search to run periodically.

## 19. Export Results

- **Export to CSV**:

  ```plaintext
  index=main | table _time, status, source | outputcsv my_results.csv
  ```

  Exports the results to a CSV file.

## 20. Help Command

- **Get Help**:

  ```plaintext
  | help
  ```

  Displays help for Splunk commands.

