# Challenge Solution step by step

This repository contains a production-ready Bash script designed to identify the color of a specified fruit. It demonstrates fundamental shell scripting best practices, including robust input validation, pattern matching via case statements, correct streams for error redirection (`>&2`), and standard Unix exit code handling.

---

## Script Requirements Satisfied
* Takes exactly one argument (the fruit name).
* Validates that an argument is provided and handles empty states safely.
* Uses a `case` statement to efficiently match fruit types.
* Outputs errors to standard error (`stderr`) and exits with a non-zero code (`1`) for unknown inputs.
* Cleanly passes `shellcheck` linting with no warnings.

---

## Implementation (`fruit`)

```bash
#!/bin/bash

# Description: Tell the color of a fruit
# Exit Codes:  0 = Success, 1 = Error / Unknown Fruit

# 1. Validate that exactly one argument is provided
if [[ $# -ne 1 ]]; then
    echo "Usage: $0 <fruit>" >&2
    exit 1
fi

fruit="$1"

# 2. Process fruit selection
case "$fruit" in
    apple)
        echo "Red or green"
        ;;
    banana)
        echo "Yellow"
        ;;
    orange)
        echo "Orange"
        ;;
    grape)
        echo "Purple or green"
        ;;
    mango)
        echo "Yellow or green"
        ;;  
    *)
        # 3. Handle unknown fruit error
        echo "Unknown fruit: $fruit" >&2
        exit 1
        ;;
esac

### Deployment & Testing

# Run the static analysis tool to verify code quality
shellcheck Challenge

# Grant executable permissions to the script
chmod +x Challenge

# Run valid test cases
./Challenge apple    # Output: Red or green
./Challenge banana   # Output: Yellow

# Run an error validation case
./Challenge kiwi     # Output: Unknown fruit: kiwi (Exit code: 1)
