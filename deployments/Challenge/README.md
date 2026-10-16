This precisely documents the fruit challenge code logic, emphasizing proper stream handling.

```markdown
# Shell Scripting Challenge: Input Validation & Stream Routing

A specialized Bash scripting implementation designed to evaluate strict input validation patterns and robust Unix standard stream separation techniques.

## 🎯 Core Functionality
The core script accepts a user-defined fruit name as an input argument, evaluates it against an internal conditional matrix using robust `case` statements, and returns the corresponding color signature.

## 🛠️ Technical Implementation Details
* **Strict Parameter Checking:** Validates the presence of arguments immediately upon execution, throwing structured error payloads if the input parameters are missing or corrupted.
* **Stream Redirection (`>&2`):** Correctly decouples operational outputs from diagnostic messaging. System errors are explicitly sent down the Standard Error stream (`>&2`), ensuring logging utilities can harvest them independently from Standard Output (`stdout`).
* **Unix Exit Status Hygiene:** Utilizes deliberate exit code returns (`exit 0` for successful lookups, `exit 1` for missing criteria) to seamlessly interface with modern CI/CD orchestration layers.
