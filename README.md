
#  Harmouzi Agent Backup

This repository contains a full backup of the Hermes agent's configuration, skills, memory, and session history.

**Last Backup Date:** `2026-07-04`

## How to Restore

After a fresh installation of Hermes Agent, follow these steps to restore from this backup:

### 1. Clone the Repository

Clone this repository to your local machine:

```bash
git clone https://github.com/sabq4org/Harmouzi.git
```

### 2. Copy the Backup Data

Copy the contents of the `hermes_data_backup` directory into your `.hermes` home directory. This will restore all your skills, memories, and settings.

```bash
# Make sure your Hermes home directory exists
mkdir -p ~/.hermes

# Copy the backed-up data
cp -R Harmouzi/hermes_data_backup/ ~/.hermes/
```
> **Note:** If you get a "No such file or directory" error, it may be because Hermes Agent hasn't been run for the first time yet. Running `hermes` once should create the `~/.hermes` directory.

### 3. Restore Sensitive Files (Manual Step)

For security reasons, sensitive files containing API keys and authentication tokens were **not** included in this backup. You will need to recreate them manually.

- **`.env` file:** Create a new file at `~/.hermes/.env` and add your API keys. It should look something like this:

  ```env
  # ~/.hermes/.env

  # OpenAI API Key
  OPENAI_API_KEY="sk-..."

  # Anthropic API Key
  ANTHROPIC_API_KEY="sk-ant-..."

  # Other keys...
  ```

- **GitHub Authentication:** Re-authenticate with the GitHub CLI if you use GitHub-related skills:
  ```bash
  gh auth login
  ```

### 4. Restart Hermes

Once the files are restored and your API keys are in place, restart the Hermes agent or gateway. Your agent should now be fully restored.
