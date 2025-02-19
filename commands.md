# Splunk Basic Commands

Splunk is a powerful tool for searching, monitoring, and analyzing machine-generated data. Below are some basic Splunk commands and examples to help you get started:

## 1. Searching Data

- **Basic Search**: Search for a specific term in your data.

  ```plaintext
  index=main "error"
  ```

  This searches for the term `"error"` in the `main` index.

- **Search in a Specific Index**:

  ```plaintext
  index=web_logs "login failed"
  ```

  Searches for `"login failed"` in the `web_logs` index.




